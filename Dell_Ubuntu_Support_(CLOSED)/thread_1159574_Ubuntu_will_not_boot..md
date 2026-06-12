---
title: "Ubuntu will not boot."
date: 2009-05-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sirebral on 2009-05-14
This has never happened to me before.

Currently my Mini 9 is in a brick state since Ubuntu will not boot completely.  I receive the error message

> 
The display server has been shut down about 6 times in the last 90 seconds.  It is likely that something bad is going on.  Waiting for 2 minutes before trying again on the display :0


So the culprit is the display.  This makes sense because I fell asleep watching Adult Swim and my Mini 9 went to sleep too.  When I awoke and woke my mini the audio for the adult swim episode could be heard but the system never fully awoke.

Any ideas?

---

### Post by albinootje on 2009-05-14
> **sirebral said:**
>  Currently my Mini 9 is in a brick state since Ubuntu will not boot completely. 

Is it in a messed up suspend or hibernate state ?
Can you get a prompt, and then shut it down with this command :
```

sudo halt

```
If that works, try a reboot after that complete shutdown (halt).

---

### Post by sirebral on 2009-05-14
It did not work.  Bummer.  I even tried starting and stopping Gnome Display Manager.  Not sure what to do right now.

---

### Post by sirebral on 2009-05-14
So my next step was to hunt down menu.lst so I could edit the Grub timeout.  I managed that and now I am looking at, after recover mode and continuing to regular boot;

> 
*Starting web server apache2
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName


So this might be the whole of the problem.  Next step, an attempt to fix the X-Server.

---

### Post by sirebral on 2009-05-15
Hrm.. I got past that error by adding

ServerName localhost to my /etc/apache2/apache2.conf file, but now I have the same problem with no error.

Ubuntu will not load and I get an error box that has the text in all boxes.  Nothing is readable.

---

### Post by coffeeaddict22 on 2009-05-15
Boot into a recovery console, and select the option to "repair my Display" (or something like that).  Essentially it runs xfix, but it sounds like that's what you need.

---

### Post by sirebral on 2009-05-15
tried running xfix.  Not working.

---

### Post by albinootje on 2009-05-15
> **sirebral said:**
> tried running xfix.  Not working.

Is the screen okay when you boot into a live session from a cdrom or usb stick ?
If so, can you compare /etc/X11/xorg.conf ?

And can you do a force file system check ?
[http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/](http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/)

---

### Post by sirebral on 2009-05-15
I have decided to try and update to 9.04 to see if that fixes the problem.  I think 8.10 is no longer supported so I am going to try with the version that is supported.

---

### Post by albinootje on 2009-05-15
> **sirebral said:**
> I have decided to try and update to 9.04 to see if that fixes the problem.  I think 8.10 is no longer supported so I am going to try with the version that is supported.

Hmm, well, 7.10 is no longer supported, but 8.10 has support till April 2010. See here : [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by sirebral on 2009-05-15
Oh. I already started the update through terminal.

---

### Post by albinootje on 2009-05-15
> **sirebral said:**
> Oh. I already started the update through terminal.

Okay :) Good luck!

---

### Post by sirebral on 2009-05-15
well, that fixed it.  Now I have another problem.  new thread!

):P

---

