---
title: "Run X applications within a chrooted Dapper."
date: 2006-07-25
forum: Desktop Environments
---

### Post by lolipop on 2006-07-25
Hello all.

First of all, I hope that I post in the good section, I apologize if it's not and I ask you to move that thread.

For some time, I try to remaster a Dapper Drake following those instructions :
[https://help.ubuntu.com/community/LiveCDCustomization/6%2e10](https://help.ubuntu.com/community/LiveCDCustomization/6%2e10)

It works fine, I create the chroot without any problem.

However I would like to run graphical applications in the chroot. I know that it's possible with knoppix :
In this tutorial : [http://www.knoppix.net/wiki/Knoppix_Remastering_Howto#X_Session_Configuration](http://www.knoppix.net/wiki/Knoppix_Remastering_Howto#X_Session_Configuration)
I tested the second solution, i.e. the nested X, and now I can run graphical applications in the nested X by the chrooted Ubuntu.

But the first solution, i.e. "export DISPLAY=localhost:0.0" in the chroot, doesn't work with me. I tested it with knoppix and ubuntu and I always have the same problem : when I try to run xclock I get : "Error: Can't open display: localhost:0.0", nautilus >> "(nautilus:9236): Gtk-WARNING **: cannot open display:", etc. And I don't know why, I tested with "xhost +", it's the same thing.

So if you are able to tell me what is the problem, I'm reading you. :]

Please excuse my potential mistakes in English, it is not my native language. If you did not understand something, tell me, I will be delighted to explain again.

Thanks in advance with all those who will want to answer.

---

### Post by lolipop on 2006-07-25
I don't know if it can help but I have the same problem with "export DISPLAY=127.0.0.1:0.0". (At the beginning I had domain name resolution problems.)

---

