---
title: "Is there a Nautilus alternative ?"
date: 2008-07-09
forum: Desktop Environments
---

### Post by oygle on 2008-07-09
I'm having way too many problems with Nautilus ( see [http://ubuntuforums.org/showthread.php?t=784259](http://ubuntuforums.org/showthread.php?t=784259) ) ; it seems lots of other people are also having the same issues.

I can now view/browse with nautilus, but not write to the XP computer (as I was able to do with Gutsy).

Is there an alternate browser that someone can recommend please ?

---

### Post by cpetercarter on 2008-07-09
xfe

---

### Post by OutOfReach on 2008-07-09
Well, theres always Dolphin (KDE's default file browser), Thunar (XFCE's default browser. Theres some other ones that I can't remember right now. Dolphin is in the repos, im not sure about Thunar, you can check though.

---

### Post by DirtDawg on 2008-07-09
You may want to check out ntfs-config tool. After install, it shows up in Applications>SystemTools and allows you to change the write permission on an internal or external ntfs drive.
```
sudo apt-get install ntfs-config
```

As far as alternative browsers go, I recommend Thunar. It's in the repos, but you may have to dig around for instructions for assigning it as the default browser.

---

### Post by atomkarinca on 2008-07-09
Thunar is an excellent replacement for Nautilus. You should also check out PCMan file manager.

---

### Post by sayakb on 2008-07-09
Also try out  PCMan File Manager and ROX Filer.

---

### Post by urukrama on 2008-07-09
Thunar is excellent: good looking, fast, light, and configurable. It is my absolute favourite file manager.

PCManFM is decent too; Rox-filer is something you have to get used to (I never did). Dolphin or Konqueror are KDE apps and will therefore be a bit slower in Gnome (as you need to load some KDE libraries to run them).

If you want to replace Nautilus entirely (so that the entries in the Places menu don't load Nautilus), and set another file manager as the default, have a look at [aysiu's guide]("http://psychocats.net/ubuntu/nonautilusplease").

---

### Post by konungursvia on 2008-07-09
+1 for thunar.

---

### Post by imwithid on 2010-11-07
Yes, Thumar is quick, however, if you have other partitions, it may be a nuisance in setting that up. I'm not too familiar with fstab, but I think you have to make some changes in the /etc/fstab file or some configuration file linked to fstab.

---

### Post by 73ckn797 on 2010-11-07
Check out gnome-commander in Synaptic.

---

### Post by pete_l on 2011-02-06
> **73ckn797 said:**
> Check out gnome-commander in Synaptic.
Ha, ha. Very funny. I'll use that next time I want my Ubuntu 10.10 installation converted into a DOS system circa. 1985 (Having said that, a single panel of gnome-commander is far superior (in terms of less irrelevant visual embellishments) to Nautilus).

---

### Post by Copper Bezel on 2011-02-06
> If you want to replace Nautilus entirely (so that the entries in the Places menu don't load Nautilus), and set another file manager as the default, have a look at aysiu's guide.

You don't have to replace Nautilus entirely to get the Places menu to talk to Thunar instead. Right-click a folder in Nautilus, select Open With - > Other Application, select Thunar, and make sure that the "Remember" checkbox is marked. All it takes.

The desktop will still be managed by Nautilus, and double-clicking a folder there will load a Nautilus window, but you can always right-click and select "open with Thunar."

---

### Post by dmizer on 2011-02-28
Replacing Nautilus isn't going to fix your problem because your problem is completely unrelated to Nautilus. Your problem is that you are unable to browse Windows shares, and that is a problem with samba, not Nautilus.

Please see the 6th link in my sig for how to fix your problem.

---

### Post by oygle on 2011-03-01
Okay thanks. Your 'how to' looks good. I had forgotten about this thread, and have been copying files to and from Ubuntu computers, via a USB stick (not high volume, a few times per week).  :)

---

