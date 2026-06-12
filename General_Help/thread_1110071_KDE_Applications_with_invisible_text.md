---
title: "KDE Applications with invisible text"
date: 2009-03-29
forum: General Help
---

### Post by wikwanderlust on 2009-03-29
Alright here's my (newest) situation...I have a fresh install of Ubuntu 8.10. I then installed SMB4K (Because I can't find another way to browse my Windows PC), and Amarok. The problem I'm having with these programs is the text will be visible for a split seond before dissappering. I've uploaded a screenshot of the problem with Amarok. The problem also manifests itself in the right click menu. (I'd send a screenshot of that, but apparently Print Screen won't work if you have a right click menu...At least not for me.

I have a feeling the problem is simple, like a missing font or something. I run Ubuntu 8.10 on an EMacheines w3118  1.8 GHz processor, Nvidia GeForce 6100 Graphic Card (Version 96 driver) I'm assuming that this is too much information, but better to have too much than not enough. Any help would be appreciated. Thanks.

---

### Post by wikwanderlust on 2009-03-29
Believe it or not, this is the first time I've ever done this on any forum...but...Bump.

---

### Post by 3Miro on 2009-03-29
Not sure, but it might be the font color. Text might still be there, just using the same color as the background and thus invisible. Try selecting the text, if it is still there, you might be able to select it.

Font colors could be adjusted from the KDE System Settings.

---

### Post by wikwanderlust on 2009-03-30
Unfortunately, I don't think it's the text colour. My reasoning, which is hard to show in a picture, is when I scroll the songs, or click rapidly, they all appear in black for a split second before disappearing again. If I hold down the scrollbar and pull it up or down, they stay black and visible until I release. Right click menus for Amarok and SMB4K also display similar behaviour; When I right click the icon, the text appears for a split second in black before disappearing. Thanks for the input, though, as any help is greatly appreciated.

---

### Post by wikwanderlust on 2009-03-30
Here's another screenshot, showing the problem in SMB4K...

---

### Post by BRB on 2009-04-15
I'm getting exactly the same behaviour; it seemed to happen about a month ago, after a routine update. This is a problem in several KDE apps, particularly K3B, Amarok, and Digikam. 

The problem does not appear to affect 'core' KDE apps such as Konqueror, Kontact, Korganizer, Konsole or Kate. Other 'contributed' applications such as KTorrent and OKular also work fine.

The problem with thes apps occurs whether I am logged using Gnome or KDE.

I checked for common dependencies of the applications not working, and they all use package kdelibs4c2a v.3.5.10. I reinstalled that package in Synaptic, but this didn't fix the problem. I figure it has to be a problem with some package common to these applications.

Ubuntu 8.10 (Intrepid), Gnome 2.24.1, KDE4.1.4. The specific apps not working are K3b 1.0.5, Amarok 1.4.10, DigiKam 0.9.4, installed from the Intrepid pools.

-- B.

---

### Post by graphius on 2009-06-02
I am having a similar but different problem. the background colour is missing, well half missing (see attached screen shot). I have tried to manually set the background in the theme files, but it doesn't work.
I have tried reinstalling Digikam, no change. It seemed to happen either after an update, or after installing VirtualBox. (these all happened at about the same time)
At least I can still use the program, or install a white theme...

---

