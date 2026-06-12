---
title: "kubuntu desktop or kde package?"
date: 2005-09-29
forum: Desktop Environments
---

### Post by btdown on 2005-09-29
I have regular breezy installed and want to apt-get kde to see if its working any better than hoary did for me. I'd like it to be set up so that I could log into either a KDE or gnome session, and keep the two separate (does that make sense?)
 
So the question is, what would I install, the kde package(s) or the kubuntu-desktop pkg? or ?
 
Thanks,
 
Any input would be appreciated
BT

---

### Post by twigsby on 2005-09-29
I had to use both. With just the Kubuntu package things were very sluggish.

---

### Post by mlomker on 2005-09-29
kubuntu-desktop includes all of Kubuntu.  kde-core will get you just the desktop and none of the add-on applications.

---

### Post by btdown on 2005-09-30
Well, I installed the KDE pkg and unfortunately I did what I was trying to avoid. I dont know why, but it annoys me to no end to be logged into gnome and see like 9 million K* programs in there.

---

### Post by mlomker on 2005-09-30
[QUOTE=btdown]Well, I installed the KDE pkg and unfortunately I did what I was trying to avoid. I dont know why, but it annoys me to no end to be logged into gnome and see like 9 million K* programs in there.[/QUOTE]

Yup.  I get the same thing in KDE with the gnome apps.  You put your chocolate in my peanut butter!  Darn...I guess peanut butter cups aren't too bad.

---

### Post by Knome_fan on 2005-09-30
[QUOTE=btdown]Well, I installed the KDE pkg and unfortunately I did what I was trying to avoid. I dont know why, but it annoys me to no end to be logged into gnome and see like 9 million K* programs in there.[/QUOTE]
I think this is pretty unavoidable, but pretty annoying nontheless. 
However, there is a dirty workaround:
As root go to /usr/share/applications/kde/ and issue the following command:
```
for i in *; do echo "OnlyShowIn=KDE;" >> $i; done
```

---

### Post by btdown on 2005-09-30
Wow! Thanks for the tip. Much appreciated.

---

### Post by mlomker on 2005-09-30
You'll need to add that line to each .desktop whenever you add an application.  I also wonder if it'd be overwritten on upgrades?

---

### Post by Knome_fan on 2005-09-30
[QUOTE=mlomker]You'll need to add that line to each .desktop whenever you add an application.  I also wonder if it'd be overwritten on upgrades?[/QUOTE]
Yes to both.
As I said, it's a dirty workaround.
But you could of course always expand on the concept to make it usable after an updgrade.
Something like this comes to mind (untested): 
for i in `grep -L OnlyShowIn *`; do echo "OnlyShowIn=KDE;" >> $i; done

---

### Post by apokryphos on 2005-09-30
all fully explained on wiki.ubuntu.com/InstallingKDE

---

