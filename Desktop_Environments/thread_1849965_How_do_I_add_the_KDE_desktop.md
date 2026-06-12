---
title: "How do I add the KDE desktop?"
date: 2011-09-25
forum: Desktop Environments
---

### Post by Mazate on 2011-09-25
Currently using Unity but I'd also like to be able to use KDE.  Used to using YUM on fedora so I'm unsure of some of the command line changes in Ubuntu.

Thanks!

---

### Post by SecretCode on 2011-09-25
```
sudo aptitude install kubuntu-desktop
``` should do it!

---

### Post by b2zeldafreak on 2011-09-25
> **SecretCode said:**
> ```
sudo aptitude install kubuntu-desktop
``` should do it!

or 
```
sudo apt-get install kubuntu-desktop
```

---

### Post by Krytarik on 2011-09-25
Personally, I would just install plain KDE - package "kde" - , not the complete Kubuntu package:
```
sudo apt-get install kde
```See here about the different meta-packages available:

[https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

Greetings.

---

### Post by Mazate on 2011-09-25
> **b2zeldafreak said:**
> or 
```
sudo apt-get install kubuntu-desktop
```

Ok, I did this and it installed KDE.  During the install process it asked me which I wanted to be the default desktop and I chose KDE.  After it finished installing, I restarted.  It came up with a blue splash screen and asked me to login.  I logged in.  Now all I have is that same splash screen with a terminal window.  Nothing else is on the screen.  Did I forget something?

---

### Post by Mazate on 2011-09-25
> **Krytarik said:**
> Personally, I would just install plain KDE - package "kde" - , not the complete Kubuntu package:
```
sudo apt-get install kde
```See here about the different meta-packages available:

[https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

Greetings.
   

Wish I had seen this before I did the install.  What's the difference between installing just the KDE desktop and KUBUNTU?  Does that reinstall the whole OS?

---

### Post by Krytarik on 2011-09-25
Well, in absence of a response from any of those who suggested "kubuntu-desktop"; at the login screen of your newly chosen display manager - KDM - , click the first button left-below of the sign-in box, it should offer to choose the different session options.

Reg. the differences between "kubuntu-desktop" and "kde", see the previously posted link.

---

### Post by Mazate on 2011-09-25
> **Krytarik said:**
> Well, in absence of a response from any of those who suggested "kubuntu-desktop"; at the login screen of your newly chosen display manager - KDM - , click the first button left-below of the sign-in box, it should offer to choose the different session options.

Reg. the differences between "kubuntu-desktop" and "kde", see the previously posted link.

Well, I did log into kde but I got what I described above-essentially a kde background with a terminal window open up in the corner. Nothing else.

---

### Post by Krytarik on 2011-09-25
I just noticed that those community doc - once again - tricked me. The meta-package I was referring to is - since Lucid 10.04 - named "kde-full", not just "kde" anymore. =D>

You can check the packages each meta-package is pulling here:

"kubuntu-desktop": [http://packages.ubuntu.com/natty-updates/kubuntu-desktop](http://packages.ubuntu.com/natty-updates/kubuntu-desktop)

"kde-full": [http://packages.ubuntu.com/natty/kde-full](http://packages.ubuntu.com/natty/kde-full)


Reg. the login issue, try choosing GDM again:

1. In the terminal you are currently getting, run:
```
sudo dpkg-reconfigure gdm
```2. Choose "gdm".

3. Reboot.

---

### Post by SecretCode on 2011-09-26
> **Mazate said:**
> It came up with a blue splash screen and asked me to login.  I logged in.  Now all I have is that same splash screen with a terminal window.  Nothing else is on the screen.  Did I forget something?

Not obviously, but something is wrong.

At the login screen do you have a choice of sessions? If you are using KDE's login screen click the blue arrow & it should look like this:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=202967&stc=1&d=1317030814[/IMG]

If you've gone back to gdm as suggested above it should look like this, but should have the above entries (not necessarily the 'Default' line):
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=202966&stc=1&d=1317030814[/IMG]

Make sure you select "KDE Plasma Workspace".

---

