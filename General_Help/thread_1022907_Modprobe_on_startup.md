---
title: "Modprobe on startup"
date: 2008-12-27
forum: General Help
---

### Post by SlalomMan on 2008-12-27
I recently tried installing ndiswrapper to improve wireless speeds, and that went awry. So I've tried going back to the default driver, which is "iwl4965." I can get it to work by going into the terminal and typing "sudo modprobe iwl4965" but I have to do this each and every time I start up. Is there some way to get modprobe to remember this driver and load it on startup, aside from putting that command in the sessions list?

Thanks.

---

### Post by albinootje on 2008-12-27
> **SlalomMan said:**
> I recently tried installing ndiswrapper to improve wireless speeds, and that went awry. So I've tried going back to the default driver, which is "iwl4965." I can get it to work by going into the terminal and typing "sudo modprobe iwl4965" but I have to do this each and every time I start up. Is there some way to get modprobe to remember this driver and load it on startup, aside from putting that command in the sessions list?


Did you remove ndiswrapper, or do you need it for something else ?

Put the kernel module name in : /etc/modules

---

### Post by bodhi.zazen on 2008-12-27
Thanks albinootje

---

### Post by SlalomMan on 2008-12-27
Alright, I forgot to remove ndiswrapper, but I did now. And putting iwl4965 in the /etc/modules should work like a charm. I've just got one more question: before I did a clean install of 8.10, ndiswrapper worked fine; but now I can't get it to work with WPA security networks; it sees the networks but won't connect. Any ideas?

---

### Post by bodhi.zazen on 2008-12-27
It could be a problem with ndiswrapper, wpa_supplicant, or network manager.

I suggest you try wicd first.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

that will replace network manager.

If that fails, try installing ndiswrapper and wpa_supplicant from source.

---

### Post by SlalomMan on 2008-12-27
Thanks! I had been considering getting wicd, but I wasn't sure how it would interface with ubuntu, and I wasn't ready to risk losing my internet.

It seems to be working like a charm, although I'm not sure if I need to set ndiswrapper as the "wpa supplicant driver" in wicd's preferences or not.

Speed seems good, though. Thanks!

---

### Post by bodhi.zazen on 2008-12-27
If it is working, don't break it !!!

I use wext rather then ndiswrapper.

---

### Post by SlalomMan on 2008-12-27
Alright, I was just confused because the "wpa driver" isn't the driver I'm using for the network, right? Just for WPA? Because that was my issue with Network Manager and ndiswrapper; wpa wouldn't work.

---

### Post by bodhi.zazen on 2008-12-27
That is the driver for WPA

I do not know the specific problem, I could never sort it out. Since it resolved when network manager is replaced I have always assumed it was a problem with network manager.

FYI , on my box, with Ubuntu 8.04 I need wicd, with 8.10 network manager is working, so again I assume it is with network manager.

---

