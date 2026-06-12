---
title: "800x600 resolution problem"
date: 2009-03-07
forum: Desktop Environments
---

### Post by yehgross on 2009-03-07
I can only select 800x600 resolution and lower, and my monitor is capable of 1440x900 @60hz. I have an acer x193w lcd monitor and a nvidia geforce 7050 graphics card. When i activate the nvidia drivers in the hardware drivers and restart, it goes to the login and the screen goes black and says 'INPUT NOT SUPPORTED'. To be able to get it back i have to run in recovery mode and fix X. I dont really know what to configure in /etc/X11/xorg.conf as im completely new to linux, coming from a windows background.

oh yeah, im running ubuntu 8.10

if it makes any difference there are 224 updates i havnt installed, would installing them fix it ?

---

### Post by benblout on 2009-03-07
It is unlikely, but possible, that an update would fix the problem.
Is there a reason you haven't done them?  They should be pretty quick
and easy.

Then come back if you are still having the problem.  My inclination is 
for you to uninstall the nvidia drivers, get the display recognized, then
add the drivers back in.

---

### Post by yehgross on 2009-03-07
I installed the updates and nothing. the reason i didnt install them before is because they took a while. I uninstalled drivers and reinstalled and i still get the INPUT NOT SUPPORTED screen at the start up. I can hear it loading up, but i can't see anything. The only way to fix it is too boot up in the recovery mode and click fix x server and im back to a low res set up.

---

### Post by benblout on 2009-03-07
OK, I'm not surprised doing the updates did not fix anything, but it was worth a quick try, especially since you really should do them for security reasons.

The next step I would take is to remove the packages that contain the nvidia drivers, and try starting X.  Then tackle the problem in two steps - one step is to get the monitor working at higher resolutions.  The second is to get the nvidia drivers working at this higher resolution.

That make sense?

---

### Post by yehgross on 2009-03-07
```
jon@jon-desktop:~$ startx


Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.

```

i get this when i try and start X. i wouldnt really know what to do when it is started anyways, or is it pretty straight forward?

is it safe to removed /tmp/.X0-lock?

---

### Post by benblout on 2009-03-07
To restart X:
```
Logout
when you see the screen asking for your user name, hold down the control
   and alt keys, and then press backspace.
```
That keystroke combination will restart X anytime, I think.  But it is best to logout first.

---

### Post by yehgross on 2009-03-07
im sort of lost on what to do next. when i go to terminal and type startx i still get the same thing. am i doing something wrong, i really dont know much about linux, this is my first day using it.

---

### Post by benblout on 2009-03-07
OK, we will get this sorted out.

When you talk about a terminal, are you seeing terminal in a window, with menus and a border?  If you are, you are already running X.  Anytime you want to restart X, follow my directions above that involved logging out and then typing c-a-bksp.

On the other hand, you might be at a screen with NO graphics - no windows, no menus.

What are you seeing?

Also, if you have another computer, you might want to try IRC for this - it provides quicker back and forth for what is likely to be a simple problem.

---

### Post by yehgross on 2009-03-07
im seeing the default ubuntu theme, with the menus etc, just in 800x600 resolution that i cant change

do you thing editing xorg.conf would work following this tutorial?: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

### Post by yehgross on 2009-03-08
edited xorg and it still doesnt work

---

### Post by yehgross on 2009-03-09
Randomly worked after installing drivers again. Thanks.

---

