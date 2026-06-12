---
title: "mouse + trackpad messed up, is it the kernel? URGENTE !!! MAY YOU PLEASE??"
date: 2010-06-22
forum: Desktop Environments
---

### Post by guyshoxton on 2010-06-22
[SIZE="4"]Ok so for a few days now i have been erasing my harddisk and installing ubuntu 9.10 , and then ubuntu 10.04 LTS over and over seeing if my trackpad or mouse works again...
I had ubuntu on my laptop now for more then 1 year but never had any type of problems with my trackpad(A.K.A touch pad) or mouse.

On friday, i re installed ubuntu 10.04 LTS, the first install of lucid was upgrading from 9.10, but then i decided to install a fresh new lucid so it didnt have the themes from 9.10 and other software installed from it...

but thats when my mouse stopped working when ever my arm or hand accidently brushed on the laptops trackpad or when ever i used the trackpad, the mouse and trackpad left-click button stopped working (im a right handed person)

so im like, it must be the new fresh install.. then i installed 9.10 and the same thing happened, so from 9.10 i upgraded to ubuntu 10.04 ... i did that about 4 or 6 times for the last few days and i have not been able to get it back to normal !!

I have posted a similar thing to this here [http://ubuntuforums.org/showthread.php?t=1514846](http://ubuntuforums.org/showthread.php?t=1514846)

and prylux said this happened to him before too, and he told me to switch kernels, i did but it did not work!

now i re- re- installed ubuntu 10.04 and its kernel by default is 

2.6.32-21-generic <-- i checked.

but still,
after a few minutes of using my laptop, it stoped working or when ever i touch any buttons or the pad on my laptops trackpad both stop working - and i loose every thing i was doing (like all the graphics i was designing, my emails, etc..).

**may some one please help????!!!**

is this the kernel?? if it is the kernel which kernel do i switch to??
 what can i do to solve this???:confused:

THANK YOU SO MUCH IF YOU HELP OR TRY TO!!

P.S.
When this first started which was when i installed the new fresh version like i said above, i tried to update ubuntu (system > administration > Update Manager) and it said 
"**COULD NOT GRAB YOUR MOUSE.**

A malicious client may be eavesdropping on your session or you may 
have just clicked a menu or some application just decided to gt focus.

Try again."

[COLOR="Red"]OR, is there any way for me to disable my trackpad? (The buttons & the touch part)[/COLOR]
[/SIZE]

---

### Post by sashby on 2010-07-05
Here's something you can try.  This assumes the underlying problem is actually with your settings that affect how your system handles window focus and focus stealing.

I am using XFCE - if you aren't using XFCE it could still be a similar problem, but the settings would be found  elsewhere.

1) "Applications" Menu / Settings / XFCE 4 Settings Manager
2) Uncheck "Activate focus stealing prevention"
3) Uncheck "Honor standard ICCCM focus hint"

This has been absolutely maddening for me - coming and going every time I update the system.  I suspect these settings were always the problem, but system updates have affected how these settings are interpreted.  Good luck!

---

