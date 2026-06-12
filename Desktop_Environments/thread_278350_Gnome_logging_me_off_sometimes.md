---
title: "Gnome logging me off sometimes"
date: 2006-10-16
forum: Desktop Environments
---

### Post by charlvj on 2006-10-16
Hi,

This only happened twice so far and unfortunately I am not 100% sure what happens since it only happened when I was away from my computer. 
I usually lock my desktop when away from the computer, and twice now I've come back to find my login screen and all my open programs gone - very annoying. It is almost like the computer restarted or I got logged off. I don't think the computer restarted - at least it doesn't look like it has from the log files and the other computers in the office is ok so there wasn't a power failure or something.

Has anybody else experienced this?

I am using Dapper and I have the latest updates. Dell Latitude C840. 

Thanks

---

### Post by dannyboy79 on 2006-10-16
this has happened to me also except i know for sure that one of the times there was a power outage because the mircowave clock was off. i wonder if it's kind of like when ms updates come and they are critical enough that it automatically shuts down the system so you do a restart? i am not sure why this happens but it's not good as I have a ftp server that all my friends use to share stuff so hopefully we can figure this out.

---

### Post by charlvj on 2006-10-17
It happened again today - seems to happen only when I lock the desktop to go on lunch! 

It looks like the following appears in messages log file everytime this happens:
> 
Oct 17 13:05:10 localhost kernel: [17196412.976000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Oct 17 13:05:10 localhost kernel: [17196412.976000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Oct 17 13:05:10 localhost kernel: [17196412.976000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Oct 17 13:05:14 localhost gconfd (charlvj-4995): GConf server is not in use, shutting down.
Oct 17 13:05:14 localhost gconfd (charlvj-4995): Exiting
Oct 17 13:14:06 localhost gconfd (charlvj-15118 ): starting (version 2.14.0), pid 15118 user 'charlvj'


Regards

---

### Post by MasterZ on 2006-10-22
Hello, 

I have a similar problem, in fact, I think that my computer reboot and its not only a log off... But I cant be sure because it's always when I'm away for some time. 

I thought it could be related to usb management. In fact, my monitor is also a usb hub, and everytime I go away for a long time, I cut the power of the monitor and the usb is disconnected also. 
I did experience the problem only when cutting power of the monitor and not if I go away leaving it on. 

But this is only a supposition. To investigate further I would need some guidelines about the logging on linux. I already looked at the kern.log syslog and messages files; but I do not find anything strange in there (In fact I'm barely able to recognize a restart/reboot in the logs). So if someone could point me to a guide about logging, what I can activate; are there other important logfiles; how to change the log sensitivity, ... 

And if I find something else, I'll post it here. 

Thanks, 

MasterZ

---

### Post by Nikusan on 2006-11-13
Happens to me too, but only on edgy. Anyone worked it out yet?

EDIT: Some threads suggest you add this line to your device section in xorg.conf

```
Option 		"RenderAccel" "0"
```

I did that and also changed my driver from ati to fglrx.
Not sure which of those did it, but it seems to have fixed the problem for me.

---

### Post by charlvj on 2006-11-20
I have since upgraded to Edgy hoping it will perhaps disappear in the same way it appeared, but unfortunately it happened again. 

I have not tried the RenderAccel thing.

Just thought I'd give an update. :-)
Thanks

---

