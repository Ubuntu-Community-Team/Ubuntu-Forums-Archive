---
title: "Full screen games (say, ET) on a laptop"
date: 2006-03-11
forum: Gaming &amp; Leisure
---

### Post by pdobrev on 2006-03-11
Hello!
I have a DELL laptop running Ubuntu Dapper and an i810 Intel video card. I've got the following problem - when I want to play a game in a resolution different from the native in full screen, the game screen shrinks to the given resolution without actually changing the resolution resulting in a small window and the remaining part of the screen is black. That's, for example, with Enemy Territory or Starcraft via Wine. 

Is there a solution to this problem or I'll just have to live with it/

---

### Post by dpaint4 on 2006-03-11
I have the exact opposite problem. I'm so sick of all my games warping to fit the 'full size' of my widescreen monitor, but many of them have no option to run in a 4x3 mode with black bars on the sides, which to my mind would be much better because then the image would be as the designers intended.

---

### Post by ZylGadis on 2006-03-12
Zdrasti Dobrev,
I believe your problem is related to your xorg.conf. Take a look at it and see what the permitted resolutions are. My guess is that ET wants to run in a specific resolution, but xorg won't switch to that, so ET does its best to still obey your desired format, resulting in what you see.
I have a similar "accidental feature" here with ET - I have an nvidia dual monitor display, at 2560x1024. As ET does not support that resolution, I have left it at 1280x1024, resulting in its occupying my left monitor full-screen, leaving the right one blank. Needless to say, 2560x1024 is the only allowed resolution in my xorg.conf.
Write back if you need my conf file. I don't think it will help you much, because it is customized for nvidia, but you never know.
Alex

---

### Post by pdobrev on 2006-03-12
Hi!
Alas, the desired resolution is actually present in my xorg.conf file, but I think the problem is that X can't to switch to ANY resolution other than my native laptop's. For example, if I try to run X in 800x600, it would still run in 1024x768. Weird.

---

