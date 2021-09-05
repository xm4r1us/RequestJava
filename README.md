# RequestJava
Basic Java Function About Requests
# No Need Installation
```
//Only put this script on your code
    	public static String request(String types, String link, String[] headers ,String postdata) throws Exception {
    	String inputLine = "";
    	if (types == "get") {
        URL yahoo = new URL(link);
        URLConnection yc = yahoo.openConnection();
        for (int i = 0; i < headers.length; i++) {
        	  //System.out.println(headers[i]);
        	String[] isimvs = headers[i].split(":");
        	yc.setRequestProperty(isimvs[0],isimvs[1]);
        	}
        BufferedReader in = new BufferedReader(
                                new InputStreamReader(
                                yc.getInputStream()));
        

        while ((inputLine = in.readLine()) != null) 
            System.out.println(inputLine);
        in.close();
       
        return inputLine;
    	}else if (types =="post") {
    		 URL url = new URL(link);
    	        URLConnection conn;
    	        conn = url.openConnection();
    	        for (int i = 0; i < headers.length; i++) {
    	        	  //System.out.println(headers[i]);
    	        	String[] isimvs = headers[i].split(":");
    	        	conn.setRequestProperty(isimvs[0],isimvs[1]);
    	        	}
    	        String data = postdata;
    	        conn.setDoOutput(true);
    	        conn.setDoInput(true);
    	        OutputStreamWriter wr = new OutputStreamWriter(conn.getOutputStream());
    	        wr.write(data);
    	        wr.flush();
    	        BufferedReader rd = new BufferedReader(new InputStreamReader(conn.getInputStream())); 
    	        while ((inputLine = rd.readLine()) != null) 
    	            System.out.println(inputLine);
    	}
		return inputLine;
    }
```
#Usage (GET)
```java
request("get","https://httpbin.org/post", new String[] {"User-Agent:Sa","deneme:deneme"} ,"");
```

