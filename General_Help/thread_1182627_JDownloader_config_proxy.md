---
title: "JDownloader config proxy"
date: 2009-06-09
forum: General Help
---

### Post by askno on 2009-06-09
Hi I installed Jdownloader, however now i only have access to the internet in my HighSchool, and to change the settings of the program I have to open it.

andre@andre-laptop:~/Documentos$ ./jd.sh 
JD Installation found: Starting JD now
9/Jun/2009 12:10:42 - INFO [jd.Main(main)] -> Start JDownloader
JAR
9/Jun/2009 12:10:42 - FINEST [jd.utils.JDUtilities(getJDClassLoader)] -> Create Classloader: for: /home/andre/.jd
9/Jun/2009 12:10:42 - FINEST [jd.JDClassLoader(<init>)] -> rootDir:/home/andre/.jd
/home/andre/.jd
 file:/home/andre/.jd/jd
9/Jun/2009 12:10:43 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/andre/.jd/plugins/JDShutdown.jar
9/Jun/2009 12:10:43 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/andre/.jd/plugins/JDTray.jar
9/Jun/2009 12:10:43 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/andre/.jd/plugins/JDUnrar.jar
9/Jun/2009 12:10:43 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/andre/.jd/plugins/JDHJMerge.jar
9/Jun/2009 12:10:43 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/andre/.jd/plugins/JDChat.jar
9/Jun/2009 12:10:43 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/andre/.jd/JDownloader.jar
9/Jun/2009 12:10:43 - INFO [jd.Main(main)] -> init Eventmanager
9/Jun/2009 12:10:43 - FINER [jd.config.DatabaseConnector(<init>)] -> Loading database
9/Jun/2009 12:10:43 - FINER [jd.config.DatabaseConnector(checkDatabaseHeader)] -> Checking database
9/Jun/2009 12:10:44 - INFO [jd.Main(main)] -> init Localisation
9/Jun/2009 12:10:45 - INFO [jd.Main(go)] -> init Configuration
Removed Consolehandler. Start with -debug to see console output
/home/andre/.jd/config/WEBUPDATE.cfg (No such file or directory)
Update Downloadmirrors
java.net.SocketTimeoutException: connect timed out
    at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
    at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
    at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
    at java.lang.reflect.Constructor.newInstance(Constructor.java:513)
    at sun.net.www.protocol.http.HttpURLConnection$6.run(HttpURLConnection.java:1360)
    at java.security.AccessController.doPrivileged(Native Method)
    at sun.net.[www.protocol.http.HttpURLConnection.getChainedException(HttpURLConnection.java:1354]("http://www.protocol.http.HttpURLConnection.getChainedException%28HttpURLConnection.java:1354"))
    at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1008]("http://www.protocol.http.HttpURLConnection.getInputStream%28HttpURLConnection.java:1008"))
    at jd.http.HTTPConnection.getInputStream(HTTPConnection.java:104)
    at jd.http.requests.Request.read(Request.java:517)
    at jd.http.requests.Request.read(Request.java:502)
.......................
.......................



So my question is how do I change settings without open jDownloader???
If anyone could help I would apreciate!!! Thanks!

---

### Post by alien-377h on 2009-10-31
I got this problem also today

I don't see any webupdate.cfg in the .jd directory.

And even a fresh one install in Windows don't have that.

I don't know how to solve this.

JDownloader is not working now :(

---

### Post by Jiaz on 2009-11-04
you can set proxy with normal java parameter  java -Xmx512m -Dhttp.proxyHost=myproxyserver.com  -Dhttp.proxyPort=80 -jar JDownloader.jar or jdupdate.jar  when jd is running, set proxy in settings of it ;)

---

### Post by leofenix on 2010-11-26
That command line works great! Thanks!

---

