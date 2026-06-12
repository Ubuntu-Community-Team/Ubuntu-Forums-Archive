---
title: "PS3 firmware regression"
date: 2010-05-08
forum: Gaming &amp; Leisure
---

### Post by kennethadammiller on 2010-05-08
Ok, so I know this has probably been overkilled, and that I'm not talking on an official ps3 forum, and that everyone else will just tell me there's no way to do what I want to do.

But this is really the place where I've received the most help. It's really the only place that I want to even rely on, so here goes.

I had to software update my 60gb version ps3 because it didn't want to play gta4. So i went about doing it with a usb because i don't have wifi, and there's only one ethernet in the house, so on so forth, i hate where i live because I'm a caveman type thing.

Anyway, I go about doing it, and I had it all set up just fine. I let it update and left the room. When I came back, the version 3.30 update had messed up my ps3. I don't know whether it was the software, or if my neise pulled the jumpdrive out prematurely, but it only shows black and white now.

I was feeling impatient so I tried downloading the file again to the computer, only to open the file with gvim. After I opened the file with vim, I found the version number kept at the very top portion of the file. I changed it to 3.40, so that when the ps3 read the file, it would think it was newer and then it would just update once again, and hopefully a new update would fix it.

The ps3 simply told me that there was no acceptable updates on the media or something like that. I'm thinking that the ps3 read the file, and compared it to a checksum, which invalidated it. Does anyone think it would be possible to open such a file, identify the checksum and it's type, and then replace such a checksum?

---

### Post by kiddykoff on 2010-05-09
I think you're going to need to talk to Sony.

I don't think there's any way to fake a firmware update. If there is let me know, I'm still on 3.21 (holding on to my linux partition)

There was a demonstration for a custom firmware from geohot a while ago, but he hasn't released it and he's still fiddling around with his ipad.

---

### Post by donkyhotay on 2010-05-12
I doubt simply 'changing the number' will work since it probably uses checksums, certificates, or something similar to prevent invalid updates. On a side note, according to the [eff](http://www.eff.org/deeplinks/2010/05/ps3-owners-sue-sony-over-removal-features) there is a class action lawsuit against sony over this firmware "upgrade".

---

### Post by James Paige on 2010-05-12
I don't have a PS3, so I have not been able to test this out myself, but apparently you can install custom firmware. There is a fairly recent page that talks about it here:

[http://www.ps3-hacks.com/2010/04/07/otheros-reintroduced-in-ps3-custom-firmware-3-21oo/](http://www.ps3-hacks.com/2010/04/07/otheros-reintroduced-in-ps3-custom-firmware-3-21oo/)

---

### Post by kiddykoff on 2010-05-14
> **James Paige said:**
> I don't have a PS3, so I have not been able to test this out myself, but apparently you can install custom firmware. There is a fairly recent page that talks about it here:

[http://www.ps3-hacks.com/2010/04/07/otheros-reintroduced-in-ps3-custom-firmware-3-21oo/](http://www.ps3-hacks.com/2010/04/07/otheros-reintroduced-in-ps3-custom-firmware-3-21oo/)

I'm sorry to say, but as of right now that was a demonstration of what geohot was working on. He never released the CFW. 

It's not the first time that he has come up with something that has resulted in nothing. I take that back, he is the reason otherOS was taken away.

---

