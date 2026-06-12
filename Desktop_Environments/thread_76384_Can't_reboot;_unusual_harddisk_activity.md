---
title: "Can't reboot; unusual harddisk activity"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Estariel on 2005-10-15
**1.**
I cannot reboot.
Honestly.
If I try to do that, I will get a (small) glance at the kubuntu shutdown screen, then the screen goes black, my CPU fan starts spinning like mad, and the system stays like that, until I hard-reset it.

This is on the most linux-unfriendly laptop ever invented, the Sony Vaio VGN S3-XP.

I checked all logs, there is nothing at all in them that would indicate what's going on. 

What could be going on here? Does Kubuntu use some sophisticated shutdown method I'm not aware of?

**2.**
I have a tiny led on my laptop that indicates whether it is being written on the harddisk. Having used gentoo (which I had on this laptop before trying ubuntu) I know that this led should be flickering on booting and after that only if I do something that involves reading/writing to the harddisk.

Now it just stays constantly "on" from the moment kubuntu takes over (thus as soon as I leave the GRUB screen).
I cannot hear lots of writing to the harddisk though (which I normally can).

Is kubuntu just messing with the LED? Or is it really writing on the harddisk constantly (which would sooner or later kill the disk, wouldn't it?)

What could I do?

Thanks!
Estariel

---

### Post by simlu on 2006-01-17
[QUOTE=Estariel]**1.**
I cannot reboot.
Honestly.
If I try to do that, I will get a (small) glance at the kubuntu shutdown screen, then the screen goes black, my CPU fan starts spinning like mad, and the system stays like that, until I hard-reset it.

This is on the most linux-unfriendly laptop ever invented, the Sony Vaio VGN S3-XP.

I checked all logs, there is nothing at all in them that would indicate what's going on. 

What could be going on here? Does Kubuntu use some sophisticated shutdown method I'm not aware of?
[/QUOTE]

Hey don't blame your laptop, I have a Dell Inspiron 2650 and I have the same problem. I can't reboot like you. Did you find something about this problem yet? For me what I found is that I can't even exit from X (doing ctrl-alt-backspace)... The screen goes black and it stay there, forever until I do a cold reboot.

---

### Post by cwaldbieser on 2006-01-17
[QUOTE=simlu]Hey don't blame your laptop, I have a Dell Inspiron 2650 and I have the same problem. I can't reboot like you. Did you find something about this problem yet? For me what I found is that I can't even exit from X (doing ctrl-alt-backspace)... The screen goes black and it stay there, forever until I do a cold reboot.[/QUOTE]
What if you switch to a console and manually kill the X display server?

---

### Post by simlu on 2006-01-19
[QUOTE=cwaldbieser]What if you switch to a console and manually kill the X display server?[/QUOTE]

The black screen again. I think it is a well known problem with the nvidia linux driver for GeForce GO. For others with the same problem, look here: [http://www.nvnews.net/vbulletin/printthread.php?t=43577&pp=40](http://www.nvnews.net/vbulletin/printthread.php?t=43577&pp=40)

---

