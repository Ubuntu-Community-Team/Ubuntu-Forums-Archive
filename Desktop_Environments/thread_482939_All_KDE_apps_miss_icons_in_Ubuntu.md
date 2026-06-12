---
title: "All KDE apps miss icons in Ubuntu"
date: 2007-06-24
forum: Desktop Environments
---

### Post by Magnentius on 2007-06-24
Hi all,

I've a very strange problem. I use UbuntuCE 7.04 and when I use KDE software like K3B or ksnapshot or kate under Gnome, they miss all their icons. I tried to resolve this problem by installing kubuntu-desktop using adept, but when I choose a KDE session, the entire KDE desktop misses his icons.

[IMG]http://Pixsup.com/uploads/8be0a9594a.jpg[/IMG]

I hope someone can help me with this. Thanks in advance!

Magnentius

---

### Post by bluknight on 2007-06-24
Mine too in Feisty. For amarok when I configure settings the icons there are missing too.

---

### Post by Magnentius on 2007-06-24
Yes, I also prefer amarok above rythmbox, but it is unusable now. I forgot to say that KDE apps take a very long time to load under Gnome. When you start K3B for instance, nothing happens for about 15 seconds, and then it appears with no icons.

---

### Post by ComplexNumber on 2007-06-24
do you have the kdeartwork packages installed?

---

### Post by Magnentius on 2007-06-24
Thanks for your help. No, I didn't have kdeartwork, but after there are still no icons after installing it and rebooting.

---

### Post by Magnentius on 2007-06-24
{spitFire} gave another possible solution [here]("http://ubuntuforums.org/showthread.php?p=2905250"):
> IMO, the icons are fetched from pre-defined locations like
* ~/.icons
* /usr/share/icons
* /usr/share/pixmaps

and when Gnome can't find an icon associated with an app, it loads the default icon, which in your case seems to be a piece of paper or whatever! I think it is the problem with your current icon theme! Load some other icon theme (either from the defaults installed or from more sexy ones from [www.gnome-look.org](www.gnome-look.org)), and the apps should get their icons back.

But it doesn't work. Anyone an other solution, please?

---

### Post by Magnentius on 2007-06-25
I've submitted this as a bug report to [https://bugs.launchpad.net/ubuntu/+bug/122117]("https://bugs.launchpad.net/ubuntu/+bug/122117")

---

