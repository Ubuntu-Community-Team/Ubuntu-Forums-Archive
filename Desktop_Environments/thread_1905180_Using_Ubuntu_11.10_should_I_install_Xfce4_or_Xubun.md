---
title: "Using Ubuntu 11.10 should I install Xfce4 or Xubuntu-desktop?"
date: 2012-01-06
forum: Desktop Environments
---

### Post by manilaph on 2012-01-06
Hi.

I am currently using the Ubuntu 11.10 on Gnome-fallback mode. It is much better than Unity or Gnome 3 Shell.

I want to try Xfce4 (Xubuntu) but I do not know what I should install?

If I install the Xubuntu-desktop, it will install other things like Abiword, Gnumeric and lots of stuff that are redundant like xfburn etc.

Should I just install:

```
sudo apt-get install xfce4
```

or 

```
sudo apt-get install xubuntu-desktop
```

would having xubuntu and ubuntu slow down my system?

thank you!

---

### Post by mastablasta on 2012-01-06
use the first one then
 
 
and no.

---

### Post by cottfcfan on 2012-01-06
I installed xfce4, to stop the other apps being included.
Speed wise it appears just as fast as Xubuntu.
The problems you may have though are Nautilus, which I had to uninstall as it kept on conflicting with Thunar, and I also uninstalled gvfs-backends as it caused a delay in file opening.
Other than that it seems to work fine.
Just remember to reinstall those programs if you go back to Ubuntu.

---

### Post by kurt18947 on 2012-01-06
> **cottfcfan said:**
> I installed xfce4, to stop the other apps being included.
Speed wise it appears just as fast as Xubuntu.
The problems you may have though are Nautilus, which I had to uninstall as it kept on conflicting with Thunar, and I also uninstalled gvfs-backends as it caused a delay in file opening.
Other than that it seems to work fine.
Just remember to reinstall those programs if you go back to Ubuntu.

I did the same because I'm not a fan of Unity either though I can cope with it.  I prefer Gnome-shell though.  I was offered a choice of Nautilus or Thunar.  I chose Nautilus, the only problem is that every time I open xfce, Nautilus opens my /home folder.  Thunar doesn't do that but it's a minor annoyance, I just click 'close'.  I have my preferred Gnome apps without the Unity WM.

---

### Post by manilaph on 2012-01-06
Thank you for your replies.

I just did the 

```
sudo apt-get install xfce4
```

and now my next question is:

should I install the additional stuff like:

xubuntu restricted-extras
xubuntu restricted-addons
xfce4 goodies

i am currently using adobe flash-plugin and I noticed that if I install the restricted-extras it will remove adobe and moreso, it will install icedtea which I removed because I am using sun-java jre/plugin instead of icedtea.

cheers!

---

### Post by manilaph on 2012-01-06
actually I am using Xfce4 right now (chosen from the log-in menu) and there does not seem to be a significant speed difference compared to using Gnome.

is there an actual benchmark comparison between Xubuntu and Ubuntu (Gnome-fallback)?

---

### Post by cottfcfan on 2012-01-07
There probably isn't a great deal of difference if your using gnome-fallback without effects. That gets rid of Compiz which can be quite a system drag, and uses metacity instead.
 But Xubuntu is definitely faster than Unity, and the main advantage is that it is more configurable (at the moment) than anything Gnome3 based.

---

### Post by manilaph on 2012-01-07
Thanks again for the info.

By the way, can I remove everything that deals with Unity or will this screw-up my system? I tried it and it said it will remove the Ubuntu-desktop.

---

