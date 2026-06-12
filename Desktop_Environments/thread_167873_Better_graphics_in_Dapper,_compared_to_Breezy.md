---
title: "Better graphics in Dapper, compared to Breezy?"
date: 2006-04-29
forum: Desktop Environments
---

### Post by kneewobbler_1 on 2006-04-29
Sorry beforehand if this is the wrong forum for my "problem". Let me describe the issue here. I have an amd64 desktop, with a nvidia GeForce FX5200. I've been running Breezy on it (x86 on purpose, not amd64) lately, Hoary before that. Standard kernel, no tweaking here. Very satisfied, 99% works (bluetooth, scanner, the works). My monitor is a 19 inch CRT Gateway VX900, that I set to 1600x1200 at 75Hz. I have a triple boot with FC5 and Windoze XP.
This morning I booted the Dapper beta2 live x86 cd. Fast boot, I like the hibernation stuff, all roses. 
I noticed immediately, the desktop graphics quality in Dapper live is slightly "better". All other things being equal, the fonts are "sharper", in short, easier on the eye. I choose 1600x1200, 75Hz, same 10 pt Sans fonts, same nvidia modules are loaded by default (lsmod | grep nvidia yields nvidia, i2c_core and agpart, just like Breezy). Different Gnome though, 2.12 (Breezy) vs 2.14 (Dapper beta2).
The proof of the pudding is in the eating, and for me the pudding is Firefox. On Breezy, my firefox version is 1.5.0.2 (downloaded from mozilla.org, Breezy Firefox default is at 1.0.8 now).
A lot of websites on Dapper-live with Firefox 1.5.0.1 are looking sharp now, no longer blurred, or slightly off-base (In Breezy I always have to 'Ctrl+'+' in firefox to arrive at readability, which turns out to be just a little too large). 

My question is: have any of you who ran the Dapper live cd on a system with a crt monitor noticed improved graphics? If so, is it because of some "generic way" the live cd kernel treats the graphics card? Is it the newer, better kernel?

My second question: if, for some reason, there is an improved graphics quality that comes with Dapper live, will that still be there after a Dapper install? Or will some 'smart' graphics recognition routine spoil it? I don't want to install a beta over a "production system", and I don't have a removable hard disk bracket, so I can't tell right now. 

For comparison, you might want to go to [http://www.ad.nl](http://www.ad.nl) (dutch newspaper), and see for yourself. On Breezy, watching this site in firefox at 1600x1200 hurts my eyes, on Dapper live, it looks perfect, excellent ergonomics). 

Incidentally, graphics on my Fedora Core 5 partitions (and on WinXP) is on par with Breezy, so Dapper is also an improvement over that.

---

### Post by hw-tph on 2006-04-30
To me it sounds like you simply have different font rendering configurations. You can tailor it to your liking using the xml config file ~/.fonts.conf. Read fonts.conf(5) for more information.


Håkan

---

### Post by Sendervictorius on 2006-04-30
I have breezy, and a VX 900 monitor, and your dutch newspaper link looks great to me. 

But I don't run my monitor at 1600 x 1200 - the 75Hz flicker drives me nuts. I have 1400 x 1050 at 85Hz.

---

### Post by _linux_ on 2006-04-30
I don't know what's wrong, but Dapper does look nicer and "sharper" than Breezy. It could be the driver for your graphics or the font rendering, though.

---

