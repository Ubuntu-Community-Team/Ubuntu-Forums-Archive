---
title: "frostwire issue"
date: 2006-06-02
forum: Desktop Environments
---

### Post by puccaso on 2006-06-02
the picture  is attatched,
this is what happeneds
i cant see anything

this is terminal output

```
mahir@jt:/tmp$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_06]
Configuring environment...
Loading FrostWire:
log4j:WARN No appenders could be found for logger (com.limegroup.gnutella.gui.Initializer).
log4j:WARN Please initialize the log4j system properly.
CyberGarage warning : HTTP/1.1 200 OK
Cache-Control:max-age=120
Location:http://192.168.1.1:5678/rootDesc.xml
Server:NT/5.0 UPnP/1.0
ST:upnp:rootdevice
USN:uuid:upnp-InternetGatewayDevice-1_0-0090a2777777::upnp:rootdevice
EXT:


CyberGarage warning : org.cybergarage.xml.ParserException: java.io.IOException: Server returned HTTP response code: 500 for URL: http://192.168.1.1:5678/rootDesc.xml
org.cybergarage.xml.ParserException: org.cybergarage.xml.ParserException: java.io.IOException: Server returned HTTP response code: 500 for URL: http://192.168.1.1:5678/rootDesc.xml
        at org.cybergarage.xml.Parser.parse(Parser.java:80)
        at org.cybergarage.upnp.ControlPoint.addDevice(ControlPoint.java:222)
        at org.cybergarage.upnp.ControlPoint.searchResponseReceived(ControlPoint.java:470)
        at org.cybergarage.upnp.ssdp.SSDPSearchResponseSocket.run(SSDPSearchResponseSocket.java:75)
        at java.lang.Thread.run(Thread.java:595)
Caused by: org.cybergarage.xml.ParserException: java.io.IOException: Server returned HTTP response code: 500 for URL: http://192.168.1.1:5678/rootDesc.xml
        at org.cybergarage.xml.Parser.parse(Parser.java:56)
        at org.cybergarage.xml.Parser.parse(Parser.java:78)
        ... 4 more
Caused by: java.io.IOException: Server returned HTTP response code: 500 for URL: http://192.168.1.1:5678/rootDesc.xml
        at sun.net.www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1149)
        at org.cybergarage.xml.Parser.parse(Parser.java:46)
        ... 5 more
/usr/share/themes/Clearlooks/gtk-2.0/gtkrc:49: Engine "clearlooks" is unsupported, ignoring
mahir@jt:/tmp$

``` 
whats happening

---

