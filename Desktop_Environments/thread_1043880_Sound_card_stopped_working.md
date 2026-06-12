---
title: "Sound card stopped working"
date: 2009-01-18
forum: Desktop Environments
---

### Post by mgrajesh on 2009-01-18
Hi, 

I have been using Ubuntu for more than a year now. I am using 8.04 Hardy Heron. My sound card was working until I installed gfax and/or I performed a recent update using 'update manager'. I tried re-installing alsa drivers, etc. Please help.


rajesh@linuxpc1:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
rajesh@linuxpc1:~$ 

rajesh@linuxpc1:~$ aplay -l
aplay: device_list:217: no soundcards found...
rajesh@linuxpc1:~$

---

### Post by mgrajesh on 2009-01-19
Any help would be greatly appreciated.


Thanks
Rajesh

---

### Post by mgrajesh on 2009-01-20
Anyone? Please help.

---

### Post by XanTrax on 2009-01-20
Can you please post the output of:

```

sudo lshw -C sound

```

---

### Post by mgrajesh on 2009-01-20
Here it is. Thanks for your willingness to help.



rajesh@linuxpc1:~$ sudo lshw -C sound
[sudo] password for rajesh: 
  *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
rajesh@linuxpc1:~$

---

### Post by mister_p_1998 on 2009-01-21
I seem to get this problem every time I do an update & there's a Kernel update installed. Strangely, If I remove the pci sound card & put it in a different slot, it usually starts working again. Im running intrepid now, but it did the same thing on Hardy, might be my crappy HP motherboard. Failing that try going into your grub meny & booting on an earlier Kernel, if it works, keep that one as default. Hope this helps.

Steve

---

### Post by XanTrax on 2009-01-21
This part:

```

*-multimedia UNCLAIMED 

```

Means that your multimedia card has not claimed a device driver.  That is about all the information I can give you right now.  This will at least give you something to go on and search for.

EDIT:

Here is something for you to work from:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by mgrajesh on 2009-01-22
Steve,

Using the old kernel seems to be producing the sound at login prompt, but no sound afterwards. I will follow the link that XanTrax provided and get back to you.

Thanks

---

### Post by XanTrax on 2009-01-22
> **mgrajesh said:**
> Steve,

Using the old kernel seems to be producing the sound at login prompt, but no sound afterwards. I will follow the link that XanTrax provided and get back to you.

Thanks

Since the sound is being produced at the login prompt on an old kernel can you please boot into that kernel, open a terminal and type:

```

sudo lshw -C sound

```

and copy/paste the output of that.  To reiterate, make sure you are booted into the kernel that produces the login prompt sound.

If lshw does NOT say "UNCLAIMED" in it (like it did above) then open a terminal and type

```

alsamixer -c 0

```

and make sure no devices are muted (there will be an mm or m under the volumed devices).  This is a test to see if your sound card is actually 100% working on an old kernel.  All we need to do now is to get it to be claimed on the new kernel.

Also, please type 

```

uname -a

```

and post the output of that from both kernels here as well.  You could also just tell me what kernel version produces the login prompt and the one that does not.

---

### Post by mgrajesh on 2009-01-24
XanTrax,


Currenct status is -
              - Sound at the login prompt
              - No sound played after login.
Your help is greatly appreciated.


Here is the output of lshw.

rajesh@linuxpc1:~$ sudo lshw -C sound
  *-multimedia            
       description: Audio device
       product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
rajesh@linuxpc1:~$ 



"alsamixer -c 0" command shows that the Master is not muted.



And here is the uname output
rajesh@linuxpc1:~$ uname -a
Linux linuxpc1 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux
rajesh@linuxpc1:~$ 



Thanks
Rajesh

---

### Post by XanTrax on 2009-01-24
> **mgrajesh said:**
> XanTrax,


Currenct status is -
              - Sound at the login prompt
              - No sound played after login.
Your help is greatly appreciated.


Here is the output of lshw.

rajesh@linuxpc1:~$ sudo lshw -C sound
  *-multimedia            
       description: Audio device
       product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
rajesh@linuxpc1:~$ 



"alsamixer -c 0" command shows that the Master is not muted.



And here is the uname output
rajesh@linuxpc1:~$ uname -a
Linux linuxpc1 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux
rajesh@linuxpc1:~$ 



Thanks
Rajesh

Hi mgrajesh,

This is going to sound a little dumb but can you please open up sound properties in Preferences -> Sound and list here what is selected?  Then, go about trying each selection in the drop down menus and clicking 'test' next to the menus.

Please let me know how that goes.  It doesnt make much sense that your sound card is reporting UNCLAIMED driver and yet, you get the login sound.  By the 'login sound' you mean those drum kind of sounds?

---

### Post by mgrajesh on 2009-01-24
XanTrax,

Sorry, I did not describe clearly in my last note. After switching to Ubuntu 8.10 (and good kernel), I see the sound modules are loaded. Multimdedia is no longer unclaimed (see my previous post). Yes, by login sound, I meant drum sound. I still can hear the drum sound at the login prompt.

When I select System->Preferences->Sound, under 'Sound Events' and 'Music and Movies', I see the following

Selection                              Click 'Test'
============                           =================
Autodetect                             No Sound

HDA Intel ALC880 Analog(ALSA)          Error - audiotestsrc wave=sine 
                                      freq=512 ! audioconvert ! 
                                      audioresample ! gconfaudiosink:  
                                      Could not open audio device for playback

HDA Intel ALC880 Analog(OSS)            Long beep
(This entry appears twice)

ALSA - Advanced Linux ....              No Sound

OSS -Open Sound System                  Long Beep

PulseAudio Sound Server                 No Sound


I still cannot hear login sound, movie, youtube etc.

What am I doing wrong? 
Something silly, for sure. Please help

Thanks
rajesh

---

### Post by XanTrax on 2009-01-24
> **mgrajesh said:**
> XanTrax,

Sorry, I did not describe clearly in my last note. After switching to Ubuntu 8.10 (and good kernel), I see the sound modules are loaded. Multimdedia is no longer unclaimed (see my previous post). Yes, by login sound, I meant drum sound. I still can hear the drum sound at the login prompt.

When I select System->Preferences->Sound, under 'Sound Events' and 'Music and Movies', I see the following

```

Selection                              Click 'Test'
============                           =================
Autodetect                             No Sound

HDA Intel ALC880 Analog(ALSA)          Error - audiotestsrc wave=sine 
                                      freq=512 ! audioconvert ! 
                                      audioresample ! gconfaudiosink:  
                                      Could not open audio device for playback

HDA Intel ALC880 Analog(OSS)            Long beep
(This entry appears twice)

ALSA - Advanced Linux ....              No Sound

OSS -Open Sound System                  Long Beep

PulseAudio Sound Server                 No Sound

```

I still cannot hear login sound, movie, youtube etc.

What am I doing wrong? 
Something silly, for sure. Please help

Thanks
rajesh


Alright, making progress.  Did each area of the sound properties yield all of those same results?  

For example, when you selected HDA Intel ALC880 Analog(OSS) for Sound Events and clicked test, it made a long beep as well as selecting it under music and movies?

If this is the case then select HDA Intel ALC880 Analog(OSS) for the 3 "Sound Playback" instances in the sound properties and then try to play a video or something.

Like I said though, if we can get the login sound then we can surely get other sounds to work.  Try what I said above; select HDA Intel ALC880 Analog(OSS) for all instances of "Sound Playback".  Also, under "Default Mixer Tracks" select the HDA Intel ALC880.

---

### Post by mister_p_1998 on 2009-01-25
Is it worth trying booting on a live cd?

Steve

---

### Post by XanTrax on 2009-01-25
> **mister_p_1998 said:**
> Is it worth trying booting on a live cd?

Steve

Not entirely because its just a configuration thing.  Seeing as "lshw -C sound" says that it is not UNCLAIMED anymore...so, its gotta be something small.

---

### Post by mister_p_1998 on 2009-01-26
Id still try moving to a new pci slot, I got a Kernel update yesterday & my soundcard died (again!)
booted this morning and all is working again!
It seems to come & go as it pleases!
Its only a testbox I only use for secondlife, so no major worries.

Steve

---

### Post by fsav on 2009-02-01
Hi,

I have been having the exact same problem you (mgrajesh) had for the last 2-3 days or so. I don't remember specifically having updated the kernel, but I guess this could have started the problem (if it was a security update, I have probably applied it quite fast, though).

Anyway, by "exact same" I mean:
* Using Hardy
* Sound suddenly stopped working after months of loyal service, volume control gave error messages etc.
* I had the same outputs for "lspci | grep Audio", "aplay -l"
* For "sudo lshw -C sound" I also had an UNCLAIMED output (and I have the same chipset (82801FB))

But I have a lower version of the kernel apparently (2.6.24-23), though.

But when I tried loading the sound modules with modprobe ("modprobe snd-intel8x0"), it told me it couldn't find the modules. I started searching for them (they're in /lib/modules/2.6.xyz), and realized there were no "ubuntu" and "madwifi" subdirectories under 2.6.24-23-generic, and they were the directories that contained the snd-xyz modules.

So, long story short, I went to the package manager and realized that the package "linux-ubuntu-modules-2.6.24-23-generic" was not installed (but it was installed for earlier kernel versions). I installed it, rebooted, and now sound works again, yay!

Hope this helps.

---

