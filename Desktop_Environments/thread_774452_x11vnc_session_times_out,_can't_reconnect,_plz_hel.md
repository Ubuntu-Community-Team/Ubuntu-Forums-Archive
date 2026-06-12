---
title: "x11vnc session times out, can't reconnect, plz help"
date: 2008-04-29
forum: Desktop Environments
---

### Post by uschxc on 2008-04-29
it seems when i leave my desk with my vnc session open it times out or loses connection with the server.  when i try to reconnect the window opens and closes.  here's my log output, i tried a vncviewer and the java applet.

```
29/04/2008 13:37:45 Got connection from client 150.125.199.76
29/04/2008 13:37:45   other clients:
29/04/2008 13:37:45      150.125.199.76
29/04/2008 13:37:46 Client Protocol Version 3.8
29/04/2008 13:37:46 Protocol version sent 3.8, using 3.8
29/04/2008 13:37:46 rfbProcessClientSecurityType: executing handler for type 2
29/04/2008 13:37:46 active keyboard: turning X autorepeat off.
29/04/2008 13:37:49 -dontdisconnect: Not shared & existing client
29/04/2008 13:37:49   refusing new client 150.125.199.76
29/04/2008 13:37:49 client_count: 1
29/04/2008 13:37:49 Client 150.125.199.76 gone
29/04/2008 13:37:49 Statistics             events    Transmit/ RawEquiv ( saved)
29/04/2008 13:37:49  TOTALS              :      0 |         0/        0 (  0.0%)
29/04/2008 13:37:49 Statistics             events    Received/ RawEquiv ( saved)
29/04/2008 13:37:49  TOTALS              :      0 |         0/        0 (  0.0%)
29/04/2008 13:40:25 httpd: get '' for 150.125.199.76
29/04/2008 13:40:25 httpd: defaulting to 'index.vnc'
29/04/2008 13:40:25 httpd: get 'favicon.ico' for 150.125.199.76
29/04/2008 13:40:25 httpProcessInput: open: No such file or directory
29/04/2008 13:40:30 httpd: get 'favicon.ico' for 150.125.199.76
29/04/2008 13:40:30 httpProcessInput: open: No such file or directory
29/04/2008 13:40:30 httpd: get 'vncviewer.jar' for 150.125.199.76
29/04/2008 13:40:31 httpd: get 'vncviewer.jar' for 150.125.199.76
29/04/2008 13:40:32 httpd: get 'vncviewer.jar' for 150.125.199.76
29/04/2008 13:40:40 Got connection from client 150.125.199.76
29/04/2008 13:40:40   other clients:
29/04/2008 13:40:40      150.125.199.76
29/04/2008 13:40:40 Client Protocol Version 3.3
29/04/2008 13:40:40 Protocol version sent 3.3, using 3.3
29/04/2008 13:40:41 -dontdisconnect: Not shared & existing client
29/04/2008 13:40:41   refusing new client 150.125.199.76
29/04/2008 13:40:41 client_count: 1
29/04/2008 13:40:41 Client 150.125.199.76 gone
29/04/2008 13:40:41 Statistics             events    Transmit/ RawEquiv ( saved)
29/04/2008 13:40:41  TOTALS              :      0 |         0/        0 (  0.0%)
29/04/2008 13:40:41 Statistics             events    Received/ RawEquiv ( saved)
29/04/2008 13:40:41  TOTALS              :      0 |         0/        0 (  0.0%)
```

on my side the connection seemed to have timed out or gotten lost.  the x11vnc server never disconnected him, so maybe there isn't even a time out at all.  i have and an ssh session open to the remote machine but am not exactly sure how to reset things and go about what i was doing, if i even can.

thanks in advance

---

### Post by krunge on 2008-04-29
From your log, it seems like you already have another VNC viewer connected ('other clients').  If you want to have more than one viewer connected at the same time use the '-shared' x11vnc option.

If you want it to not exit after the first viewer disconnects also use the '-forever' option.

[http://www.karlrunge.com/x11vnc/faq.html#faq-forever-shared]("http://www.karlrunge.com/x11vnc/faq.html#faq-forever-shared")

It is possible that the 'other client' process is actually gone, but somehow the TCP connection still exists and so x11vnc still thinks it is there. What does netstat(1) say? Not sure what how to handle that case...

---

### Post by alfonso78 on 2011-11-01
Hello,

I have the same problem.

Sometimes my x11vnc session times out or gets disconnected and I cannot login anymore.

[B]If I try [FONT="Courier New"]-shared[/FONT] as suggested, it works, but this means my previous session is still hanging and consuming resources (I tried to login twice at the same time to test).

Is there a way to tell x11vnc to allow every login and to kick out any previous login?[/B]

I would like to be able to login and to clean up resources if there is a previous session hanging!

thank you.

---

### Post by krunge on 2011-11-03
> 

If I try [FONT="Courier New"]-shared[/FONT] as suggested, it works, but this means my previous session is still hanging and consuming resources (I tried to login twice at the same time to test).

Is there a way to tell x11vnc to allow every login and to kick out any previous login?

Yes, I put posted this in another related thread:

```
x11vnc -forever -nevershared
```

---

