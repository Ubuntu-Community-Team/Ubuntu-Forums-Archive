---
title: "slow dropdown menus after Beryl"
date: 2007-06-08
forum: Desktop Effects &amp; Customization
---

### Post by albesan on 2007-06-08
hello team,

I'm getting really slow dropdown menus (applications, places, system menus for example) after installing Beryl.
Everything else is working like a charm.
I'm running a low latency ubuntu studio, on a Dell Inspiron 6400, Intel integrated graphics.

I've run beryl in the past and it worked fine, the only differences are that I manage to make it work on a dual screen and that I'm running ubuntu studio.

Any comments apreciated, thanks.

a.

---

### Post by nate_nightroad on 2007-06-08
probably u r using intergrated graphic card and running dual screen....tat's alot of pressure on the on board graphic card.....

try turning off the dual screen and see if there is any diff

---

### Post by albesan on 2007-06-08
Hey thanks for the reply,

Not really it doesn't make any difference.
Everything else runs like the wind. It is not glitchy. There is just a delay on dropdown lists and menus, every other button/interaction run at normal speed, it feels more responsive than metacity.

I tried setting the menu pop up delay to 0 using this :
[http://ubuntuforums.org/showthread.php?t=215119](http://ubuntuforums.org/showthread.php?t=215119)

Which worked wonders for Dapper on older machines but it did not make any difference on ubuntu studio.
I turned all of the animation features in Beryl and the dropdown menus are still slow as long as I keep running the beryl window manager.

I'll keep looking and trying and post back.

thanks.

a.

---

### Post by ktulu1115 on 2007-10-18
same issue here.  just installed fresh gutsy copy.  running dual display, separate x screens (no twinview or xinerama).  only a delay on one of the screens (main screen 0)  my additional 2nd display has no delay when rendering menus.

---

### Post by vinmar on 2007-10-18
Yup, same here, also with two screens. Would like to hear if anyone has fixed this!

---

### Post by Nicksha on 2007-10-19
Same here. Dual screen and everything. It works ok if the second screen is turned off (in my case it's when I don't connect the tv before login). Also, the second screen has no window decorations. Don't know if that's your case too, maybe it's a clue...

Before Gutsy, compiz and tv-out didn't work together at all, so there is great improvement there. I could live with the delay, if it was on the second screen.

---

### Post by vinmar on 2007-10-19
I have window decorations on the second screen, so that's probably got nothing to do with it.

I haven't actually checked if the 2nd screen is responsive as it's not usually even turned on (always connected though, so that the screen is created).

I'll have a look later to see what differences there are between the two screens in xorg.conf.

---

### Post by albesan on 2007-10-19
hello team,

I haven't that problem anymore unfortunately I can't provide a solution because since I first posted the issue here I've gone through some mayor system changes and what I'm running now it is quite different. Also I'm no longer using a dual screen set up.

I think vinmar is on the right track, look in xorg.conf and maybe see if defining the right refreshing rates for each screen helps.

good luck.

a.

---

### Post by Nicksha on 2007-10-19
There is a bug filed about this: [#149764]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764"), and [_this_]("http://ubuntuforums.org/showthread.php?t=536045&highlight=compiz+slow+menus&page=2") topic has some good tips, especially the one about disabling compiz on second screen.

---

### Post by vinmar on 2007-10-20
I couldn't see any differences in xorg.conf.

When I unplugged the second screen and rebooted the first screen became usable.

The script from Nicksha's [link]("http://ubuntuforums.org/showthread.php?t=536045&highlight=compiz+slow+menus&page=2") (see post #14) worked for me, but things went a bit unstable so I'm back to 2D for now.

---

### Post by joeri_83 on 2007-10-20
> **Nicksha said:**
> There is a bug filed about this: [#149764]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/149764"), and [_this_]("http://ubuntuforums.org/showthread.php?t=536045&highlight=compiz+slow+menus&page=2") topic has some good tips, especially the one about disabling compiz on second screen.

I tried that solution and it fixed the problem on the primary screen, but now my TV screen has no window decoration, and I can't even move windows around anymore. Any other knows fixed?

---

### Post by Nicksha on 2007-10-20
Apparently, Metacity hasn't taken over window managing on your TV. I think you should first disable desktop effects (set visual effects to 'none') and then run the script.

---

### Post by joeri_83 on 2007-10-20
Thanks! That did the trick.

---

### Post by bitmand on 2008-02-09
Post in wrong thread! Moved - sorry.

---

