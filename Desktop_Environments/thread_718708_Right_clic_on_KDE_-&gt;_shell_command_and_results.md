---
title: "Right clic on KDE -&gt; shell command and results"
date: 2008-03-08
forum: Desktop Environments
---

### Post by EvilAngel on 2008-03-08
Hi all,

I add a small config file to be able to compute md5 hash on right clic in KDE.
Here is the file:
```
[Desktop Entry]
ServiceTypes=all/allfiles
Actions=makemd5
ExcludeServiceTypes=kdedevice/*
Encoding=UTF-8

[Desktop Action makemd5]
Name=Generate md5 sum
Exec=/usr/bin/md5sum %F
Icon=kmail
```
My problem is that when i right clic on a file and then go on "Generate md5 sum", it is not opening a shell with the result.

Do you know how to open and launch a shell command on right clic ?

Thanks

---

### Post by ssj3strife on 2008-03-08
Replace

Exec=/usr/bin/md5sum %F

with something like

Exec=Konsole -e '/usr/bin/md5sum %F ; sleep 10000'

That's probably not going to work if you just copy/paste it, I just made it up off the top of my head. It'll get you started in the right direction though, and the sleep bit at the end should make it so the console doesn't close immediately after having finished the command.

Good luck!

---

### Post by EvilAngel on 2008-03-14
I replaced Konsole by konsole in the command line (Konsole is not working for me)

But i am experiencing a problem
When i right clic to execute my special menu, i have a message saying that there is a problem whith PTY (konsole needs read/write access on pty)

You got the same problem ?

Thanks

---

### Post by ssj3strife on 2008-03-15
I don't know, I don't use KDE or konsole. I'll fire up a virtual machine and play around with it, and let you know what I come up with.

---

### Post by ssj3strife on 2008-03-15
Try this:

konsole -e /bin/sh -c '/usr/bin/md5sum %F ; sleep 3600'

---

