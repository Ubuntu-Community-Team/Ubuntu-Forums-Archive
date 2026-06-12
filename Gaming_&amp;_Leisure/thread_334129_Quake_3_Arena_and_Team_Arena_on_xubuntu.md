---
title: "Quake 3 Arena and Team Arena on xubuntu"
date: 2007-01-08
forum: Gaming &amp; Leisure
---

### Post by mikeym on 2007-01-08
Hello All.

I'm trying to install quake 3 and quake 3 team arena on ubuntu and I am having a few problems. I have been trying to follow [this help wiki]("https://help.ubuntu.com/community/Games/Native/QuakeIIIArena") to do it and I have quake 3 loaded but it crashes a bit randomly (more than once just after finishing the first level - as soon as it shows you on the pedestal).

I followed the guide up to the security update but I couldn't find that file so I couldn't install it. I have also put my pk3 files from quake 3 team arena in baseq3. When I installed the binaries I also allowed it to install the Team Arena info. 

I am running a nvidia 3dfx using the legacy drivers you get from the ubuntu repositories. 

I have managed to get sound working by adding 

```

        #-----------------------
        # fix sound for Quake 3 and Enemy Territory
        echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
        echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
        echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
        #------------------------

```

at the end of the  do_start() section in /etc/init.d/bootmisc.sh

Could someone help me get it running stable and also Team Arena running too?


Cheers.

---

### Post by mikeym on 2007-01-08
It's sound card related as I have now run quake 3 and team arena with the *+set s_initsound 0* parameter and both seem to be running OK without sound. 

I found this at [this website]("http://zerowing.idsoftware.com/linux/q3a/#install"):

```

VIA chipset and AC97 driver:
This combination is known to have various issues. They have been fixed in recent drivers (thanks to Arne Schmitz for the heads up):

http://sourceforge.net/projects/gkernel has got the up to date version of 
the AC97 kernel driver. The current version can be found here:

http://prdownloads.sourceforge.net/gkernel/via82cxxx-1.1.15.tar.gz

It has working mmap sound, so Q3 shouldn't be a problem any more.

```

Now this rang a bit of a bell in that I have some kind of via sound card but I don't know which one for sure and I don't know where'd tell me. I tried this as a start:

```

$ cat ls /proc/asound/cards
cat: ls: No such file or directory
 0 [V8233          ]: VIA8233 - VIA 8233
                      VIA 8233 with ALC200,200P at 0xe400, irq 5
 1 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10

```

It doesn't appear to fit with the 'C' part of the name but I'm not sure.

Does anyone have any ideas?

---

### Post by mikeym on 2007-01-09
Hi,

Well I found the solution for anyone that's interested it was that the sound on my via8233 sound card was causing problems for quake 3. 

So for anyone using a via soundcard with the snd-via82xx module (you can test this by typing *modprobe -l | grep snd-via82xx* and seing if it lists anything) add:

```

options snd-via82xx dxs_support=4

```

to your */etc/modprobe.conf* and then reboot (I had to create the /etc/modprobe.conf because I didn't have one to begin with.)

---

### Post by LordFiodor on 2007-01-09
I managed to run Quake III via ioquake 3, which also fixes the sound problem by using ALSA. you also can run any mod with it, but there is no PunkBuster support.

---

### Post by mikeym on 2007-01-09
Thanks for the reply,

I had found that and decided to stick with the id release. It is now working fairly well by making the changes to */etc/init.d/bootmisc.sh* (a general sound fix for edgy - I think) and */etc/modprobe.conf* (for via82xx sound cards).

I installed punk buster and it's working as well.

I tried out joss and q3jack to see if they would sharpen up the sound but they both ran like dogs and had loads of time out problems. (They also required a bit of tweaking to compile.)

Team Arena ran without any problems once I had the sound up and working. :)

---

### Post by fakie_flip on 2007-01-22
> **mikeym said:**
> Hello All.

I'm trying to install quake 3 and quake 3 team arena on ubuntu and I am having a few problems. I have been trying to follow [this help wiki]("https://help.ubuntu.com/community/Games/Native/QuakeIIIArena") to do it and I have quake 3 loaded but it crashes a bit randomly (more than once just after finishing the first level - as soon as it shows you on the pedestal).

I followed the guide up to the security update but I couldn't find that file so I couldn't install it. I have also put my pk3 files from quake 3 team arena in baseq3. When I installed the binaries I also allowed it to install the Team Arena info. 

I am running a nvidia 3dfx using the legacy drivers you get from the ubuntu repositories. 

I have managed to get sound working by adding 

```

        #-----------------------
        # fix sound for Quake 3 and Enemy Territory
        echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
        echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
        echo "quake3.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
        #------------------------

```

at the end of the  do_start() section in /etc/init.d/bootmisc.sh

Could someone help me get it running stable and also Team Arena running too?


Cheers.

Do you understand what those commands do? The first one puts "et.x86 0 0 direct" in /proc/asound/card0/pcm0p/oss. The next one puts overwrites the file to put "quake3.x86 0 0 direct" in the file. The third one overwrites (anything that was in the file is gone) "quake3.x86 0 0 disable", so why do the first two commands just to have what they put in a file erased?

---

### Post by mikeym on 2007-01-30
Those commands were lifted from somewhere else in the foum and whilst they did have an effect by stopping the initial crash I was having with Q3 - it was still far from stable.

No I don't know what the commands do. But they are writing to a /proc file which means that it is not just a normal file. Would you happen to know how a file in /proc would treat a call to overwrite a file like this?

>  The proc filesystem is a pseudo-filesystem rooted at /proc that contains user-accessible objects that pertain to the runtime state of the kernel and, by extension, the executing processes that run on top of it. "Pseudo" is used because the proc filesystem exists only as a reflection of the in-memory kernel data structures it displays. 

---

