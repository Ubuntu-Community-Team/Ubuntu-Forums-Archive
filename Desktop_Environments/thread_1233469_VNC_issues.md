---
title: "VNC issues"
date: 2009-08-06
forum: Desktop Environments
---

### Post by doesntcount on 2009-08-06
I need some advice, if anybody's able to provide it.

I've installed ubuntu and need a way to vnc to this machine. I have gnome, which comes with the vino server. But the screen doesn't update for me when i use it. Mouse actions get through, but changes to the screen don't make it back to my client. Looks like this bug has affected a lot of people:

[https://bugs.launchpad.net/ubuntu/+source/vino/+bug/77442](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/77442)

I tried installing x11vnc, but I'm not able to connect from my gentoo box upstairs. I've started x11vnc on the server with this command:

```

sudo x11vnc -safer -nopw -accept popup:0 -display :0

```

But when i try to connect, i get this error:

```

06/08/2009 17:15:25 Got connection from client 192.168.0.101
06/08/2009 17:15:25   other clients:
06/08/2009 17:15:40 could not connect to ident: 192.168.0.101:113
06/08/2009 17:15:55 accept_client: using builtin popup for: 192.168.0.101

```

Does anybody have any advice on the vino bug, or the x11vnc connection issue that may help here? I'm at a loss :(

Thanks.

---

### Post by krunge on 2009-08-06
Why are you using "-accept popup"?  Do you really want that?  If not, remove it from the cmdline.  I think that is your problem.

Be sure to add this to the x11vnc cmdline:```
-noxdamage
``` to work around the screen updates bug in Xorg that you mentioned.

Also, who is logged into the display :0 X session?  Why do you use sudo??

---

### Post by doesntcount on 2009-08-10
ya, looks like the accept popup was my problem. I found this howto to pretty helpful as well:

[http://ubuntuforums.org/showthread.php?t=45565](http://ubuntuforums.org/showthread.php?t=45565)

Thanks for the quick response.

---

