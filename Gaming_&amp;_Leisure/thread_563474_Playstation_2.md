---
title: "Playstation 2"
date: 2007-09-30
forum: Gaming &amp; Leisure
---

### Post by ep3w on 2007-09-30
This doesn't have to directly do with linux, so if this needs to be moved then do so, i just thought this was a good place to ask...I just got a hauppauge wintv-pvr-usb2 tv tuner and when testing under windows, i tried to hook my playstaion2 up to it but there was too much lag to play anything, otherwise works great.  Is there any kind of converter so I can just hook it directly up to my monitor?  My monitor only has vga and dvi inputs, the playstation2 is composite.  Or any ideas on how to limit the lag?  I have not tried it in linux yet...I am pretty new to it still and haven't tried yet...

---

### Post by gwoodard on 2007-10-07
Did you try the "S-video" plug in?

If not you need to get special adapter with Composite+S-Video...try ebay

---

### Post by acoustibop on 2007-10-07
I do the same with a Playstation into one of the composite inputs of a Hauppauge Impact VCB card, ep3w, and it works perfectly.  I'm using TVTime for the software player.

Are you trying to use the RF (aerial) input for your card?  Try s-video or composite as gwoodard suggests.

---

### Post by ep3w on 2007-10-07
I will have to get an adapter and try the s-video input.  I was using the composite before. Hopefully that helps, thanks for the idea!

---

### Post by acoustibop on 2007-10-08
Ah, I see you were talking about results in Windows.  IIRC some of the Windows drivers do introduce lag - I guess they're mainly intended for watching TV rather than playing games, so the lag isn't as much of a consideration.

As I said, in Linux I use TVTime, which is very easy to install (in the repositories) and I get no delay at all.  I've never tried TVTime on a tuner card, but it works excellently on my video-only  card - I'm on cable, so a tuner would be a bit superfluous for me.  Good picture quality, too - better than Hauppauge's WinTV

IIRC the lag in Windows is caused by your TV application assuming you'll want to record what you're watching and buffering it.  It may be possible to turn this off, but it depends on the application.

S-video is unlikely to fix the lag problem; it should get you a slightly better quality picture, though.

---

### Post by ep3w on 2007-10-08
I have tried everything I could find in windows, including multiple programs, so I guess my next best bet is to try it in ubuntu then.  If I have read correctly, I need to build/configure my own kernel in order to enable a few options to get my card to work right (thanks to this forum I have found easy step by step instructions how to do it), but since gusty is coming out in a few days I was just going to wait for that to be released then do it.  I will check out tvtime though, thanks for the suggestion!

---

### Post by acoustibop on 2007-10-08
TVTime is only a viewer; it doesn't have capping capabilities.  However, it's easy to install (as I said, in the repositories) and configuration is also simple.  You do need to have overlay set appropriately for your videocard driver, eg for the fglrx ATI driver you need to do

sudo aticonfig --overlay-type=Xv

AFAIK default (free) drivers should be set already.

---

### Post by ep3w on 2007-10-08
Thanks alot! I will give it a shot once I get it up and running.

---

