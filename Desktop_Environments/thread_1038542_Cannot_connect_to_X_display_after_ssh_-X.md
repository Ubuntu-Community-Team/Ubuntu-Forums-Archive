---
title: "Cannot connect to X display after ssh -X"
date: 2009-01-12
forum: Desktop Environments
---

### Post by narcan on 2009-01-12
I ssh'd to my ubuntu machine from mac os x using ssh -X.

Now when I ssh (without -X forwarding) and try to run a program on the local X server I get this:

MBP:~ djfumberger$ ssh dave@10.1.1.3
dave@10.1.1.3's password: 

dave@server:~$ export DISPLAY=:0.0
dave@server:~$ xterm
No protocol specified
xterm Xt error: Can't open display: :0.0 

The .Xauthority file is empty which I'm suspecting might have something to do with it. 

Any ideas what I've got to do to get the local X server functioning again ?

---

