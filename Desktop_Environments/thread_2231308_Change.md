---
title: "Change"
date: 2014-06-24
forum: Desktop Environments
---

### Post by kakashi_12 on 2014-06-24
How do I change my desktop environment. I hate Unity. I liked GNome. I like LXDE, but I have a fast computer. Can this easily be done from the Software Center, rather than through the terminal?

I gave Kubuntu a try, but was not crazy about the environment. Better than Unity though. Anyone have suggestion of what to run on a fast 64 bit pc that is classic like look like GNome, LXDE, or WinXP kind of look?
And how do I make a bootable thumbdrive of the OS, so I don't keep wasting discs... to try them out Live?

---

### Post by deadflowr on 2014-06-24
If you want a classic gnome like desktop, simply look for gnome flashback in the software center.
Same for lxde, simply search for it in the software center.

I'm not sure using the software center is any quicker, but you won't have to know the exact name of whichever desktop you decide to try.

Once installed, log out and in the login screen, if the login screen has not changed(sometimes the new desktop replaces the login screen with whichever new desktop's greeter you have installed), click on the icon in the top right corner of the box where you put your name and password --you will see a list of desktops to choose from.

As for bootable usb sticks, look at something like unetbootin.

---

### Post by ibjsb4 on 2014-06-24
> **kakashi_12 said:**
> How do I change my desktop environment. I hate Unity. I liked GNome. I like LXDE, but I have a fast computer. Can this easily be done from the Software Center, rather than through the terminal?

Its easy in terminal :)

[http://ubuntuforums.org/showthread.php?t=797223&page=320&p=13057652#post13057652](http://ubuntuforums.org/showthread.php?t=797223&page=320&p=13057652#post13057652)

---

### Post by kakashi_12 on 2014-06-24
That command does not work in Kubuntu and just tried to find it in software center, wasn't there. Also could not find any boot manager software in software center either. VERY limited software available in Software Center. Kubuntu stinks. I guess that distro is out of the water.

---

### Post by deadflowr on 2014-06-24
It's a tit for tat thing.
You could provide us info on which version you are using.
Kubuntu uses the exact same repos as Ubuntu does.

But each version(12.04, 13.10, or 14.04) can have different packaging names, depending...

---

### Post by kakashi_12 on 2014-06-24
Using the latest version. 14.04
How come when I search, barely anything comes up?

---

### Post by kakashi_12 on 2014-06-25
I uninstalled Kubuntu and just installed Ubuntu 14.04. Could not find that exact program in Software Center, but the command that was provided did work :) Any way I can make GNome the default log-in without having to click it (for all users)?

---

### Post by LastDino on 2014-06-25
Just saying but you could've installed Gnome version of Ubuntu to boot from rather than going install unity>install gnome flashback. 

Yeah, you can make Gnome default log in by running something like this in terminal when you're logged in.

```

sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-shell
```

---

### Post by ibjsb4 on 2014-06-25
> **kakashi_12 said:**
> Using the latest version. 14.04
How come when I search, barely anything comes up?
Try a different search engine.
[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by deadflowr on 2014-06-25
> **LastDino said:**
> Just saying but you could've installed Gnome version of Ubuntu to boot from rather than going install unity>install gnome flashback. 

Yeah, you can make Gnome default log in by running something like this in terminal when you're logged in.

```

sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-shell
```

First, I don't think that command works for 14.04, as it did for earlier versions.
Second the command wants the name via the xsession desktop file.
I believe gnome-shell is simply Gnome, where as gnome-flashback is gnome-flashback(effects, or no effects)
You can find session names in /usr/share/xsessions.
But here's how to change it in 14.04
[https://wiki.ubuntu.com/LightDM#Changing_the_Default_Session](https://wiki.ubuntu.com/LightDM#Changing_the_Default_Session)

---

### Post by LastDino on 2014-06-26
> **deadflowr said:**
> First, I don't think that command works for 14.04, as it did for earlier versions.
Second the command wants the name via the xsession desktop file.
I believe gnome-shell is simply Gnome, where as gnome-flashback is gnome-flashback(effects, or no effects)
You can find session names in /usr/share/xsessions.
But here's how to change it in 14.04
[https://wiki.ubuntu.com/LightDM#Changing_the_Default_Session](https://wiki.ubuntu.com/LightDM#Changing_the_Default_Session)

Makes sense, I never tried 14.04 Unity and 14.10 has pleased me enough to not install gnome flashback. Thanks for confirming this.

---

