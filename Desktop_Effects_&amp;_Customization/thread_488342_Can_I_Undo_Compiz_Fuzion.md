---
title: "Can I Undo Compiz Fuzion?"
date: 2007-06-30
forum: Desktop Effects &amp; Customization
---

### Post by jmusso on 2007-06-30
Okay, so I'm new to Ubuntu. I want to try out Compiz Fuzion. I've found a few sites that look like they tell me what I need... they are:

[http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)
and
[http://www.compiz.org/Compiz_and_Copmiz_Fusion_GIT_Ubuntu_Repository#Feisty_Repository](http://www.compiz.org/Compiz_and_Copmiz_Fusion_GIT_Ubuntu_Repository#Feisty_Repository)

I think I enabled my vid card by going to System > Administration > Restricted Drivers and clicking "enable" for my video card. I'm running the ATI Radeon Xpress 200m on my Compaq Presario v5000. Will this work?

But most importantly, my question is, after I install Compiz Fuzion according to those guides... If it messes my system up, can I easily remove it and revert to the way everything was BEFORE I installed it...?

Thanks.

---

### Post by hyperair on 2007-06-30
Sure it's possible, but it won't be as easy as installing it.

---

### Post by jmusso on 2007-06-30
That's okay. Do you know how? Or are there any guides already detailing how? I can't seem to find anything, I've been scouring the forums for over two hours...

---

### Post by hyperair on 2007-06-30
Yeah I know how, but I don't see any guides detaling how around. So here it is:

**Only for Ubuntu, NOT for Kubuntu or Xubuntu**
1. Get your X Server working (if it isn't. if it is, then just skip to step 2) 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
2. Disable Trevino's eyecandy repositories
2.1 Go to System->Administration->Software Sources->Third party repositories
2.2 Uncheck all the entries that correspond to Trevino's eyecandy repositories (which you had added during installation
2.3 Close the window. You'll be prompted to reload the repository info. Click reload
3. Uninstall compiz and reinstall it (it should reinstall the version from the Ubuntu repositories)
** Use EITHER 3.1 or 3.2, but not both. **
3.1 The terminal method:
```
sudo apt-get autoremove compiz*
sudo apt-get install ubuntu-desktop

```
3.2 The GUI method:
3.2.1 Open Synaptic Package Manager.
3.2.2 Run a search for compiz (Look In: name)
3.2.3 Uninstall everything
3.2.4 Apply
3.2.5 Once it's done, look for ubuntu-desktop and install it.

---

