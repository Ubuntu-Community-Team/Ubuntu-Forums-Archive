---
title: "DVD play problems"
date: 2005-11-22
forum: Desktop Environments
---

### Post by djheadley on 2005-11-22
I am running Breezy dual boot with WinME on a 433mhz Celeron with 256mb ram (8mb dedicated to video) with a cdrw (master)and dvd (slave)drives.  When I try to play a dvd (commercial) I get a vertical pink bar in the middle of the playback window and 2 or 3 vertical "windows" of the dvd title screen.  I can play dvds in WinME but they are a bit choppy.  I've installed all the codecs and am using Totem-xine.  DMA for the DVD drive is on.  Now what?

---

### Post by matthewv on 2005-11-22
Do you have libdvdcss2 installed??

---

### Post by djheadley on 2005-11-22
Yes.  At first I thought the problem was due to not enough memory but if that were true, why would I be able to play dvds in WinME?

---

### Post by dcstar on 2005-11-23
[QUOTE=djheadley]I am running Breezy dual boot with WinME on a 433mhz Celeron with 256mb ram (8mb dedicated to video) with a cdrw (master)and dvd (slave)drives.  When I try to play a dvd (commercial) I get a vertical pink bar in the middle of the playback window and 2 or 3 vertical "windows" of the dvd title screen.  I can play dvds in WinME but they are a bit choppy.  I've installed all the codecs and am using Totem-xine.  DMA for the DVD drive is on.  Now what?[/QUOTE]
What Linux kernel (linux-image file) are you using, a 386 or 686 one?

---

### Post by djheadley on 2005-11-23
I'm using the 386 kernel.  What else can I tell you that might help?

Thanks

---

### Post by djheadley on 2005-11-25
OK, I tried totem and plain xine.  I'm still getting the pink(?) vertical bar and multiple vertical images in the playback window.  I have libdvdcss2 installed and am using the 386 kernel.  I know I'm probably short on power (433mhz Celeron) and memory (256mb with 8mb for agp video) but I CAN play these dvds in WinME.  Any suggestions????

---

### Post by Mr. Electric Wizard on 2005-11-28
I'm having the same issues.
Playback is pretty jerky with both Totem and Xine-UI.
Anybody got a fix for DVD playback?  (using the 386 kernel). 
I am trying to play DVD's on a brand new AMD Sempron 2800 HP Laptop.  I know I have the umph to play DVD's...:confused:

---

### Post by alank on 2005-12-03
I had problems with totem crashing and xine only working with XShm video output option. Xine would just have a blue screen with auto video output or xv video output. Xine would show a picture with XShm video output but would be dropping so many frames it was practically useless (on 2.2 G Athlon) . 

The solution for both players was to edit /etc/X11/sorg.conf and change the default colordepth from 24 bit to 16 bit.

---

### Post by djheadley on 2005-12-03
Thanks, I'll give it a try and let you know.:D

---

### Post by mephisto786 on 2005-12-03
It seems each release of ubuntu has one bug that drives people crazy:) ...on Hoary it was a crashing home with a konqueror workaround. Now, with gnome and kde installed, totem is a total flop insisting another app is using the video output, along with constant kaffeine crashes, if it works at all on dvds.  Whats with this gstreamer nonsense?  Kaffeine is usually my old standby for playing anything on disc.
  Workaround?  Install ogle, which aint picky and usually doesnt result in choppy video. Bugs are Gods why of saying youre using bleeding edge software, heh.  
  Will try mplayer today and see what happens. It could be worse. I could be using Fedora Core without sound....ack!
  Anyone find a good errata or workaround howto on fixing up kaffeine?  When i try uninstalling totem or kaffeine synaptic threatens to remove either kubuntu or ubuntu desktop, which sounds ominous....

---

### Post by meborc on 2005-12-03
sorry to hear that you guys have problems... if you have installed all the codecs and enabled DMA then i really don't know how to tackle this problem... but i do know that you can play DVD's with a very slow machine with eccelent quality... so it is not the comp, but the soft that is rotten... the color depht solution should help a bit though...

---

### Post by djheadley on 2005-12-03
I changed the color depth, checked DMA and I still get the pink bar and odd video when using totem.  Now what?

---

### Post by _4ace on 2005-12-03
have you tried the exellent OGLE dvd-player, available through synaptic?

---

### Post by DrBair on 2005-12-03
Make sure you are using the correct video drivers! 

Doing the DVD playback by software will lag, especially on older machines.  The nv driver for nvidias doesn't count either, last I checked it didn't support hardware overlays.

---

### Post by djheadley on 2005-12-03
Tried OKLE, no luck.  As for video drivers, I have SiS 530/620 PCI/AGP built in to the motherboard. The CPU is Intel Celeron - Mendicino.  This is getting frustrating :(   but I'm not going to give up!

---

### Post by Sp@z on 2005-12-07
I am having issues with DVD playback as well. Totem say Could not read from resources, and are you trying to play an encrypted dvd without libdvdss? HA, no I am not! It is installed, mplayer freezes and locks up my system. Ogle and okle plays past the government warnings and just crashes. Funny I installed Linux because I hate windows 98 SE and WINXP doesn't run well on my old trusty machine! Stupid DVD's LOL. I love linux but so far it isn't doing what I want (not expected, since I had no expectatons) Hate to go back to win 98 se. :( Btw I need help too and didn't want to start a new thread! Thanx!

---

### Post by djheadley on 2005-12-26
OK, did a re-install (due to other problems), created a swap partition, upgraded to 686 kernel, re-installed all codecs & libdidcss2, etc, still have the same "pink" bar.  I couldn't get ogle to work either.  Any suggestions?  Thanks for all the help.


djheadley

---

### Post by griz on 2005-12-26
Ok, I was having trouble playing DVDs with Totem, MPlayer and Xine.  Just not recognising the DVD drive.  Installed OGLE and it works fine.  Thanks for the tip.  

Griz.

---

### Post by djheadley on 2005-12-27
Well, I'm glad yours is going.  Mine needs a new video card.  Anyone know where I can get a ised pci card?

djheadley

---

### Post by feathers on 2005-12-28
Install kaffeine-xine and then choose kaffeine as the player engine. That way you avoid gstreamer which has never worked for me either.

---

### Post by djheadley on 2005-12-28
I uninstalled gstreamer a while ago and that didn't work.  The video built in video card only has 8mb shared memory, I don't think it's enough to play dvds.  It's an old SiS and although I've gotten some drivers for it, I didn't get them to work - caused more trouble.  Thanks.

djheadley

---

