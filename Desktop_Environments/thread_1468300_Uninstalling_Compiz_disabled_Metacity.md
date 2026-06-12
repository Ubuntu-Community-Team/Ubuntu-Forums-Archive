---
title: "Uninstalling Compiz disabled Metacity"
date: 2010-05-01
forum: Desktop Environments
---

### Post by krantionline on 2010-05-01
Hi, 

I just installed Ubuntu 10.04 LTS.

I installed compiz for a further Eye-candy. I set reflections on. This, caused my system to log-out over and over again. So i went to the command prompt through the login screen (Ctrl + Alt + F1), and uninstalled Compiz by command 

```
sudo apt-get remove compiz*
```Now, when i login, no window manager comes by default, and when i try 
```
metacity --replace
```It replaces the window manager only till the shell is open. Once i close the shell, the window manager also disappears. 

Please guide me through to enable the window manager.

---

### Post by dino99 on 2010-05-01
reinstall ubuntu-desktop
sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by drreed on 2010-05-01
> **krantionline said:**
> Hi, 

I just installed Ubuntu 10.04 LTS.

I installed compiz for a further Eye-candy. I set reflections on. This, caused my system to log-out over and over again. So i went to the command prompt through the login screen (Ctrl + Alt + F1), and uninstalled Compiz by command 

```
sudo apt-get remove compiz*
```Now, when i login, no window manager comes by default, and when i try 
```
metacity --replace
```It replaces the window manager only till the shell is open. Once i close the shell, the window manager also disappears. 

Please guide me through to enable the window manager.

Did you reboot in between? I was playing around with that awhile back and similar difficulties. I think I had to log out/reboot, then do a metacity --replace. Maybe you can re-install metacity stuff, go look around in synaptic.

---

### Post by krantionline on 2010-05-01
Thanks, Re-installing ubuntu-desktop worked. :KS 
 But the splash screen for startup is not coming now. It was coming earlier. I get a text based startup, followed by a graphical Login Page. Where should I look for this?

---

