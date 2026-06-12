---
title: "video corrupt on install"
date: 2010-06-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pishta on 2010-06-18
Inspiron 8000 running the weird 1050X1400 UXGA monitor, I cant get anything but the failsafe graphics mode to work and it wont even let me reconfigure the video (as if I even knew how) Im running the ATI M4 (R128 driver in Puppy and it works great over there) video that is generic to this model and I get a folded/wrap around/corrupt video on install and normal boot. Generic is painfully slow, like 4 fps when I drag stuff around. Can someone tell me where to put the "drivers" (winspeak) in the file structure or what text I need to change in a config file? I think X would work, but I think Ubuntu 10 uses KDE? describe like you are talking to a 4 year old as I have no previous experience with Linux. Thanks alot!

---

### Post by candtalan on 2010-07-14
I also have a  problem. The  Inspiron 8000 laptop is old:  2001 vintage, but has a beautiful display, large and bright, and is a nice quality machine. Ubuntu 8.04 LTS works fine (am using it now) however, I have just tried Ubuntu 10.04 LTS live CD and only get a strange display of a creeping brightness, as if the video is not being controlled in any way at all.

lspci used in 8.04 provides:
VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)

I am also mystified that the 10.04 live CD does not have 'safe graphics' (F4) available. That used to get me out of most trouble in previous versions on various machines.

From the  previous message
'I cant get anything but the failsafe graphics mode to work'
the implication is that an install is actually possible, perhaps via online upgrades or the alt version.
I certainly cannot begin the install from a desktop version CD because there is no useful display at all.

Comments would be much appreciated, to help keep this rather nice machine out of landfill.

tia

---

### Post by candtalan on 2010-07-14
I found that when booting from the 10.04 live cd I could use F6 and choose 
no modeset
and then the display would actually work! 

It was, however, about 3/4 size. Fn and F7 would then enlarge the  display to fill the screen.
Still using the live cd I could accept the restricted video driver - nvidia 96. Of course, it would only activate after a restart and being a live cd I left it there.

I proceeded from this live desktop session to install, and completed the install. (this laptop has 370MB ram).

However the bad news is that after the install which went well, I restarted, and the display again became non functional with creeping white as it had with the live cd originally before I had used the 
F6  no modeset
option.

So, the big question is now:
how can I edit this installation to get the 
no modeset
functionality?

It is a dual boot with a working 8.04 so I have access to the 10.04 partition fairly easily.

Comments appreciated.

---

### Post by pishta on 2010-07-21
I have found a workaround for this, possibly. Use the function F7 key. I
> believe that says mode or something. If you toggle it, the display  sharpens
> but gets small, hit it again and the display is once again  stretched full
> screen, and is no longer corrupt but I have yet to find an answer  to the
> screen resolution settings. All I see is 800X600, yet PUPPY 5.0x  gets
> 1440X10xx natively, looks beautiful! I couldnt get Ubuntu 10 to  work in any
> better resolution, couldnt get puppy to boot from anything else  than a live
> CD (I think the 8000 uses a SCSI interface that Puppy doesnt like  or GRUB
> cant figure out, always gives me file not found error) so I went  back to XP.
> Boots faster, everything works (after 3 SP updates) and I can  actually get
> my wireless to work. Good luck. I really like puppy, I have it on a
> flashdrive and use it on my work laptop during lunch. I even used  it on a
> few customer PC's that had corrupt windows OS's!

---

