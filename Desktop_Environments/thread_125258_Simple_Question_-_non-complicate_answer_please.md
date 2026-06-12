---
title: "Simple Question - non-complicate answer please"
date: 2006-02-03
forum: Desktop Environments
---

### Post by kelloggsx on 2006-02-03
first... ( english not first language, so easy on me )

Totally New to the whole linux world ( ubuntu ).. Have spend the last 4 days playing around with this.  Most say! that sucks that i been missing on this for so long.

This is the problem i have and i would love find a simple solutions for this.

*  own 1000's of wma ( media procteted, or however M$ call them ) files that i have on an external hard drive.   I manage to connect to it in ubuntu.  no problem there.

I have tried everything under the sun to get to play this files on ubuntu, so far nothing works.   I have follow every instruction, every link, every single newsgroup suggestion and so far only thing i got is to reinstall the os every time this thing crash and burn.

The last suggestion was to install "automatix" and that took a while running a bunch of stuff on the terminal.   after it was done - me.. coming from the world of windows figure that i should "restart" my pc.  Right!  

lets just say.. i am on installation # 24 and still not getting anywhere with my protected files.

I really really REALLY WANT TO MOVE ON FROM M$$$$SOFT to a better world, a place where i dont have to pay for every thing i want to do on my pc.. and the constact updates and BS from those people, BUT (major BUT)  i dont think i could part away from my WMA files.

Help!

thanks in advance.
(and hope the posted have u LOL )

---

### Post by psilo357 on 2006-02-03
i used automatix to install Beep Media Player and the extensions for WMA....i think it is the #24, only install this if you live outside of US thing, but it will let you play those files.

peace

---

### Post by kelloggsx on 2006-02-03
what happen if I am in the USA?

can i still install the automatix?  what would happen if i cheat the installation into telling the pc that i am in like... CANADA or some other "english speaking" country?

this whole wma is so frustrating.. :-(

help

---

### Post by syklitengutt on 2006-02-03
nothing can happen but its not legal according US laws!

---

### Post by kelloggsx on 2006-02-03
but i have already paid-for those wma files.

all i want is to convert them to mp3 so i could leave the world of MS$$$$

:-/

---

### Post by syklitengutt on 2006-02-03
convert them to ogg...
Just install automatix and instal mp3 support and everything you need....
Automatix rox!

---

### Post by kelloggsx on 2006-02-03
:-)

thanks syklitengutt for the prompt reply.

now... the million dollar question(s)

1) link to automatix? and i read that there like 5 different version
2) if it dosent work... should i just once again ( actually 15 times ) reinstall ubuntu and tell the setting that i am in good old-CANADA OR SOME Caribbean Island.. maybe Jamaica :)  and then reinstall automatix?

thanks

ps. Jamaica would be nice


shooottttt i now i cant fine the so call "TERMINAL WINDOW" ICON

---

### Post by jannol on 2006-02-03
For some reason automatix didn't run gst-register for me so I just did it manually.

open a terminal window and run

gst-register-0.8

Maybe this helps

---

### Post by inthegroove on 2006-03-01
thanks for helping me see it is gst-register-0.8 I have entered
gst-register 20 times and was feeling really frustrated.
I downloaded gstreamer 10.3 
Would gst-register-0.10.3 be what I should enter?

---

### Post by RAOF on 2006-03-01
Those "protected WMA" files have DRM - that's Digital Rights Management.  The upshot is - the audio is encrypted, and only supported software (with the right key) can play them.  

Before you can play them, you'll need to decrypt them - strip the DRM from them.  It is illegal to do this in a couple of countries - it **certainly** is in the US.  Additionally, I'm not sure that the DRM has actually been broken yet, so it may be actually impossible to play/convert those WMA under linux.

The simple solution would be to convert them under Windows to ogg (preferably) or mp3.  If the DRM allows you to do that, which it probably won't.  You could try burning them as audio cds and then importing those audio cds.  Once again, if the DRM allows you to burn them as an audio cd.  Plus, this will take a long time.

In short, "protected WMA"s and DRM are incredibly annoying, and prevent you from legally playing songs that you've bought on anything but Windows.

---

### Post by powder on 2006-03-01
You can try this WMA plugin for Beep Media Player if you have BMP installed.  I haven't tried it.

[http://mirror2.ubuntulinux.nl/pool/extras/bmp-wma-0.1.1_0.1.1-1_i386.deb](http://mirror2.ubuntulinux.nl/pool/extras/bmp-wma-0.1.1_0.1.1-1_i386.deb)

sudo dpkg -i bmp-wma-0.1.1_0.1.1-1_i386.deb

---

### Post by Scunizi on 2006-05-07
You could also try loading the Windows version of Audacity, tell it to record from Wav, then play the files one at a time while recording.  Cumbersome, time consuming, frustrating.... but it just might work!

---

