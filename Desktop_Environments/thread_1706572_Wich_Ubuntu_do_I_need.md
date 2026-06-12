---
title: "Wich Ubuntu do I need?"
date: 2011-03-14
forum: Desktop Environments
---

### Post by Rich3077 on 2011-03-14
I am currently running 32 bit 10.10 and was going to upgrade anyway to 64 bit. During my trial run of 10.10 I discovered some sound issues due to no dev/dsp ( I dunno, just a newb ) 

This is not my post or software.. something I found on Goolgle

"I recently installed a program called SBaGen which uses device /dev/dsp to output audio. However, the OSS (Open Sound System) device is not available anymore in Lucid and Maverick (maybe it doesn’t work with older versions, but I’m not sure), not even with OSS emulation with alsa. The snd-pcm-oss module does not load even when oss-compat and alsa-oss have been installed. It is seen to be blacklisted in /etc/modprobe.d/alsa-base.conf."

I have been unable to get quake 3 running due to this same issue. 

So how many versions do I need to go back to have a dev/dsp directory??
I would need 64 bit. 

Thanks
Rich

---

### Post by highspider on 2011-03-14
The world hasn't caught up to 64bit in all things. (both winblows and Linux).  Its still best to run a 32 bit. 
The issues is mostly with device drivers since they all 32 bit drivers at one time and lots have made to 64 bit but not all of them.  So when bust out the old joy stick its junk because there is no 64 driver for it.

Basicly a driver for 32 will not work on 64 bit system 

Unless you run a sever with like lots ram aka more the 20g of ram Your best with 32 bit.


Q: did you install SBaGen or Are having sound issues?  I know its not you post But I Really didn't get it ? discovered some sound issues due to no dev/dsp? and was 10.10 the 64 bit edition?

---

### Post by 3Miro on 2011-03-14
If you are having issues with the sound under 32-bit, you will have the same issues under 64-bit, on the other hand all 32-bit open source drivers have been recompiled for 64-bit so there is no reason for 64-bit to be any worse. I have been using 64-bit exclusively since 8.10 and I have had no trouble with it (with the exception of one printer driver).

---

### Post by Copper Bezel on 2011-03-14
I think he's primarily asking about versions. Like, going back to Karmic, etc.

---

### Post by Rich3077 on 2011-03-14
> **Copper Bezel said:**
> I think he's primarily asking about versions. Like, going back to Karmic, etc.

Thats correct. Just like I wouldnt update to Windows 7 if it didnt support my games, same goes to linux. I can run an older version just fine. Not sure about changing distros... I tried Suse once and didnt like it.

---

### Post by highspider on 2011-03-14
I think this might help
[http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/)
[https://help.ubuntu.com/](https://help.ubuntu.com/)

Ever version of Linux has its own hardware compatibility list. So first find out what hard ware you have, then check the net for a "hardware compatibility list" for that flavor Linux.

---

