---
title: "login problems"
date: 2011-06-13
forum: Desktop Environments
---

### Post by houshdaran on 2011-06-13
Hello.I have a dualboot system.My Ram and Graphic card crashed and I changed them.After that I was not able to log into ubuntu(It displays the grub boot menu but it has difficult building '/', '/temp', ...)what is the problem probably and what shall I do?

---

### Post by houshdaran on 2011-06-13
> **houshdaran said:**
> Hello.I have a dualboot system.My Ram and Graphic card crashed and I changed them.After that I was not able to log into ubuntu(It displays the grub boot menu but it has difficult building '/', '/temp', ...)what is the problem probably and what shall I do?
please answer!

---

### Post by houshdaran on 2011-06-15
> **houshdaran said:**
> Hello.I have a dualboot system.My Ram and Graphic card crashed and I changed them.After that I was not able to log into ubuntu(It displays the grub boot menu but it has difficult building '/', '/temp', ...)what is the problem probably and what shall I do?
 
Noone is gonna answer me?

---

### Post by AeroZak on 2011-06-15
If I was in your situation, I would boot into your other OS, then download a Live CD of Ubuntu and try to see what happens when your computer runs that.  I would assume that it will run it normally, but you never know.

If it runs normally, then it could just be that your Ubutnu configuration/files somehow got messed up during the process of whatever was going on when your Ram and Graphics card broke.

If it doesn't run (which would be very odd), then it could be a plethora of problems, but my first instinct would be to reinstall your ram and graphics card.

What were you doing when your ram and graphics card crashed?
What OS were you booted into?
Did you manage to boot into Ubuntu, all the way to the login screen, but just could not actually login?
Or did it just stop when it was building the 'temp'?

Your description of what happened is very vague, so I'm trying to help, but I don't have much to work off of haha.

---

### Post by houshdaran on 2011-06-15
> **AeroZak said:**
> If I was in your situation, I would boot into your other OS, then download a Live CD of Ubuntu and try to see what happens when your computer runs that. I would assume that it will run it normally, but you never know.
 
If it runs normally, then it could just be that your Ubutnu configuration/files somehow got messed up during the process of whatever was going on when your Ram and Graphics card broke.
 
If it doesn't run (which would be very odd), then it could be a plethora of problems, but my first instinct would be to reinstall your ram and graphics card.
 
What were you doing when your ram and graphics card crashed?
What OS were you booted into?
Did you manage to boot into Ubuntu, all the way to the login screen, but just could not actually login?
Or did it just stop when it was building the 'temp'?
 
Your description of what happened is very vague, so I'm trying to help, but I don't have much to work off of haha.
 
Thank you.I was sleeping when the cards crashed!
No, it cannot mount  '/' at all;so I see no login screens.
I have on my machine winxp and(RIP)ubuntu 10.10

---

### Post by AeroZak on 2011-06-15
Which did you install first, Ubuntu or Windows, and what was the method of installation? WUBI, CD/DVD?

---

### Post by wildmanne39 on 2011-06-16
> **houshdaran said:**
> Thank you.I was sleeping when the cards crashed!
No, it cannot mount  '/' at all;so I see no login screens.
I have on my machine winxp and(RIP)ubuntu 10.10Hi, it may be the video card because you have a driver installed for the old card and it is not working with the new card, here is a link, you can try this if it does not work let us know,if it does you will need to uninstall the driver for your old card after you boot.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by houshdaran on 2011-06-16
> **AeroZak said:**
> Which did you install first, Ubuntu or Windows, and what was the method of installation? WUBI, CD/DVD?
 Windows.but it was long before the crash.
DVD

---

### Post by houshdaran on 2011-06-16
> **wildmanne39 said:**
> Hi, it may be the video card because you have a driver installed for the old card and it is not working with the new card, here is a link, you can try this if it does not work let us know,if it does you will need to uninstall the driver for your old card after you boot.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
 Do you think it affects the mounting of '/'?
and where do I uninstall the driver for the old Graphic card?From windows?

---

### Post by rothux.j on 2011-06-16
Are you not able to login under console? I thought that uses standard drivers, so the graphics card changing shouldn't make a difference...
You can then test mounting things, as well as do an apt-get update and upgrade.
Have a look at getting into recovery mode.

---

### Post by dhinteractive on 2011-06-16
do you think it works

---

### Post by houshdaran on 2011-06-16
> **rothux.j said:**
> Are you not able to login under console? I thought that uses standard drivers, so the graphics card changing shouldn't make a difference...
You can then test mounting things, as well as do an apt-get update and upgrade.
Have a look at getting into recovery mode.
 I cannot enter ubuntu.even the login screen does not show up

---

### Post by wildmanne39 on 2011-06-16
> **houshdaran said:**
> I cannot enter ubuntu.even the login screen does not show up
Hi, look in my previous post there is a link to change settings on boot up that should allow you to boot, then you can check on your video card driver.

---

### Post by rothux.j on 2011-06-17
> **houshdaran said:**
> I cannot enter ubuntu.even the login screen does not show up
You don't use the login screen to get to a tty... you follow what wildmanne says.

---

