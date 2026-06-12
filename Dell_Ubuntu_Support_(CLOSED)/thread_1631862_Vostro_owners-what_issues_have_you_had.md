---
title: "Vostro owners-what issues have you had?"
date: 2010-11-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by wgarider on 2010-11-27
I bought a Vostro 1014 yesterday on sale.......from my reading here, seems there were some issues in Ubuntu prior to 10.10, If you have a Vostro, or specifically a 1014, what issues have you had and how did you overcome it?

I understand sound from the built-in speakers is bad....any issues with video or wifi? Is anyone running Xubuntu?

Thanks!

---

### Post by CoolJohnB on 2010-11-27
I have a Vostro 1700 running 10.04, will I will shortly upgrade, not had any serious issues with it. Your right about the sound but that can be tweaked using various equalizers, no problems with video or wifi just had to install the correct drivers which Ubuntu did for me.

I also have a Vostro 3700 running 10.10 it works great, volume is a bit low on the sound but that seems to be a general issue with Ubuntu using VLC or Audacity to play back you can increase the volume above 100% also I often play back through an amplifier.  

On the whole I would recommend Ubuntu for any Vostro it is far superior to Windows and far more intuitive, a much better OS all round.

---

### Post by ScottTiger on 2010-11-27
My Vostro 1014 with Ubuntu 8.10 worked just fine until I upgraded to 10.04. Now I have no wireless wifi or webcam. The upgrade process took several hours and must be done with a wired connection as you loose wifi part way through the process. 

Sound is as expected from a single speaker system and fine for use in a quiet office setting.

Dell provides no support.

Some steps to gets the laptops Atheros AR9285 wifi working would be appreciated. Pre-compiled driver or source anywhere?

No idea yet how to find the webcam hardware info.

---

### Post by wgarider on 2010-11-27
> **ScottTiger said:**
> My Vostro 1014 with Ubuntu 8.10 worked just fine until I upgraded to 10.04. Now I have no wireless wifi or webcam. The upgrade process took several hours and must be done with a wired connection as you loose wifi part way through the process. 

Sound is as expected from a single speaker system and fine for use in a quiet office setting.

Dell provides no support.

Some steps to gets the laptops Atheros AR9285 wifi working would be appreciated. Pre-compiled driver or source anywhere?

No idea yet how to find the webcam hardware info.

Hi - have you considered a clean install of 10.10?

---

### Post by ScottTiger on 2010-11-27
> **wgarider said:**
> Hi - have you considered a clean install of 10.10?
No as this would not have the drivers either.

---

### Post by wgarider on 2010-11-28
> **ScottTiger said:**
> No as this would not have the drivers either.

Hi - this thread seems to describe an issue with the networking - didn't know if that would be helpful to you....

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1615494](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1615494)

---

### Post by jwaclawsky on 2010-12-02
I just got a Vostro 1014 on Monday - It was a great deal at Dell for only $350 and has a 2.2 Ghz processor (and I also ordered another Gig of memory that I had to put in myself, Dell only ships Ubuntu on this machine with 1 GB - It's easy just open the back compartment and push it in and snap in down, now it has a 2GB of memory). I am also happy I don't have to pay the microsoft tax since I don't use it anymore. 

I ran with the Dell supplied 8.10 Ubuntu just long enough to build a recovery DVD (in case I needed it for a return due to hardware not working etc). I did a clean install of Ubuntu 10.10. Except for the sound and microphone everything worked well right after the fresh install. web cam works fine, WiFi works well, DVD/CD reader/writer works fine etc.

I fixed the sound and microphone problems by following the instructions on the thread at; [http://ubuntuforums.org/showthread.php?t=1457859&highlight=vostro+1014+mic](http://ubuntuforums.org/showthread.php?t=1457859&highlight=vostro+1014+mic) by using gedit to modify the alsa-base.conf file
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
Basically adding a line to the very end of this conf file did the trick. 
"options snd-hda-intel model=dell-vostro position_fix=0 enable=yes"  

I am happy to say all the hardware is working fine using 10.10. The compiz video effects works well on the machine. I know some people were complaining about the sound being too low but I think it is fine. It won't blast music but for skype video calls etc it is more than adequate IMHO.

---

### Post by patrickslee on 2010-12-02
I run 10.10 64bit on a Vostro 1510 laptop.

Everything works perfectly out of the box, except that the suspend button (Fn+F1) hibernates rather than suspends. But this is relatively minor comparing to everything else.

---

### Post by mciverza on 2010-12-03
I can run 10.04 x64 and 10.10 on my Vostro 1500  Currently running 2.6.32-24-generic on Lucid 64 bit.  I recently had a fan problem, it stopped turning on. this was sorted by replacing "fancontrol" in /etc/init.d/ with "dellfand" from dellfand.dinglisch.net  Now it is working fine.

---

### Post by dfrandin on 2010-12-03
Been running 10.04 on a Vostro 1400, and 8.04 prior to that. Bought a new drive and installed 10.04 clean on it, and everything worked fine right off, including webcam/bluetooth/wifi....

---

### Post by wgarider on 2010-12-04
> **jwaclawsky said:**
> I just got a Vostro 1014 on Monday - It was a great deal at Dell for only $350 and has a 2.2 Ghz processor (and I also ordered another Gig of memory that I had to put in myself, Dell only ships Ubuntu on this machine with 1 GB - It's easy just open the back compartment and push it in and snap in down, now it has a 2GB of memory). I am also happy I don't have to pay the microsoft tax since I don't use it anymore. 

I ran with the Dell supplied 8.10 Ubuntu just long enough to build a recovery DVD (in case I needed it for a return due to hardware not working etc). I did a clean install of Ubuntu 10.10. Except for the sound and microphone everything worked well right after the fresh install. web cam works fine, WiFi works well, DVD/CD reader/writer works fine etc.

I fixed the sound and microphone problems by following the instructions on the thread at; [http://ubuntuforums.org/showthread.php?t=1457859&highlight=vostro+1014+mic](http://ubuntuforums.org/showthread.php?t=1457859&highlight=vostro+1014+mic) by using gedit to modify the alsa-base.conf file
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
Basically adding a line to the very end of this conf file did the trick. 
"options snd-hda-intel model=dell-vostro position_fix=0 enable=yes"  

I am happy to say all the hardware is working fine using 10.10. The compiz video effects works well on the machine. I know some people were complaining about the sound being too low but I think it is fine. It won't blast music but for skype video calls etc it is more than adequate IMHO.

Great review/help post - thank you!

---

