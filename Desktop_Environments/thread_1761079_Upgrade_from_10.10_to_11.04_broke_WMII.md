---
title: "Upgrade from 10.10 to 11.04 broke WMII"
date: 2011-05-17
forum: Desktop Environments
---

### Post by pimparello on 2011-05-17
Hello guys, 
i am looking for help. I have upgraded from 10.10 to 11.04. I have been using wmii as window manager under ubuntu for years. After the upgrade it's entirely broken. 

The metakey is not working anymore, I cannot do anything. The key itself works fine in other environments so is's no hardware issue.  After several attempts I completely uninstalled wmii, removed all relevant folders in home and /etc/X11 and reinstalled wmii from the ubuntu repositories. 

This fresh install does not work.  It starts a strange looking wmii without any key responding to my actions.  I copied my old wmiirc to ~/.wmii. When i log in I see my individualized wmii but the metakey is not working and i cannot do anything, like opening a shell. 

So, what can I do? Please help, I need to use wmii again, I am going crazy with gnome, fluxbox, etc...

Thx!


Edit: A change to "MODKEY=ALT" in wmiirc does not change anything.

---

### Post by wildmanne39 on 2011-05-18
> **pimparello said:**
> Hello guys, 
i am looking for help. I have upgraded from 10.10 to 11.04. I have been using wmii as window manager under ubuntu for years. After the upgrade it's entirely broken. 

The metakey is not working anymore, I cannot do anything. The key itself works fine in other environments so is's no hardware issue.  After several attempts I completely uninstalled wmii, removed all relevant folders in home and /etc/X11 and reinstalled wmii from the ubuntu repositories. 

This fresh install does not work.  It starts a strange looking wmii without any key responding to my actions.  I copied my old wmiirc to ~/.wmii. When i log in I see my individualized wmii but the metakey is not working and i cannot do anything, like opening a shell. 

So, what can I do? Please help, I need to use wmii again, I am going crazy with gnome, fluxbox, etc...

Thx!


Edit: A change to "MODKEY=ALT" in wmiirc does not change anything.

Hi, maybe this will help. Also look at the links in my signature below this text and you will learn a lot about customizing natty. Also this can be set as background so you will have the list of short cuts until you get use to them.

---

### Post by hpainter on 2011-05-27
I'm in the same boat as the OP...wmii doesn't respond to any key combinations and I'm stumped on how to proceed.

---

### Post by Jinx-Wolf on 2011-06-13
Ubuntu users are not alone! I am having similar issues with my Slackware 13.37. I just so happened to stumble upon this thread while researching the issues I'm having. Here's my thread from [LinuxQuestions.org]("http://www.linuxquestions.org/questions/slackware-14/wmii-slackware-13-37-a-885632/")

Some system info so we can compare:
ThinkPad x201
Core i5 540
GMA HD Graphics
Slackware 13.37
kernel 2.6.38.4-smp
2D driver: xf86-video-intel 2.15.0 release
3D driver: mesa 7.10.2 release
Libdrm: libdrm-2.4.25 release

---

### Post by Senesence on 2011-07-15
As I'm sure you guys noticed, 11.04 comes with a more recent version of wmii (3.9), which is not compatible with your old 3.5 configuration files.

You can copy the "new-style" wmiirc in **/etc/X11/wmii** to **~/.wmii**, and then edit that.

It's basically the same structure, with slightly different syntax in certain places, so it shouldn't be too difficult.

---

