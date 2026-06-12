---
title: "Need help in setting up VNC server on ubuntu"
date: 2008-10-30
forum: Desktop Environments
---

### Post by yinglcs2 on 2008-10-30
Hi,

I have been following the following thread in setting up the VNC server on ubuntu.

[http://ubuntuforums.org/showthread.php?t=197964](http://ubuntuforums.org/showthread.php?t=197964)

I am at the point of trying to run the 'vncview' locally.

1. I make sure Xvnc is running:
```

sudo /etc/init.d/xinetd start
 * Starting internet superserver xinetd                                  [ OK ]
 netstat -a 
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:5901                  *:*                     LISTEN     
tcp        0      0 localhost:5037          *:*                     LISTEN     
tcp        0      0 *:4662                  *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN  

```

but When i try to run vncviewer locally,I get this:
```

 ./vncviewer localhost:5091
./vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server
./vncviewer 127.0.0.1:5091
./vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server
./vncviewer localhost:1
./vncviewer: read: Connection reset by peer



```

And yes, i have try disable all the visual effect in my environment (the thread said something like beryl makes it not working). 

Thank you for any pointer.

---

### Post by Spitphire on 2008-10-31
You are using the wrong port... check your config file compared to what you are typing, when attempting to connect.

---

### Post by yinglcs2 on 2008-11-01
I have re-tried it.

On server, it is listening on port 5901:
```

> netstat -a
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:5901                  *:*                     LISTEN     
tcp        0      0 *:51413                 *:*                     LISTEN     
tcp        0      0 *:4662                  *:*                     LISTEN     
tcp        0      0 localhost:ipp           *:*                     LISTEN     

```


I try it in another shell:
```

 vncviewer localhost:5901
vncviewer: read: Connection reset by peer

```
Same error.

Again, I have disabled compiz fusion. Still does not help.

---

### Post by CSandman on 2011-08-09
The vncviewer script plays a little trick here.

The convention is that in things that look like, XX.XX.XX.XX:Y, the Y is a port.

In the vncviewer command the Y is actually the display that you're connecting to.

The command you're looking for is:

```

vncviewer localhost:1

```

---

