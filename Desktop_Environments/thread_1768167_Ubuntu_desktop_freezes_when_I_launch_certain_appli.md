---
title: "Ubuntu desktop freezes when I launch certain applications."
date: 2011-05-26
forum: Desktop Environments
---

### Post by shaakunthala on 2011-05-26
Hi all,

I have installed Ubuntu 11.04 Natty Narwhal. I'm using the Gnome desktop (Ubuntu Classic) instead of Unity.

My problems is, when I launch certain applications, most of the time LibreOffice ones, Ubuntu desktop freezes.

When this happens the desktop becomes unresponsive to the keyboard. However the mouse pointer can still be moved around. Everything on the screen will freeze including panels and their items.

This happens only when an application launches.

I have already set up a shortcut key combination so that Ctrl + Alt + Backspace will perform a session restart. But when the above mentioned problem occurs, shortcut keys do not work (so I can't just do a session restart). So there's nothing to do other than restarting the laptop by holding the power button down.

My question is, why does this happen? And is their any known fix?

Thanks in advance.

--
Shaakunthala

---

### Post by wildmanne39 on 2011-05-27
> **shaakunthala said:**
> Hi all,

I have installed Ubuntu 11.04 Natty Narwhal. I'm using the Gnome desktop (Ubuntu Classic) instead of Unity.

My problems is, when I launch certain applications, most of the time LibreOffice ones, Ubuntu desktop freezes.

When this happens the desktop becomes unresponsive to the keyboard. However the mouse pointer can still be moved around. Everything on the screen will freeze including panels and their items.

This happens only when an application launches.

I have already set up a shortcut key combination so that Ctrl + Alt + Backspace will perform a session restart. But when the above mentioned problem occurs, shortcut keys do not work (so I can't just do a session restart). So there's nothing to do other than restarting the laptop by holding the power button down.

My question is, why does this happen? And is their any known fix?

Thanks in advance.

--
Shaakunthala
Hi, have you checked to make sure your laptop is not getting hot that is a very common cause of freezes but not the only one. What video card are you using? are you using the cube? What are your system specs?

---

### Post by shaakunthala on 2011-05-27
Hi,

My laptop specs are below.

Model: Acer Aspire 4315
CPU: Intel Celeron 1.73 GHz
RAM: 1.5 GB
Graphics: Mobile Intel GL960 Express

My laptop does not overheat as recently I cleaned the cooler. Now the temperature is about 60 - 70 C. Before cleaning up I have experienced sudden reboots when the temperature rises above 90 C.

Yes I use the desktop cube.

Thanks!

---

### Post by wildmanne39 on 2011-05-27
> **shaakunthala said:**
> Hi,

My laptop specs are below.

Model: Acer Aspire 4315
CPU: Intel Celeron 1.73 GHz
RAM: 1.5 GB
Graphics: Mobile Intel GL960 Express

My laptop does not overheat as recently I cleaned the cooler. Now the temperature is about 60 - 70 C. Before cleaning up I have experienced sudden reboots when the temperature rises above 90 C.

Yes I use the desktop cube.

Thanks!
Hi log out and log in as ubuntu classic with no effects and see if that fixes your problem.

---

### Post by shaakunthala on 2011-05-27
Yes, that fixes! :)

But I need the effects as well... So could it be a problem of the Window decorator or compiz? 

Thanks for your help! This was critical for me since I use Ubuntu only.



> **wildmanne39 said:**
> Hi log out and log in as ubuntu classic with no effects and see if that fixes your problem.

---

### Post by wildmanne39 on 2011-05-27
> **shaakunthala said:**
> Yes, that fixes! :)

But I need the effects as well... So could it be a problem of the Window decorator or compiz? 

Thanks for your help! This was critical for me since I use Ubuntu only.
Hi, go into ccsm to opengl and make sure the sync to vblank is disabled,also if you have video settings manager like nvidia make sure it is disabled in there too. While you are in ccsm set your refresh rate to 60.):P

---

### Post by kutenkov on 2011-05-30
Have a similar problem since installed 11.04 (from scratch). It doesn't happen at start of any particular application, but after I leave the laptop running for sometime and go back.

Ctrl+Alt+F1 works, so I login and do shutdown/restart until next time it happens.

Previously used on the same laptop Ubuntu 10.10 and lower versions without such problem.

Will try later today the above cure and let everyone know if it helped.

Thanks!

---

### Post by msw1 on 2013-01-27
I have a similar problem. 100% sure this is due to Desktop Cube, any way to fix while preserving cube?

---

### Post by wildmanne39 on 2013-01-27
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title. 
Thanks

---

