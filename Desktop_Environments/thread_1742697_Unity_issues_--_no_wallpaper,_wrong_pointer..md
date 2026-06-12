---
title: "Unity issues -- no wallpaper, wrong pointer."
date: 2011-04-29
forum: Desktop Environments
---

### Post by Karandr on 2011-04-29
[COLOR=#000000][FONT=Arial]Just updated last night to Natty from Maverick. Most things are working fine, but...[/FONT][/COLOR]
[LIST]
[*][COLOR=#000000][FONT=Arial]the  wallpaper is not displaying -- only a light grey. when I go to change  it, the desktop kinda freaks out (black and white shapes at odd angles  behind the window)[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]I've  got the cursor set to redglass at the largest size (my dad uses this  computer and his eyesight is poor) The large red pointer appears in some  areas (Firefox, for example), but not on the desktop or launcher, where the tiny default pointer is used.
[/FONT][/COLOR]
[/LIST]

[COLOR=#000000][FONT=Arial]Didn't have either of these issues in Maverick, so I'm assuming it's something to do with Unity. Thanks in advance.
[/FONT][/COLOR]

---

### Post by zebrattt on 2011-04-30
> **Karandr said:**
> [COLOR=#000000][FONT=Arial]Just updated last night to Natty from Maverick. Most things are working fine, but...[/FONT][/COLOR]
[LIST]
[*][COLOR=#000000][FONT=Arial]the  wallpaper is not displaying -- only a light grey. when I go to change  it, the desktop kinda freaks out (black and white shapes at odd angles  behind the window)[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]I've  got the cursor set to redglass at the largest size (my dad uses this  computer and his eyesight is poor) The large red pointer appears in some  areas (Firefox, for example), but not on the desktop or launcher, where the tiny default pointer is used.
[/FONT][/COLOR]
[/LIST]

[COLOR=#000000][FONT=Arial]Didn't have either of these issues in Maverick, so I'm assuming it's something to do with Unity. Thanks in advance.
[/FONT][/COLOR]


I have this problem too.  still waiting for a solution.  It has been reported as a bug on launchpad.

---

### Post by Krytarik on 2011-04-30
> **zebrattt said:**
> I have this problem too.  still waiting for a solution.  It has been reported as a bug on launchpad.
Where is the link then?!

---

### Post by zebrattt on 2011-04-30
> **Krytarik said:**
> Where is the link then?!

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/773228](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/773228)

---

### Post by zebrattt on 2011-05-01
> **zebrattt said:**
> [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/773228](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/773228)


kubuntu had this problem too, but fixed later.  [https://bugs.launchpad.net/ubuntu/natty/+source/kubuntu-meta/+bug/712612](https://bugs.launchpad.net/ubuntu/natty/+source/kubuntu-meta/+bug/712612)

---

### Post by Krytarik on 2011-05-01
> **zebrattt said:**
> kubuntu had this problem too, but fixed later.  [https://bugs.launchpad.net/ubuntu/natty/+source/kubuntu-meta/+bug/712612](https://bugs.launchpad.net/ubuntu/natty/+source/kubuntu-meta/+bug/712612)
Gives some hope, right!? For now it seems sound just to wait.

If it bugs you too much, you can disable Nautilus' handling of the desktop by unticking the key "/apps/nautilus/preferences/show_desktop" in "gconf-editor". Of course that disables the usual desktop features, like items on it.

---

### Post by zebrattt on 2011-05-02
> **Krytarik said:**
> Gives some hope, right!? For now it seems sound just to wait.

If it bugs you too much, you can disable Nautilus' handling of the desktop by unticking the key "/apps/nautilus/preferences/show_desktop" in "gconf-editor". Of course that disables the usual desktop features, like items on it.

thanks.  I just did that.  I went through almost all recent posts on wallpaper.  yes, it could be a temporary solution.

---

### Post by Krytarik on 2011-05-02
> **zebrattt said:**
> I went through almost all recent posts on wallpaper.
I know. ;-)

---

### Post by zebrattt on 2011-05-02
> **Krytarik said:**
> I know. ;-)


haha,  I solved this problem perfectly by installing Nautilus Elementary! 

ubuntu tweak has the source for elementary already, just check it and update.

---

### Post by Krytarik on 2011-05-02
> **zebrattt said:**
> haha,  I solved this problem perfectly by installing Nautilus Elementary! 

ubuntu tweak has the source for elementary already, just check it and update.
I do like the concept and look of Nautilus Elementary, too! But unfortunately it seems like it doesn't work with my legacy nvidia-96 video driver, since I get graphical glitches when scrolling long directory trees.

Maybe it's fixed in the current version, I don't know, since I'm still running Lucid 10.04, and plan to do so until at least the end of April 2013; not just for NE. And of course I have no wallpaper issue anyway. :P

---

### Post by zebrattt on 2011-05-02
> **Krytarik said:**
> I do like the concept and look of Nautilus Elementary, too! But unfortunately it seems like it doesn't work with my legacy nvidia-96 video driver, since I get graphical glitches when scrolling long directory trees.

Maybe it's fixed in the current version, I don't know, since I'm still running Lucid 10.04, and plan to do so until at least the end of April 2013; not just for NE. And of course I have no wallpaper issue anyway. :P

you should try it again.  i guess it's been improved a lot.  :)     I enjoy it a lot.

---

### Post by Krytarik on 2011-05-03
> **zebrattt said:**
> you should try it again.  i guess it's been improved a lot.  :)     I enjoy it a lot.
I know these features, and I also like the slimmed down look of it. But in fact, the packages for Lucid in its PPA haven't been upgraded since Oktober last year. Actually, I just re-checked it some weeks ago, hoping that my driver or any other responsible package has been upgraded, still no dice.

Just for your information, there was a move the cease the development of NE in favour of its new project, Marlin, in fact it has already been declared November last year. But they just reactivated it because of their Jupiter OS project, see here:
[http://ammonkey.posterous.com/nautilus-elementary-project-reactivated-jupit](http://ammonkey.posterous.com/nautilus-elementary-project-reactivated-jupit)

So, have fun with it, for the time being!

---

### Post by zebrattt on 2011-05-04
> **Krytarik said:**
> I know these features, and I also like the slimmed down look of it. But in fact, the packages for Lucid in its PPA haven't been upgraded since Oktober last year. Actually, I just re-checked it some weeks ago, hoping that my driver or any other responsible package has been upgraded, still no dice.

Just for your information, there was a move the cease the development of NE in favour of its new project, Marlin, in fact it has already been declared November last year. But they just reactivated it because of their Jupiter OS project, see here:
[http://ammonkey.posterous.com/nautilus-elementary-project-reactivated-jupit](http://ammonkey.posterous.com/nautilus-elementary-project-reactivated-jupit)

So, have fun with it, for the time being!

the link is not working temporarily, but sounds good.  thanks for your info.  I'll keep an eye on it.

---

### Post by justborn on 2011-05-18
> **zebrattt said:**
> haha,  I solved this problem perfectly by installing Nautilus Elementary! 

ubuntu tweak has the source for elementary already, just check it and update.


**PERFECT** solution huh??he second one isn&#8217;t a perfect solution too.when i login i get the same wallpaper that was before updating from the repos&#8230;..the selected wallpaper remains only untill the particular session.

---

