---
title: "Tried for hours...Just Dont understand."
date: 2006-08-23
forum: Desktop Environments
---

### Post by Linux_Noobie on 2006-08-23
I am trying to get My Ubuntu (With Kde) to look like this. But i dont know how to use some of the stuff. I currently have my desktop looking like this.
[[IMG]http://img138.imageshack.us/img138/4262/snapshot1gl4.th.png[/IMG]](http://img138.imageshack.us/my.php?image=snapshot1gl4.png)
But im trying to get it to look like This.
[http://www.kde-look.org/content/show.php?content=43430](http://www.kde-look.org/content/show.php?content=43430)
[http://www.kde-look.org/content/pre1/43430-1.jpg](http://www.kde-look.org/content/pre1/43430-1.jpg)
I cant figure out how to do the Tranparentsy thing. Or the Start menu. I dont like the defult look of Kde very much. So how do i do the compiz thing and the Kbfx thing. I really want a good looking Desktop running linux(I love the features and inside of linux but graphicly i hate kde but i love the new human thing from that tamilia site. But i wanted to use a vista theme.)

---

### Post by Linux_Noobie on 2006-08-23
Bump?

---

### Post by Tomosaur on 2006-08-23
Screenshots aren't working for me, so it's kinda difficult to tell what you're talking about. There's a very detailed howto about getting Compiz running correctly in the HOWTO section, although I'm not sure what Kbfx is.

Sorry I couldn't be of more help.

---

### Post by Druidor on 2006-08-23
Well it looks like they have custom icon themes installed on the machine runnig the latest KDE.

[http://www.kde-look.org/](http://www.kde-look.org/) for all your little extras you should be able to just drop the themes into KDE Control to add the themes.

---

### Post by Linux_Noobie on 2006-08-23
I went to the kde-look page. Downloaded everything he had. I still cant change the kde bar. Get that semi-tranparent window. or Get the start menu.

---

### Post by ZiZi on 2006-08-23
> **Linux_Noobie said:**
> I went to the kde-look page. Downloaded everything he had. I still cant change the kde bar. Get that semi-tranparent window. or Get the start menu.

The start menu is actually the Kbfx. Read [http://www.kbfx.org](http://www.kbfx.org). Just install the kbfx package (adept or sudo apt-get install kbfx), then you can configure it using systemsettings -> Appearance -> Kbfx, for example the normal/hover/pressed button images and the whole theme itself.

To change the panel appearance, just go to systemsettings -> Panel -> Appearance, check the "Enable background image", then select the BG.PNG image provided with the button icons.

Semi-transparent windows are achieved by xgl + compiz in this case, which is quite demanding to set up, depending on your grapic card. I've found another way to control window translucency by adding a "Extensions" section to my xorg.conf and enabling the Composite manager.
```
Section "Extensions" 
 Option "Composite" "Enable" 
 EndSection
```
Translucency options can then be changed in systemsettings -> Desktop -> Window behaviour -> Translucency. I think these effect don't use DRI and acceleration features of your graphic card, therefore use more memory and CPU and can slow down your computer.

---

