---
title: "I seem to have uninstalled Unity, how do I get it back?"
date: 2012-07-30
forum: Desktop Environments
---

### Post by picklemaster246 on 2012-07-30
Couple of questions:

In an attempt to get wallpapers to stay "wallpapered" in xfce, I deleted Nautilus because some guy said that might have solved the issues.  When I rebooted, the Unity options are missing and all I have are xfce session, Xubuntu Session, and the GNOME classic options when logging in.  Even reinstalling Nautilus doesn't bring back the Unity option.  How do I get Unity back?

How do I get wallpapers to stick in xfce?  

Finally, how would I uninstall xfce?  The official website says to install xubuntu-desktop, which is how I got xfce in the first place, but after sudo apt-get remove xubuntu-desktop, the xfce session and Xubuntu session options are still useable when I log in.  If I'm not being clear on stuff, let me know please. Help is very much appreciated.

---

### Post by IWantFroyo on 2012-07-30
Use this to get rid of XFCE:

[http://psychocats.net/ubuntu/pureubuntu](http://psychocats.net/ubuntu/pureubuntu)

As for Unity:

```
sudo apt-get install unity
```?

---

### Post by markbl on 2012-07-30
Rather than install unity package as above post, you are best to do:
```

apt-get install ubuntu-desktop

```

---

### Post by ajgreeny on 2012-07-30
This may be too late, but to run nautilus successfully without it taking over the desktop and causing problems in xfce (xubuntu) you need to edit the nautilus.desktop file in /usr/share/applications and change the **Exec=nautilus** line to **Exec=nautilus --no-desktop**.  Any other instances of the launcher also need to be changed.

Without that edit nautilus attempts take over and write the desktop when you first start it in a session, just as it does in gnome, and that can have some strange effects on the display of wallpapers, etc etc.

---

### Post by picklemaster246 on 2012-07-30
> **markbl said:**
> Rather than install unity package as above post, you are best to do:
```

apt-get install ubuntu-desktop

```

This worked!

> **ajgreeny said:**
> This may be too late, but to run nautilus successfully without it taking over the desktop and causing problems in xfce (xubuntu) you need to edit the nautilus.desktop file in /usr/share/applications and change the **Exec=nautilus** line to **Exec=nautilus --no-desktop**.  Any other instances of the launcher also need to be changed.

Without that edit nautilus attempts take over and write the desktop when you first start it in a session, just as it does in gnome, and that can have some strange effects on the display of wallpapers, etc etc.

This didn't.  The image I want as my wallpaper is on my Windows partition and I selected the image through a symbolic link, so would that cause problems?  What do you mean by "launcher", just any button?

---

### Post by ajgreeny on 2012-07-31
> **picklemaster246 said:**
> This worked!



This didn't.  The image I want as my wallpaper is on my Windows partition and I selected the image through a symbolic link, so would that cause problems?  What do you mean by "launcher", just any button?
What I meant was that any other instances of the nautilus.desktop file (the launcher I spoke of) may need to have that edited command, but as it did not help your problem you can forget about it for now.

However, as an example, if I run xubuntu with a conky display on the desktop with a transparent window, as soon as I run nautilus without the no-desktop option, it tries to take over the desktop display and my conky window looses transparency.  Not a major disaster, but annoying.  I thought your problem might be related to that, but I suspect that it may be more to do with the fact that the image you want to use is linked to from a windows partition.

---

### Post by kansasnoob on 2012-07-31
> **markbl said:**
> rather than install unity package as above post, you are best to do:
```

apt-get install ubuntu-desktop

```

+1!

---

### Post by picklemaster246 on 2012-08-01
> **ajgreeny said:**
> but I suspect that it may be more to do with the fact that the image you want to use is linked to from a windows partition.

Yep, this was the problem.  Thanks a bunch!

---

