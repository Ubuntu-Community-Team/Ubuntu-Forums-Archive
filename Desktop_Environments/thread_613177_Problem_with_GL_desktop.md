---
title: "Problem with GL desktop"
date: 2007-11-14
forum: Desktop Environments
---

### Post by iccaro on 2007-11-14
Hello, I have installed Ubuntu 7.10 on my laptop, with a ATI X700 graphics card and restricted drivers.

I new in Linux. I would like to test the famous "Llinux cube", so I installed GL Desktop (I read it is a good option). When I execute it, I activate both options: "Show tray icon" and "Enable GL Desktop". But when I close the window, and I open again the GL desktop preferences, the second mentioned option is not selected. I don understand why. Of course, there is no cube, nor other effect.

Could you please help me with this problem? I don find the solution in the forum...

Thanks,

iccaro

---

### Post by jpietari on 2007-11-17
I use CompizFusion and before I could enable the cubed desktop, I had to switch the number of workspaces I have to 4.  By default, Ubuntu sets the system up with 2 workspaceses.  To do this, there was an option in CompizConfig.  In other distros I've tried, this option was always in a gnome config panel.

---

### Post by Forlong on 2007-11-17
Do not use "GL Desktop" in Gutsy.
Use compizconfig-settings-manager (ccsm) and *System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects* instead.

As for getting the cube, see [here](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion).

---

### Post by iccaro on 2007-11-26
x Forlong: I do what you say, but when i going to activate visual effects it doesnt work, and I obtain the following message: "The Composite extension is not available". I think it's strange because I have the pakage libxcomposite1 installed.

Any idea?


Thanks, iccaro.

---

### Post by Forlong on 2007-11-26
You need to install Xgl:
```
sudo apt-get install xserver-xgl
```

---

### Post by iccaro on 2007-11-26
X forlong> thanks, now I have my visual effects activated. Only one thing more, Your links to get the cube don't work...

---

