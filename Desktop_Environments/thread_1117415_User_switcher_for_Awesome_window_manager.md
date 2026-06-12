---
title: "User switcher for Awesome window manager?"
date: 2009-04-05
forum: Desktop Environments
---

### Post by junglist313 on 2009-04-05
On my main desktop I have two users, my wife and I. I use Awesome as my  window manager and my wife uses Gnome. Back when we both ran Gnome switching users while leaving the other logged in was not a issue thanks to the user switcher panel applet. Is there a way for my wife to log into her gnome session while leaving my Awesome session active? I run a lot of applications and hate coming back to my computer only to find out she has Ctrl+Alt+Backspace me out so she can check her email. Thanks!

---

### Post by Dark_Stang on 2009-04-06
I don't think you can run two window managers at a time like that but... I'm going to keep an eye on this thread to see if anybody has any suggestions because it makes me curious.

---

### Post by GoingDown on 2009-04-16
> **junglist313 said:**
> On my main desktop I have two users, my wife and I. I use Awesome as my  window manager and my wife uses Gnome. Back when we both ran Gnome switching users while leaving the other logged in was not a issue thanks to the user switcher panel applet. Is there a way for my wife to log into her gnome session while leaving my Awesome session active? I run a lot of applications and hate coming back to my computer only to find out she has Ctrl+Alt+Backspace me out so she can check her email. Thanks!

If you are using gdm and gnome-screensaver, this works. Just log your workstation with screensaver password, and in password prompt there is "Switch user" button. 

Works with awesome window manager, I am using it.

Also, you probably can use gnome-panel with awesome, but last time I tried it was a little bit clunky

EDIT. By the way, there is another way to do this. Just run command "gdmflexiserver" from your awesome session. This starts 2nd X session with gdm login window

---

### Post by junglist313 on 2009-06-09
gdmflexiserver worked like a charm. Thanks a million!

---

### Post by valadil on 2009-10-30
I had a similar problem and came up with the attached script.  The advantage of it is that it only asks for a pw if its a new login.  Otherwise it's the same as ctrl-alt-f8.  "gdmSwitch.sh WIFES_USERNAME" will switch to her.

The downside is that I don't have it working in karmic.  No idea why, but gdmflexiserver options are somewhat less plentiful in this version.

---

