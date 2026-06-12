---
title: "Black screen after boot with Nvida drivers and bios screen corruption."
date: 2016-05-11
forum: Desktop Environments
---

### Post by dethorpe on 2016-05-11
Hi, hope someone can help.

I've a old Rock x770 laptop (clevo M57RU) with nvidia GTX7950go graphics card, intel core2duo 2.4Ghz.

I've been running xubunutu 14:04 with the Nvidia 304 drivers since it came out, with no issues. Recently I I suddenly started seeing vertical  rows of white dots on the BIOS screen and it would boot to a black screen. Going to tty terminal and looking at the X logs I see Xserver is crashing with "(EE) Caught signal 11 (Segmentation fault). Server aborting" .

I can get it to work using nomodeset in grub boot line, and using the Nouveau drivers, but only at a low res 1280 x 1024 (native res is 1920x1200), as soon as I switch to nvidia drivers from the Additional Drivers app its back to black screen, even after a fresh install. If I take nomodeset off with Nouveau drivers it gets to logon screen, but heavily corrupted and freezes.

Have tried lots of suggestions for un-install and re-install of various  drivers and X packages Tried xrandr to switch modes, but that has no  effect when in the low res/nouveau mode, just a brief flicker and  message "Configure crtc 0 failed".

Tried fresh re-installs of 14.04, and 16.04 to no avail, always limited to nomodeset and low res with Nouveau drivers. Its no longer used for 3d or games so would be happy with Nouveau drivers if could get the full res.

From what I&#8217;ve researched one likely possibility is that the bios screen corruption indicates that the graphics card has gone faulty and is only able to run in basic low res VGA mode.

So, any-one able to suggest anything else to try before I look to replace the graphics card? (Its a MXM module so can be done, if i can find one).  I've seen suggestions of baking the graphics card in the oven!! which I might try first when I&#8217;ve nothing left to lose- [http://www.overclockers.com/forums/showthread.php/606658-THE-OVEN-TRICK-WORKED?highlight=oven+trick](http://www.overclockers.com/forums/showthread.php/606658-THE-OVEN-TRICK-WORKED?highlight=oven+trick)

Attached ar+e:
[LIST]
[*]X server logs from when X crashes with the nvidia drivers 
[*]Dump of terminal session when trying xrandr commands 
[*]Photo of BIOS with the rows of dots 
[*]Photo of frozen login screen without nomodeset using nouveau drivers 
[/LIST]
   
Thanks in advance

   Craig
 

[ATTACH=CONFIG]268999[/ATTACH][ATTACH=CONFIG]269000[/ATTACH]
[ATTACH]268996[/ATTACH]
[ATTACH]268997[/ATTACH]
[ATTACH]268998[/ATTACH]

---

### Post by dethorpe on 2016-05-11
dmesg and syslog as well from when booting to black screen with Nvidia drivers

[ATTACH]269001[/ATTACH]

---

### Post by dethorpe on 2016-05-17
Cross posted on ask ubuntu: 

[http://askubuntu.com/questions/773867/black-screen-after-boot-with-nvida-drivers-and-bios-screen-corruption](http://askubuntu.com/questions/773867/black-screen-after-boot-with-nvida-drivers-and-bios-screen-corruption)

---

### Post by dethorpe on 2016-06-29
Just to update in case useful to anyone else. 

It turned out it was a hardware fault with the graphics card, so I tried the oven baking method described in the overclockers link and it worked!! Graphics now all A OK. 10mins at gas mark 5 did the trick

[ATTACH=CONFIG]269852[/ATTACH]

---

