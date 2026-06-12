---
title: "Dual Monitor 90 degres rotated vs compiz vs ATI vs Xorg"
date: 2008-04-14
forum: Desktop Effects &amp; Customization
---

### Post by RodrigoRodrigues on 2008-04-14
Hi Guys, I know there is a lot of posts talking about these things but there isn't a post with all these things working together... so let me explain my problem.

First what im trying to do....
I'm using an ATI Radeon HD2600 pro, the version made by Sapphire with 256MB
and I'm trying to use 2 monitors, they are both LCD 19" widescreen connected by DVI, one AOC 193FW and one Sansung 943BWX

The restricted driver from ATI ubuntu wanted to install didn't worked, ubuntu said it did, but it didn't, the best resolution I could use was a distorced 800x600 "wided", then I tried a lot of drivers, and even envy couldn't solve the problem... after 2 days in google I found the correct driver and it worked fine, with compiz and all these things, but i was using only the AOC....

Yesterday I got the sansung and I'm trying to config, but after playing with xorg.config I couldn't make  everything work as suposed to again.... I tried to restore a backup from the xorg file but didn't worked....

so I let ubuntu install the drivers he wanted again, it works better without it installed, using the card as generic vesa,:lolflag:
but now I have both LCDs with the same image in low resolution.

to make things even worst, all this is not enoth, I want to use the Sansung in portrait, so instead of 1440X900 it would be 900X1440. I found a topic somewhere talking about the line
Option "ROTATE" "CW"
and I'm sure this would solve this...

I hate to say this, but its so easy to do in windows, in linux my cataclysm doen't even open, i thing this icon is just decoration of the menu,:)

and dont know how to correctly edit the xorg configuration, since everything I do end in a low resolution screen ](*,)

I belive I can make the correct driver work again, I'm sure I saved it somere in the disk, can someone please help me with the rest[-o<

---

### Post by RodrigoRodrigues on 2008-04-14
Ok, so I reinstalled the driver and started to play with aticonfig....

I tried the big desktop otion but Maximizing a a windows would be caos, so I userd the dual head

so now I have a full funcional desktop and a "only mouse" desktop, I cant drag anything to this socondary desktop, and the mouse become that famous "X" from the X server...

any Ideia?

---

### Post by RodrigoRodrigues on 2008-04-18
No Reply???

I Tried the 
	Option "Rotate" "CW"

but didn't work.... i think it is only for NVidia cards

---

### Post by eviltandem on 2008-05-29
I have an nvidia card with 2 dvi-out's and 2 16x9 monitors.  I like the second one to be rotated, but I couldn't figure out a way to do it with the nvidia twinview stuff, so I switched everything to xinerama.  From what I've read it's slower, but slower is better than not working.

Unfortunately the only thing that doesn't work is all the fancy effects.  Other than that though everything behaves like I like it to.  Both monitors are on the same "desktop" so I can drag windows back and forth, but maximizing something makes it maximize on just the monitor it's on.

I keep thinking someday nvidia will come through on this and fix the twinview stuff...

My [_xorg.conf_]("http://linuxloser.blogspot.com/2008/05/dual-monitor-xorgconf-with-rotation.html")

It's not sexy but it works for me.  I think xinerama works on ati too, but I don't have a card to test that.  If you know a little about the xorg.conf file you should be able to alter this to fit your needs.

---

