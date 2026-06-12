---
title: "ssh with vnc"
date: 2009-05-16
forum: General Help
---

### Post by marktyler on 2009-05-16
I have enabled the remote desktop control for my Ubuntu machine and switched the port to one of my own choosing. I can connect from my Mac using Chicken of the VNC by specifying ip:port in the host parameter. This all works fine. 

However I wanted to be able to connect away from home so I thought I'd use ssh. I specified the following in a terminal window

```
ssh -C -L <ubuntu vnc port>:127.0.0.1:5900 -p 22 <ubuntu machine name> -l <ubuntu user>
```

I enter the password when requested and the login completes.
When I now specify 127.0.0.1 and display 0 in the parameters to CotVNC I get 

[I]Could not connect to server 127.0.0.1:5900.
Connection refused: connect()[/I]

Where did I go wrong on this one?

---

### Post by doas777 on 2009-05-16
it's easier to use vnc to do the tunneling:
```
vncviewer -via user@sserver localhost:0
``` will connect via ssh to the first display on "server".

also it kinda looks like you need to add a space between your IP parameters

---

### Post by mbeach on 2009-05-16
I would normally use something like this from your work

ssh myuser@HomeExternalIPaddress -L5905:192.168.0.90:5900

192.168.0.90 is listening on port 5900 and is the machine on my lan I want to remote to.  5905 is the forwarded localport.  The ssh server and my 192.168.0.90 are two different machines.

So after sucessful connection I connect using vncviewer to "localhost:5905"


In your example, I think you may have the ports backwards.
connect to 
localhost:<ubuntu vnc port>
not 
localhost:5900

---

### Post by mbeach on 2009-05-16
or lets say on your ubuntu machine you are listening on 5999 for vnc.

ssh youruser@yourexternalipathome -L5905:127.0.0.1:5999

then in cotvnc you connect to
localhost:5905
which will forward your localport at work to your remote port at home (5999 in this example).

---

