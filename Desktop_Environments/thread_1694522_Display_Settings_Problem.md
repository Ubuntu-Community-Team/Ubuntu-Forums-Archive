---
title: "Display Settings Problem"
date: 2011-02-24
forum: Desktop Environments
---

### Post by xorxe85 on 2011-02-24
Hello, yesterday I received Ubuntu 10.10 (a friend gave me the cd) Well, I installed, but I can't change the display settings: the maximum it gives is 900x600

So, I went online and looked for a fix.. I found this:

```
Sudo dpkg-reconfigure x server-xorg
```Well, the problem is that according to the steps that the person who posted the code, I should type this code after executing Terminal before computer boots... and the way to execute Terminal is to have the key: escape holded

Well, I do hold the key: escape... but I see no terminal! I have typed in normal mode...but, I guess the code only works before boot up...

How can I execute terminal? is there any other way to fix the display settings?

I currently have Windows Xp and Ubuntu.... and I have no problem with the display settings on Xp


Can I do do from recovery mode?

Because I have 2 operating systems I get a screen like this (except mine is ubuntu 10.10)

[IMG]http://farm1.static.flickr.com/153/351969105_18d03118ed.jpg[/IMG]

If I do it from the recovery mode.... would the code works?

Please help... I am new on Ubuntu... and I usually work on 1152x864 or 1024x768


Thanks!!!

---

### Post by Krytarik on 2011-02-24
You don't need to run the command at the console, in a "Terminal" in Gnome would be sufficient. But aside from the fact that the command is somewhat wrong spelled, it wouldn't create a xorg.conf anymore nowadays! And you don't need necessarily to set up a xorg.conf to achieve the desired solution, try instead first to set it with "xrandr" commands:
[https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions]("https://wiki.ubuntu.com/X/Config/Resolution#Adding%20undetected%20resolutions")

Btw., your boot menu looks fairly cool! ;-)

---

