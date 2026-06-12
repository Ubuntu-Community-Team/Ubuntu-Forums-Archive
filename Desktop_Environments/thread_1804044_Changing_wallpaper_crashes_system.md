---
title: "Changing wallpaper crashes system"
date: 2011-07-14
forum: Desktop Environments
---

### Post by kmiller12 on 2011-07-14
Hi all

fresh install Ubuntu 10.04 x86
Compaq Presario sr1123wm
no visual effects 

System run great other than crashing when ever i try to change desktop image. Not sure witch log file to look at for errors. 

any thoughts

kevin

---

### Post by matt_symes on 2011-07-14
Hi

You are using Nautilus to draw the background and not Compiz. Is this correct ?

How many different background wallpapers have you tried ? Are they all of the same type or different types ?

What happens when it crashes ? Does it take you back to the login screen ?

Kind regards

---

### Post by kmiller12 on 2011-07-14
thank you for reply
i am    using Nautilus
i have tried 3 or 4 they are jpg format
when it crashes it brings up the original installed wallpaper, with nothing else. no icons,task-bars.
keyboard and mouse not responsive.

thank you again
kevin

---

### Post by matt_symes on 2011-07-14
Hi

I should have asked, what version of Ubuntu are you using ?

Kind regards

---

### Post by kmiller12 on 2011-07-14
Ubuntu 10.04 lts.

thanks
kevin

---

### Post by matt_symes on 2011-07-14
Hi

First things first. Lets make sure you can reboot safely when the X locks up.

Method 1. This may or may not work.

> keyboard and mouse not responsive.

Can you press CTRL + ATL + F1 to get to a console when this happens ? If you can you can log on to the console and then reboot by typing

```
sudo reboot
```

You will need to enter you password. It will not be echoed to the screen.

Method 2. This should work as long as the kernel has not locked up.

Press and hold Right ALT + SysRq keys and keep them depressed. While they are depressed hit each of these keys one after another leaving a 5 second gap between each key press.

r e i s u b

That should safely reboot your PC and is known as the magic key combination (spells busier backwards).

The main log we will need to look at  Xorg.0.log. There should also be a previous version of the log called /var/log/Xorg.0.log.old.

```
cat /var/log/Xorg.0.log
```

If a crash has happened recently, we need to look at this log. This log can be quite large so either post it as an attachment or try to find where the crash is happening and just post that part.

Hopefully one of those 2 logs will contain details about what is causing the crash.

Kind regards

---

### Post by kmiller12 on 2011-07-14
solved.

I was not paying attention. one of the memory sticks was not seated right. After i went back through and reinstalled all is good. It was a system not os crash

thank you for your time and knowledge.

kevin

---

### Post by matt_symes on 2011-07-14
Hi

> one of the memory sticks was not seated right.I've been there, i've done that. 

:biggrin::biggrin::biggrin:

I'm glad it's fixed.

Kind regards

---

