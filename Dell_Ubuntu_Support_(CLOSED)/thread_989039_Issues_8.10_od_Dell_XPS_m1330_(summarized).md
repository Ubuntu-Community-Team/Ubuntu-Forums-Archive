---
title: "Issues 8.10 od Dell XPS m1330 (summarized)"
date: 2008-11-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by biocorp on 2008-11-21
Hi, there are issues, that i encoutered on dell xps. Any other major issue? I dont want be suprised as last sunday when i wanted to use skype.

I had preinstalled 8.04 and did update to 8.10.

**1. webcam-cheese **
[https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/290506](https://bugs.launchpad.net/ubuntu/+source/cheese/+bug/290506)
*solution:* [http://ubuntuforums.org/showpost.php?p=6220547&postcount=7](http://ubuntuforums.org/showpost.php?p=6220547&postcount=7)

**2. skype - integrated mic too low**
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/275998](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/275998)
*some workarounds: *in [ http://ubuntuforums.org/showthread.php?t=956565]( http://ubuntuforums.org/showthread.php?t=956565) 

**3. pand utils missing after upgrade(bluetooth)**
[https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/284073](https://bugs.launchpad.net/ubuntu/+source/bluez-utils/+bug/284073) 

**4. brightness problem - FN-up/down**
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226981](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226981)
*no workaround available, blacklisting video is causing problems in intrepid*

**5. vmware keys mapping - up, down ....**
[https://bugs.launchpad.net/ubuntu/intrepid/+bug/289098](https://bugs.launchpad.net/ubuntu/intrepid/+bug/289098)
*Solution:*[http://communities.vmware.com/message/1091296;jsessionid=922722AF7686C37F83F8AE7F85F04593#1091296](http://communities.vmware.com/message/1091296;jsessionid=922722AF7686C37F83F8AE7F85F04593#1091296)

**6. dosbox keys mapping - up, down ....**
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287894](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/287894)
[http://ubuntuforums.org/showthread.php?p=5963381](http://ubuntuforums.org/showthread.php?p=5963381)

+
**Fan Speed problem**
**Wireless driver do Kernel Panic**
**Fingerprint Sensor broken**
*full post about these 3 problems down here in this thread (thanks to pavelp): *[http://ubuntuforums.org/showpost.php?p=6241544&postcount=5](http://ubuntuforums.org/showpost.php?p=6241544&postcount=5)

---

### Post by blierp on 2008-11-21
thanks for this list!

You know, deep down inside i'm a bit happy with things not working in this release. It had me searching the internet for possible solutions again like in the `old days` when after a linux install you had to search and fiddle for weeks to get all your hardware working ;)

---

### Post by Technoviking on 2008-11-21
Thanks for the list.

---

### Post by PsychedelicReaction on 2008-11-23
very good post. did anybody found out a way to make multimedia keys work? (at least the audio player controllers, volume controllers work fine)

---

### Post by pavelp on 2008-11-24
Ok i have couple more

[LIST=1]
[*]Fan Speed problem - solution: upgrade to latest BIOS ([http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate))
[*]Wireless driver do Kernel Panic - solution: install latest updates
[*]Fingerprint Sensor broken - solution: install workaround ([https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/256429](https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/256429))
[/LIST]

---

### Post by Technoviking on 2008-11-26
> **biocorp said:**
> 

**4. brightness problem - FN-up/down**
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226981](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/226981)
*workaround: *[https://bugs.launchpad.net/dell/+bug/226981/comments/3](https://bugs.launchpad.net/dell/+bug/226981/comments/3)


This fix does not work in Ubuntu 8.10 and will cause other problems (locks keyboard, etc...).

---

### Post by biocorp on 2008-11-26
> **Technoviking said:**
> This fix does not work in Ubuntu 8.10 and will cause other problems (locks keyboard, etc...).

thanks.. updated my post. 

Is ubuntu 8.10 realy released? It's almost like some pre-beta version...
So far is for me biggest issue is sound recording in skype and brightness problem.

---

### Post by Technoviking on 2008-11-26
This fix works in Intrepid for me.
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/External_Microphone_Capture_Volume_Low](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/External_Microphone_Capture_Volume_Low)

---

### Post by newcolour78 on 2008-12-27
Hey everybody, the post was great. May I add that the volume from the speakers is low. I tried with alsamixer and everything is maxed, but it does not really seem as loud as it should be.

Anybody has any suggestion?

Thanks.

---

### Post by rosj04 on 2008-12-28
> **pavelp said:**
> Ok i have couple more

[LIST=1]
[*]Fan Speed problem - solution: upgrade to latest BIOS ([http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate))
[*]Wireless driver do Kernel Panic - solution: install latest updates
[*]Fingerprint Sensor broken - solution: install workaround ([https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/256429](https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/256429))
[/LIST]

I have the latest bios version (A14) and I'm still having major fan issues in intrepid. No matter how hot my computer gets the fan only kicks in randomly and only for half a minute or so. Making it impossible to use the computer.

---

### Post by jacrider on 2009-01-04
> **pavelp said:**
> Ok i have couple more

[LIST=1]
[*]Fan Speed problem - solution: upgrade to latest BIOS ([http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate))
[*]Wireless driver do Kernel Panic - solution: install latest updates
[*]Fingerprint Sensor broken - solution: install workaround ([https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/256429](https://bugs.launchpad.net/ubuntu/+source/thinkfinger/+bug/256429))
[/LIST]

My son's M1330 with 8.10 is frequently locking up or crashing.  The scroll-lock and caps-lock indicators are flashing and the computer becomes unresponsive.  I think I have installed the latest wireless drivers, but can anyone confirm how to do this?

Many thanks.

---

### Post by beezlebozo on 2009-01-21
> **jacrider said:**
> My son's M1330 with 8.10 is frequently locking up or crashing.  The scroll-lock and caps-lock indicators are flashing and the computer becomes unresponsive.  I think I have installed the latest wireless drivers, but can anyone confirm how to do this?

Many thanks.

I have the same exact problem on my XPS M1330.  Haven't found the cause yet.

---

### Post by beezlebozo on 2009-01-22
Ubuntu seems to crash or freeze when the pc is idle for very long.  I have tried booting with and without the NVIDIA proprietary drivers and with and without visual effects.  I don't seem to have any of the other problems that the others have posted prior.  I have also tried cpufreq-selector -g performance and cpufreq-selector -g ondemand, that didn't seem to help either.

---

### Post by beezlebozo on 2009-01-22
Solved:  Installed 8.0.4..........no problems, so far.

---

### Post by Technoviking on 2009-01-22
I have had better luck with some of these issues (webcam, sound) by switching to 64amd Ubuntu 8.10.

---

### Post by gsbnd1 on 2009-01-23
Man... you are a genius. Thanks very much

---

