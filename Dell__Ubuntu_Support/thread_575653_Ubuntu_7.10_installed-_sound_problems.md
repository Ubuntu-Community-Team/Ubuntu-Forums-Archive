---
title: "Ubuntu 7.10 installed- sound problems"
date: 2007-10-14
forum: Dell  Ubuntu Support
---

### Post by igggyc on 2007-10-14
Hello

I have just installed the pre-release of Ubuntu 7.10 Gutsy Gibbon with just 4 days until its release on my Dell Inspiron 1720. Everything appears to be fine, except I can't get my soundcard to work.

According to dell and my motherboard settings, the soundcard is a Sigmatel 9205.

I looked briefly on google and found this link:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

which seemed to address my problem. I followed the instructions there, my sound card still is not detected. the volume control symbol is crossed off by a little red circle and no sound plays.

At first I thought maybe the drivers provided on the link were wrong, so i went to the following site:

[http://www.gtlib.gatech.edu/pub/suse...apshot/driver/](http://www.gtlib.gatech.edu/pub/suse...apshot/driver/)

and downloaded the following file:

alsa-driver-hg20071013.tar.bz2 and followed the first link's intructions on unzipping this file, yet still nothing works.

i must add i am not an experienced user, so any help for idiots such as myself would be greatly appreciated. i should also add that command: cat /proc/asound/card0/codec#* | grep Codec

comes back as invalid and fails to retrieve my codec info. it says "no such file or directory".

any help appreciated!!!!!

p/s/ all the unzipped files are in a directory caleld "alsa" located in home folder...

---

### Post by Skweek on 2007-10-14
I had exactly the same problem on my 1720 with Gutsy, and after much trawling and googleing, I came to the realisation that this wasn't going to be fixed anytime soon - so I re-installed Feisty.  I won't be upgrading to gutsy untill this problem is fixed.

Good luck.

---

### Post by igggyc on 2007-10-14
so what you're saying is in feisty it supports my soundcard, but in the newer version 7.10 it doesn't. that doesn't make much sense, it's meant to improve with newer versions ...

---

### Post by Razzoo on 2007-10-14
1720 with Gutsy RC1 -- installed alsamixergui via Synaptic -- nothing!
Like igggyc, followed the instructions in
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
using the latest ALSA Developmental Releases from
[http://www.alsa-project.org/main/index.php/Download]("http://www.alsa-project.org/main/index.php/Download")
-- no satisfaction

Resolved by following the instructions given at the bottom of the first page of
[http://ubuntuforums.org/showthread.php?p=3489580]("http://ubuntuforums.org/showthread.php?p=3489580")
Namely:
the solution
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

On rebooting and enabling Device Controls, sound appears to work.

---

### Post by Skweek on 2007-10-15
I didn't see that fix - 7.10 on my laptop didn't detect any sound hardware at all.  Maybe I'll give gutsy another chance in a few days time.

---

### Post by Razzoo on 2007-10-15
Forgot to mention that following the HdaIntelSoundHowTo instructions resulted in my adding this line:
options snd-hda-intel model=dell-m44
to the end of the file /etc/modprobe.d/alsa-base.
(Search for STAC9205 in ALSA-Configuration.txt, located in the subdirectory /alsa-kernel/Documentation/ of the alsa-driver-1.0.15rc3 directory.)

---

### Post by tommysven on 2007-10-16
The solution 

> 
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa


worked for me on my Dell Latitude D620 also after a reboot:)

---

### Post by igggyc on 2007-10-16
that's great.

thanks to the user (tomysven) who posted that solution, my sound now works. except for a minor issue.

i get sound from my laptop speakers, except when i plug in some real speakers using my headphone jack, the laptop speakers continue playing, except i get nothing out of the proper speakers.

many forums have said to change the line in the alsa-base document, which now reads:

options snd-hda-intel model=ref

to

options snd-hda-intel model=stack3

and this has worked for many people, but when in change it, i can't get any sound out of the laptop speakers, but i do get sound when i plug in extneral speakers to my headphone jack.

many sound cards out there have a feature for a headphone sensor which fixes all their problems, mine however does not have that sensor feature.

i've played around with all the settins including those of alsamixer,and i have had no success. please someone give me a solution, i want to end these stupid errors...

---

### Post by moopere on 2007-10-16
> **tommysven said:**
> The solution 



worked for me on my Dell Latitude D620 also after a reboot:)

This worked for me too.  Thanks a lot for the tip.  Can't see why this works though - seems to have downloaded the current alsa source from ubuntu and recompiled it....surely though the precompiled ubuntu deb file would have been compiled from the same source??

Weird.

Anyway, it works.  Cheers!

Craig

---

### Post by Lek130 on 2007-10-17
works also for the d630 with the latest gutsy.
Very good! Thanks. I saw people rebuilding kernels, crying, falling back to feisty, etc. and this is easy and fast and works.

Great.

---

### Post by r76 on 2007-10-17
[QUOTE=Razzoo;3534703the solution
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

On rebooting and enabling Device Controls, sound appears to work.[/QUOTE]

Works great here, thanks chinook, and razzoo for posting here!  Tried the other suggestions on the forum (recompile kernel, or remove alsa-base and install a CVS version) with no luck.  This was faster and works.

Dell D630, nvidia 135, intel 3945 wifi - the whole setup is working great :)

EDIT:
By the way I have just spent 8 hours reinstalling XP and all my apps and preferences, as despite having the laptop for a month I didn't notice the sound wasn't working in XP until yesterday :(
It was bought with Vista but I installed XP, and turning off system sounds is one of the first things I do after a fresh install :roll:
Apparently the fix for D630 sound is contained in the Dell Notebook System Software download which I left out as it is marked 'optional'(!) - and needs to be installed before ANYTHING else - specifically the intel chipset driver, then audio driver in that order (see second post [here]("http://www.dellcommunity.com/supportforums/board/message?board.id=insp_audio&message.id=37097&query.id=94593#M37097")).  Just shows how much easier it can be to deal with these things in Ubuntu.

---

### Post by ilushkin on 2007-10-19
> **Razzoo said:**
> 1720 with Gutsy RC1 -- installed alsamixergui via Synaptic -- nothing!
Like igggyc, followed the instructions in
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
using the latest ALSA Developmental Releases from
[http://www.alsa-project.org/main/index.php/Download]("http://www.alsa-project.org/main/index.php/Download")
-- no satisfaction

Resolved by following the instructions given at the bottom of the first page of
[http://ubuntuforums.org/showthread.php?p=3489580]("http://ubuntuforums.org/showthread.php?p=3489580")
Namely:
the solution
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

On rebooting and enabling Device Controls, sound appears to work.

This solution worked for me, thanks a bunch!

---

### Post by wty on 2007-10-19
It works good for me to with my D630, but its not working proper. I get sound both on my headphones, and laptopspeakers. Or just on the headphones, and no on the speakers, even if the headphones isn't plugged in. 

But I had the same problem in feisty, so I can live with it. But if someone knows how to fix the problem, I will happily test it out. :)

---

### Post by dardhal on 2007-10-21
Just upgraded to Kubuntu 7.10, had suffered from this problem. Sound is provided by the nVIDIA nForce 4 HDA on-board codec, but after the upgrade I got no sound, no mixer, and no sound card detected.

After some wandering, the problem showed quite clear: during the upgrade, Kubuntu somewhat messed up with the installed kernels. Once in 7.10 the system boots the 2.6.22-14-386 kernel, but apart from this the kernel package 2.6.22-14-generic is also installed. However, the package where the snd-hda-intel.ko kernel module is included, was not installed for the kernel version in use: the package linux-ubuntu-modules-2.6.22-14-generic was installed, but no the really needed package, linux-ubuntu-modules-2.6.22-14-386.

So after a simple "apt-get install linux-ubuntu-modules-2.6.22-14-386" and a manual "modprobe snd-hda-intel", sound was back. I suppose that on reboot the kernel module will be auto loaded as usual.

So, to summarize, check there is a "snd-hda-intel" kernel module installed for the exact kernel version you are running (check with "uname -a", "locate snd-hda-intel" and so on), and if missing, just install the missing package.

Cleaner, and more correct solution than the one provided in previous messages, hope it helps.

---

### Post by sseremeth on 2007-10-21
> **tommysven said:**
> The solution 



worked for me on my Dell Latitude D620 also after a reboot:)


You're the man.  I spent a bunch of time re-installing stuff when I stumbled across these directions and my d620 now has sound as well.  Headache averted.

---

### Post by slyboots on 2007-10-22
Yes it help when you use the:

the solution
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

but, if you install new kernel, then you need to make the same again.

Second issue is by Suspend -> sound don't work and you must restart the pc.

---

### Post by Pablonius Monk on 2007-10-23
Thanks tommysven!

Your solution worked on my Ubuntu Dell XPS 410n. Gutsy Gibbon's running like a charm now. Thanks so much! :guitar:[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

> The solution

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

---

### Post by bluedragon436 on 2007-10-26
I had an issue with my sound as well, not sure how I fixed the issue, but it seems to work fine now....except for the fact of I can't use the keyboard buttons for the volume and mute adjustment.  they do adjust the slider in the volume control for the speaker...but make no difference in the output volume or muting...which is kind of annoying, but i guess until I can figure that out I can at least use my computer and have sound...I just have to open the volume control to change the volume and to mute it...

---

### Post by vuroth on 2007-11-25
> **Razzoo said:**
> Resolved by following the instructions given at the bottom of the first page of
[http://ubuntuforums.org/showthread.php?p=3489580]("http://ubuntuforums.org/showthread.php?p=3489580")
Namely:
the solution
sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

On rebooting and enabling Device Controls, sound appears to work.

Haven't rebooted yet, but that last command pops up a window, which seems to invite further interaction.  Maybe the solution is complete, but it doesn't look like it....

---

