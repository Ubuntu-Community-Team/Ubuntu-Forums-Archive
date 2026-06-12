---
title: "Sound System problem (OSS, ALSA, etc)"
date: 2006-09-26
forum: Desktop Environments
---

### Post by SRTS on 2006-09-26
OSS doesnt work on my nforce2 mainboard. Only one app can have sound at a time, and will block the device all the time.

So I found out that I have to run everything in a 'wrapper'.

artsdsp and esddsp don't work well. They stop working after a couple of minutes. aoss kind of works, but also stops after 1-2 hours. That's true for various apps, ie webbrowser as well as stand-alone java apps.

How can I get normal working sound for all apps without restarting everything in intervals on my KUbuntu 6.06 system, please? Also the wrapper doesn't work for ALL apps (eg vmware).

When the sound stops working, some apps will start to "lag" like crazy everytime a sound _was supposed to be played_.

Another issue: artsd is being started all the time although I have no program that actually uses arts. Even if I kill it, it will be back randomly like 30 minutes later.

I need to fix sound to turn KUbuntu into a usable desktop system (been using win2k pro so far), any help appreciated.

---

### Post by Gotterdammerung on 2006-09-26
OSS is deprecated. do you have ALSA modules compiled for your kernel?

---

### Post by SRTS on 2006-09-27
Um, I installed KUbuntu and then in KDE I went to "System Settings" and set sound to ALSA. That wrong?

---

### Post by pseudonym on 2006-09-27
Don't bother with ALSA or wrappers if you have a nforce2 motherboard. You're much better off installing the nvsound driver from nvidia, which is an OSS driver. The advantages are - superior sound quality, hardware mixing (meaning you don't need to run a sound server like artsd to get more than one sound at a time),and full use of your hardware if you have a SoundStorm APU (hardware encoded Dolby Digital sound). ALSA is great, but it doesn't get you the best out of your hardware if you have a nforce2 system.

Unfortunately nvidia have given up on development of their linux nforce drivers since November 2005, but it still works great on current kernels. Luckily another Ubuntu user has written a great howto on how to set it up. You can find it [here]("http://www.ubuntuforums.org/showthread.php?t=253725"). I recommend also reading up on potential issues at nvidia.com . Just click on the linux drivers link in the drivers section.

When you get it installed, you should also stop alsa and artsd from running at system startup. A great howto for this can be found [here]("http://www.ubuntuforums.org/showthread.php?t=89491&highlight=sysv-rc-conf").

Should you nonetheless continue with ALSA, I recommend using a ~/.asoundrc file to better regulate how you output sound. Information on how to write one is at [www.alsa-project.org](www.alsa-project.org) , just search your model sound card. It's not hard, it's just a small file with a few relatively simple config options.

HTH

---

### Post by SRTS on 2006-09-27
Oh my god, this is all so complicated, what have I gotten myself into.
Anyways, I can see that your last posting is probably the key to solve my troubles, so I'll try to hack everything according to those links.
This is kinda inacceptable though, I think the Ubuntu guys should fix this instead of loading it onto their users.
Anyway, thanks alot for the hints you guys gave me, I'll post again after I tried that.

---

### Post by pseudonym on 2006-09-27
> **SRTS said:**
> Oh my god, this is all so complicated, what have I gotten myself into.
Anyways, I can see that your last posting is probably the key to solve my troubles, so I'll try to hack everything according to those links.
This is kinda inacceptable though, I think the Ubuntu guys should fix this instead of loading it onto their users.
Anyway, thanks alot for the hints you guys gave me, I'll post again after I tried that. Sorry for complicating the issue. ALSA will still get you decent sound, and it may be easier for you to set up. But if you want the best performance out of your sound hardware, the nvidia driver is the way to go. Plus you'll improve your knowledge of linux along the way.

Don't be confused about OSS being 'deprecated', btw. What that means is that open-source linux sound development is proceeding along the lines of ALSA. It's only closed-source developers who are concentrating on OSS now (eg. opensound.com and previously nvidia). It has nothing to do with performance, especially in this case.

As far as what may seem like a lack of organisation in user support is concerned, you will appreciate that it would be an astronomical task for the official Ubuntu documentation to offer detailed info on configuring any and all hardware out there. Not even microsoft does that ;) . Thus it's up to the community to come to the rescue. And there is plenty of great community-produced documentation here, written with the new user in mind. See the 'how to' section of these forums, for example.

Let us know how you go anyway. I've got an nforce2 motherboard so I'm in a good position to help with queries (so is the guy who wrote the nforce2 sound howto).

---

### Post by SRTS on 2006-09-27
Well on Windows 2000 Pro (I used it till a few months ago when I wanted to see what Linux is like) sound just worked^^

But now I just managed to follow your hints and installed all the stuff. I had two problems on the way, 1) the nvidia installer said he couldn't find kernel source but I was able to solve it! and 2) my internet connection went poof and I had no more eth0 and eth1 devices, but that was only temporarily luckily (I was already freaking out).
The documentation turned out to be actually easy to understand (except for the missing kernel source stuff).

Now with the NVidia drivers and OSS finally for the first time during all these months everything runs totally perfect!!
Thanks a lot, this is what it should be like woooo
Even Java applications now produce sound, and VMWare has sound too! Great!!
All that stuff had remained mute and I had already given up on fixing it (aoss didn't work!)
Very nice I have a usuable non-microsoft Desktop system finally^^
 Thanks everyone.

---

### Post by pseudonym on 2006-09-27
Great. Glad to be of assistance :)

btw, if you also own an nvidia video card you will be able to apply the knowledge you picked up when it comes to installing the latest driver. There's also good documentation on doing that in the how to section of the forums to guide you.

---

### Post by DSK on 2006-09-28
I have an nforce2 mobo and an Audigy2 Platinum Sound card.  I have disabled onboard sound in Bios and want to use my Audigy2 card for all my sound.  I wish to remove all OSS stuff from my fresh install of dapper and use ALSA only.  Is there any guidelines/howto's for this or suggestions.  From the debian site it said to get rid of all OSS modules because they will take resources away from ALSA.

Thanks in advance.

---

### Post by pseudonym on 2006-09-28
Do you have the nvidia OSS module described above installed on your system?

---

### Post by pseudonym on 2006-09-29
If you do, run - ```
sudo rmmod nvsound
sudo rmmod soundcore
sudo nforce-installer --uninstall
``` If it fails, you need to remove the files manually. The complete list is - ```
/usr/bin/nforce-installer
/usr/bin/nforce-bug-report.sh
/usr/bin/nvmixer
/usr/bin/nvmix-reg
/usr/local/lib/libnvopenal.a
/usr/local/lib/libnvalut.a
/usr/share/doc/nforce//ReleaseNotes.html
/lib/modules/<kernel-name>/kernel/sound/oss/nvsound.ko
/var/lib/nvidia-nforce
/var/lib/nvidia-nforce/nforce_log_audio
/var/log/nvidia-installer.log
/var/log/nforce-installer.log
/etc/modprobe.d/nvsound
```Actually,it's a good idea to check these files are gone anyway, even if the uninstaller reports success.

Also, remove or comment out this line you made in /etc/modprobe.d/blacklist -
```
blacklist snd_intel8x0
``` Leave i810_audio blacklisted because it is an OSS module. All traces of the nvsound install should now be gone.

If you didn't uninstall ALSA you could now try running - ```
sudo /etc/init.d/alsa-utils start
``` or reboot if that doesn't work.

---

### Post by DSK on 2006-10-02
> **pseudonym said:**
> Do you have the nvidia OSS module described above installed on your system?

I dont have the nvidia module installed.  I double checked also from your second post and none of those files are on my system.

I am confused still as to wether or not I have OSS modules running. I am still faily new to Linux/ubuntu but my current understanding is that with my Audigy2 card ALSA is the way to go and I should remove all OSS support as they steal resources from my card.  I want to get surround sound setup proper for movies and make sure hardware decoding is working.

-Is it sane to remove all OSS from dapper drake? or is it even there to begin with?
-I dont care to run any apps that dont support ALSA so not worried about breaking any other apps.  My primary use for this box is MythTv, Mplayer, web surfing, and the occational simple games found in add/remove apps menu.

---

### Post by VooDooTom on 2006-12-15
Hi there,

thanks for some hints in here - I got sound with my nForce2 board working, but am still using ALSA. If I try to get OSS to work via:

killall esd
sudo aptitude update
sudo aptitude install libesd0

and starting esd

firstly could nothing be killed, secondly I could make an install of libesd0 but had to uninstall ALSA. And last I could not start esd as the command is not found.

I am using Xubuntu Edgy and latest Kernel.
Do you have any ideas to help?

Thank you very much
Tom

---

