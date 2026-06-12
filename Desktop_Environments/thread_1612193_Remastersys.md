---
title: "Remastersys"
date: 2010-11-02
forum: Desktop Environments
---

### Post by throese on 2010-11-02
Okay, so, I have a question about a section of instructions given here:

[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

What does putting stuff in the /etc/skel/ folder do when using remastersys and why is it recommended to put stuff there?

Also, if it's so important, what folders should go into the /etc/skel/?

Then, in the past when I've tried making a backup disk with a DVD, it gave me some little prompt asking if I wanted to always add these kind of files or never use said files. Referring to the .iso and md5.iso files.

Also, I wiped my laptop completely so all it has is Ubuntu 10.04 LTS Lucid Lynx. I installed it from the CD, seeing as Wubi can only be used via Windows. Anyway, the only Operating System on my laptop is Ubuntu 10.04 LTS Lucid Lynx.

So, any tips/advice would be kind. ^_^

I hope I've given as much useful information as possible.

---

### Post by karmila on 2010-11-03
I want to know about this too, maybe you can ask the writer at his ubuntu thread [http://ubuntuforums.org/showthread.php?t=416802](http://ubuntuforums.org/showthread.php?t=416802).

---

### Post by roccity1 on 2010-11-03
I believe that it is for when the iso is mastered. so if you have set a default wallpaper and other config files for your apps by putting it in /etc/skel this should copy it over and when you boot into your new desktop from the cd or dvd it will have your configs that you have set up.

I think...I could be wrong I usually am :)

Stuff that is in your home folder so .config .gnome stuff like that. You don't want to copy over your music folder or videos. just config folders.

I have found this that should explain a bit better [http://www.linfo.org/etc_skel.html](http://www.linfo.org/etc_skel.html)

---

### Post by throese on 2010-11-03
Thanks. I think I figured out how to go about process without messing up anything, as long as I use VirtualBox.

---

