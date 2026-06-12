---
title: "Installed KDE, now problems"
date: 2009-11-23
forum: Desktop Environments
---

### Post by Abadon125 on 2009-11-23
I originally had Ubuntu 9.10.  I just installed KDE using the sudo apt-get install kde desktop (I think) command and all went well, I selected to use gde as my default because I just wanted to take a look at KDE, not use it full time.

Well now whenever I shutdown or start up it shows the KDE splash screen instead of the black screen with the ubuntu logo.  It is confusing though because it still shows the ubuntu screen with the loading bar after that.  

How do I fix my dual-personality OS and make it just use the Ubuntu start up images but still allow me to switch environments at log on?

Thanks so much!

EDIT: After using KDE for like 10 seconds I decided I don't like it as much as gnome, so uninstalling it if that would solve the problem is an option, but I don't know how to do that.  I don't want to mess something up if it replaced files and then they would be missing when I remove it.

---

### Post by Aflack on 2009-11-23
Why does it matter? I did this and i had the KDE splash also.. but i didnt mind lol. I got rid of it when i uninstalled kde. no biggie.

---

### Post by marshmallow1304 on 2009-11-23
[http://embraceubuntu.com/2006/02/20/restoring-the-ubuntu-usplash-after-a-kubuntu-install/](http://embraceubuntu.com/2006/02/20/restoring-the-ubuntu-usplash-after-a-kubuntu-install/)

---

### Post by Abadon125 on 2009-11-23
> **marshmallow1304 said:**
> [http://embraceubuntu.com/2006/02/20/restoring-the-ubuntu-usplash-after-a-kubuntu-install/](http://embraceubuntu.com/2006/02/20/restoring-the-ubuntu-usplash-after-a-kubuntu-install/)

Aww  I was hoping that would work.  Sadly it gave me this error:

```
There are 2 choices for the alternative usplash-artwork.so (providing /usr/lib/usplash/usplash-artwork.so).

  Selection    Path                                       Priority   Status
------------------------------------------------------------
* 0            /usr/lib/usplash/usplash-theme-kubuntu.so   55        auto mode
  1            /usr/lib/usplash/usplash-theme-kubuntu.so   55        manual mode
  2            /usr/lib/usplash/usplash-theme-ubuntu.so    10        manual mode

Press enter to keep the current choice
[*], or type selection number: 2
update-alternatives: using /usr/lib/usplash/usplash-theme-ubuntu.so to provide /usr/lib/usplash/usplash-artwork.so (usplash-artwork.so) in manual mode.

```You can see that I selected option number 2 (because it said ubuntu) but it didn't work.  Any ideas?

EDIT: I was actually able to get it to work.  There was a slight variation in the command I needed and got it working.  Thanks for your help!

---

### Post by Zorael on 2009-11-23
After changing the usplash (as done above), you need to generate a new initramfs if you want the boot splash to also change. (The change to the shutdown splash should take effect immediately.)
```
$ sudo update-initramfs -u -k all
```

---

