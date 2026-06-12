---
title: "Ok I got XMMS installed, new problem"
date: 2005-01-04
forum: General Help
---

### Post by pmshoop on 2005-01-04
Ok, I feel kinda silly,  Synaptec is SOOOO much easier than what I was doing.  Although firefox and thunderbird were real easy to install the hard way.

I'm used to unix.  Doing things the hardway.  Thanks for the replies to my other post.

My new question/problem is this:  I can not get audio cd's to play.  It will not mount them.  Any other files mount fine (aka data discs) but not audio.  Is there a device setting I need to change?  

This holds true for my USB DVD writer as well... audio cd's not being detected/mounted.

Paul.

---

### Post by wulf on 2005-01-04
You don't need to mount audio CDs in order to play them. However, you do need to make sure you've got some volume on the right channel. Using XMMS, I put the disk in then open the location /cdrom. If you can see the progress bar moving along but get no sound, right-click on the loudspeaker icon in the panel and open the "Volume Control". On both my Ubuntu systems this gives me lots of options, one of which is volume for the CD player.

Wulf

---

### Post by pmshoop on 2005-01-04
[QUOTE=wulf]You don't need to mount audio CDs in order to play them. However, you do need to make sure you've got some volume on the right channel. Using XMMS, I put the disk in then open the location /cdrom. If you can see the progress bar moving along but get no sound, right-click on the loudspeaker icon in the panel and open the "Volume Control". On both my Ubuntu systems this gives me lots of options, one of which is volume for the CD player.

Wulf[/QUOTE]


Thank you,

Turns out I had to change my Kernel.  I had i386 but not kernel for AMD k7.  Updated that wow... sounds better than my speakers ever did under windows... seems that my enviromental surround features of my sound card finally kicked in.  God I love ubuntu.

Paul.

---

