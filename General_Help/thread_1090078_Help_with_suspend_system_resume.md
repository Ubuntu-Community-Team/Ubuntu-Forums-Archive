---
title: "Help with suspend system resume"
date: 2009-03-07
forum: General Help
---

### Post by humphreybc on 2009-03-07
Hi there,

Every now and then on Ubuntu when I resume the computer from suspend mode, or even if the "screensaver" kicks in (a blank screen), Ubuntu "freezes." It doesn't ACTUALLY freeze, but what happens is that the keyboard no longer does anything and the mouse will move the cursor but cannot click anything. I know it's not frozen because when I push my power button once the shutdown menu appears and starts counting down.

Sometimes I will turn on my laptop and go away to make a cup of coffee or something and expect to return to the Ubuntu login screen (Ubuntu is set as my default OS) but instead I get a black screen, moving the mouse or hitting keys on the keyboard does nothing.

---

### Post by khamil8686 on 2009-03-08
i had a problem where i would suspend my system, come back and hit the power button, it would start up and then when i would finish and enter my password the desktop wallpaper would show, soon go black or it would just start up with a bunch of weird lines on the screen, but it would just hang, sometimes the mouse would move, other times not, was weird. i did some googling and found a post which said to disable visual effects
i have ubuntu 8.10 and goto system>preferences>appearance, click the visual effects tab and then i clicked the radio button next to none, then had no problem with the black screen when resuming, another thing that many people said worked for their particular machine was edit /etc/default/acpi-support and change POST_VIDEO to false, anyways hope this helps out :) i started using ubuntu within a few weeks ago and i had a hard time with this prob so i decided to help out in whatever small way i could :)

---

