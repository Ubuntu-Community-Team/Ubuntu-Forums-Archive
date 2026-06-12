---
title: "Randomly no sound have to restart"
date: 2010-09-22
forum: Desktop Environments
---

### Post by Emanuele_Z on 2010-09-22
Hi all,

I installed Ubuntu 10.04 x86-64 on my pc.
I have the following hardware:

Processor: AMD Phenom II X4 965 @ 3.40GHz (Total Cores: 4)
Motherboard: ASUSTeK M4A88TD-V EVO/USB3
Chipset: AMD RS780 Alternate
Memory: 8002MB
Disk: 750GB MDT MD7500AADS-0 + 1500GB SAMSUNG HD154UI
Graphics: nVidia 470 GTX 1280MB (607/1674MHz)
Audio: Realtek ID 892

Sometime (25%+) happens that when I start the computer I have no sound and if I look at System->Preferences->Sound I see no devices (I have the chip on the motherboard and a USB Headphone+Mic set as default).
When this happens I can't even set the CPU frequency from the same named applet and to shutdown the computer I have to:

*sudo shutdown -h now*

Usually after 1 restart I'll have the sound, and both audio peripherals are detected.
Am I the only one who's having this issue?
Any idea how to fix it?

Cheers,

---

### Post by gamer_pro_2000 on 2010-09-22
Have you tried killing pulseaudio and then restarting it?  Try pulseaudio -k and then just run pulseaudio in terminal and see if it comes back.

---

### Post by lkjoel on 2010-09-24
> **Emanuele_Z said:**
> Hi all,

I installed Ubuntu 10.04 x86-64 on my pc.
I have the following hardware:

Processor: AMD Phenom II X4 965 @ 3.40GHz (Total Cores: 4)
Motherboard: ASUSTeK M4A88TD-V EVO/USB3
Chipset: AMD RS780 Alternate
Memory: 8002MB
Disk: 750GB MDT MD7500AADS-0 + 1500GB SAMSUNG HD154UI
Graphics: nVidia 470 GTX 1280MB (607/1674MHz)
Audio: Realtek ID 892

Sometime (25%+) happens that when I start the computer I have no sound and if I look at System->Preferences->Sound I see no devices (I have the chip on the motherboard and a USB Headphone+Mic set as default).
When this happens I can't even set the CPU frequency from the same named applet and to shutdown the computer I have to:

*sudo shutdown -h now*

Usually after 1 restart I'll have the sound, and both audio peripherals are detected.
Am I the only one who's having this issue?
Any idea how to fix it?

Cheers,
Try Fix your sound! in my signature.
Then use Post-Fix your sound! in my signature.

---

### Post by Emanuele_Z on 2010-09-25
> **gamer_pro_2000 said:**
> Have you tried killing pulseaudio and then restarting it?  Try pulseaudio -k and then just run pulseaudio in terminal and see if it comes back.

The issue is that PA is running and alive when I see no devices (and paradoxally when I happen to have no audio devices found, SC2 with wine runs 2x faster...).

Any other idea?

---

### Post by lkjoel on 2010-09-25
> **Emanuele_Z said:**
> The issue is that PA is running and alive when I see no devices (and paradoxally when I happen to have no audio devices found, SC2 with wine runs 2x faster...).

Any other idea?
Follow the instructions of my last post.

---

### Post by Emanuele_Z on 2010-09-26
> **lkjoel said:**
> Follow the instructions of my last post.

Sorry mate, I don't want to use OSS. I'll stick with ALSA.

An other idea about my issue?

Cheers,

---

### Post by blueturtl on 2010-09-26
What is your output for command ```
cat /proc/asound/cards
``` when this happens?

Based on your symptoms at this point I would say either something wrong with the motherboard, or maybe a bug with the BIOS.

You could try see if the BIOS settings for the integrated sound card can be altered. Here's what I suspect: there is a setting such as "HD Audio Codec" or something that is set to "Auto". Try see if you can just set it to "Enabled". This is based on the idea that for some reason your system thinks it has another sound card and disables the on-board audio.

Just a thought.

---

### Post by Emanuele_Z on 2010-09-26
> **blueturtl said:**
> What is your output for command ```
cat /proc/asound/cards
``` when this happens?

Based on your symptoms at this point I would say either something wrong with the motherboard, or maybe a bug with the BIOS.

You could try see if the BIOS settings for the integrated sound card can be altered. Here's what I suspect: there is a setting such as "HD Audio Codec" or something that is set to "Auto". Try see if you can just set it to "Enabled". This is based on the idea that for some reason your system thinks it has another sound card and disables the on-board audio.

Just a thought.

Hi, the output is:
```

ema@darklady:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfbff8000 irq 16
 1 [Headset        ]: USB-Audio - Logitech USB Headset
                      Logitech Logitech USB Headset at usb-0000:00:12.0-2, full speed

```

My motherboard is an *ASUSTeK M4A88TD-V EVO/USB3*.
In the BIOS the setting for internal audio is *Enabled* (and it says front device AC97 - which is chones - or I could use HD Audio).

What do you think?
Should I update the BIOS?

Cheers,

---

### Post by blueturtl on 2010-09-26
A lot of care need to be taken to update the BIOS, it shouldn't be done except maybe as a last resort.

Did you run the command when the soundcard was working or when you were experiencing the problem?

---

### Post by Emanuele_Z on 2010-09-26
> **blueturtl said:**
> A lot of care need to be taken to update the BIOS, it shouldn't be done except maybe as a last resort.

Did you run the command when the soundcard was working or when you were experiencing the problem?

When it's working...
I'll rerun the command once is not working an will let you know...

Update.
After a restart, to check BIOS version, the sound doesn't work. The output of the command line is:
```

ema@darklady:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfbff8000 irq 16
 1 [Headset        ]: USB-Audio - Logitech USB Headset
                      Logitech Logitech USB Headset at usb-0000:00:12.0-2, full speed

```

If I go into sound properties, no devices are found, and the output is set to *Dummy Output*.
Do you still believe a BIOS upgrade shouldn't be needed? 

Cheers,

---

### Post by blueturtl on 2010-09-26
I think Ubuntu today has a USB boot flash creator in one of it's submenus (can't remember the exact name, it's not included in 9.10).

The easiest way probably is to use a floppy image of a DOS bootdisk that you could then modify (copy the BIOS image and utilities to). After obtaining such an image you need to mount it to something like /mnt, then copy the files over, then unmount the image and write it to your flash memory.

If you need more precise, step by step instructions I can provide those.

Also, if you need a suitable image file, I have some. :)

---

### Post by Emanuele_Z on 2010-09-26
> **blueturtl said:**
> I think Ubuntu today has a USB boot flash creator in one of it's submenus (can't remember the exact name, it's not included in 9.10).

The easiest way probably is to use a floppy image of a DOS bootdisk that you could then modify (copy the BIOS image and utilities to). After obtaining such an image you need to mount it to something like /mnt, then copy the files over, then unmount the image and write it to your flash memory.

If you need more precise, step by step instructions I can provide those.

Also, if you need a suitable image file, I have some. :)

I've updated my previous post.
I think I might be using Asus EZ Flash 2 utility to update it... :)

Let me know,

Cheers,

---

### Post by blueturtl on 2010-09-26
> **Emanuele_Z said:**
> When it's working...
I'll rerun the command once is not working an will let you know...

Update.
After a restart, to check BIOS version, the sound doesn't work. The output of the command line is:
```

ema@darklady:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xfbff8000 irq 16
 1 [Headset        ]: USB-Audio - Logitech USB Headset
                      Logitech Logitech USB Headset at usb-0000:00:12.0-2, full speed

```

If I go into sound properties, no devices are found, and the output is set to *Dummy Output*.
Do you still believe a BIOS upgrade shouldn't be needed? 

Cheers,

Ah I see. Well according to the output of the command the sound card *is* detected and enabled. Gnome however seems oblivious to this...

Hmm. :D

At this point I would advice against the BIOS update.

---

### Post by Emanuele_Z on 2010-09-26
> **blueturtl said:**
> Ah I see. Well according to the output of the command the sound card *is* detected and enabled. Gnome however seems oblivious to this...

Hmm. :D

At this point I would advice against the BIOS update.

Still, for example, I can't set the CPU frequency from the applet when this happens...
I'm still tempted to update the BIOS...
Do you have the same motherboard?

Cheers,

---

### Post by blueturtl on 2010-09-26
So basically this is what the problem boils down to:

Gnome periodically refuses to acknowledge audio hardware that is enabled in BIOS and detected by the kernel and ALSA...

In your first post you said you also had some problem with your CPU scaling applet? Do you believe these to be related?

Diagnosing this could be tricky indeed, because right now we don't know what changes between the reboots.

I have a suggestion: to rule out a corrupt Gnome profile, create a new user, log in as that user for some time, and see if the problem ever occurs over there. If not, you've got nothing more than a Gnome settings corruption.

---

### Post by blueturtl on 2010-09-26
> **Emanuele_Z said:**
> Still, for example, I can't set the CPU frequency from the applet when this happens...
I'm still tempted to update the BIOS...
Do you have the same motherboard?

Cheers,

That does seem odd. Updating the BIOS could do the trick, but I always like to be sure of what the problem is before advicing a remedy. :)

I don't have the same motherboard, no. This is all based on experience with several motherboards.

What version of Ubuntu and the kernel are you running? Is it possible the motherboard is so new it's not fully supported by the version of the kernel you are using?

---

### Post by Emanuele_Z on 2010-09-26
> **blueturtl said:**
> So basically this is what the problem boils down to:

Gnome periodically refuses to acknowledge audio hardware that is enabled in BIOS and detected by the kernel and ALSA...

In your first post you said you also had some problem with your CPU scaling applet? Do you believe these to be related?

Diagnosing this could be tricky indeed, because right now we don't know what changes between the reboots.

I have a suggestion: to rule out a corrupt Gnome profile, create a new user, log in as that user for some time, and see if the problem ever occurs over there. If not, you've got nothing more than a Gnome settings corruption.

It occours to other users as well... :(

Cheers,

---

### Post by blueturtl on 2010-09-26
> **Emanuele_Z said:**
> It occours to other users as well... :(

Cheers,

Damn, that would have been too easy.

What version of Ubuntu/kernel are you running? edit: Nevermind, checked your first post.

---

### Post by Emanuele_Z on 2010-09-26
> **blueturtl said:**
> That does seem odd. Updating the BIOS could do the trick, but I always like to be sure of what the problem is before advicing a remedy. :)

I don't have the same motherboard, no. This is all based on experience with several motherboards.

What version of Ubuntu and the kernel are you running? Is it possible the motherboard is so new it's not fully supported by the version of the kernel you are using?

I reckon this might be the cause perhaps... the MoBo and all components are pretty new.

I should upgrade the BIOS, should I?

Cheers,

---

### Post by blueturtl on 2010-09-26
Ideas at this point:

1) Try updating the BIOS.

2) Try the [Ubuntu Maverick Beta LiveCD]("http://www.ubuntu.com/testing/maverick/beta") (or install as a second OS) just to see if it's a problem with hardware support in Ubuntu. The Maverick Beta has a newer kernel, so if it's a kernel problem it might have been solved for the new version.

If someone wiser wants to chime in, feel free. :)

Few more questions, Emanuele_Z: Have you had this problem from the beginning with Ubuntu or did it start happening some time ago? If it wasn't there from the start, have you done any hardware/software alteration to your system recently?

---

### Post by Emanuele_Z on 2010-09-26
> **blueturtl said:**
> Ideas at this point:

1) Try updating the BIOS.

2) Try the [Ubuntu Maverick Beta LiveCD]("http://www.ubuntu.com/testing/maverick/beta") (or install as a second OS) just to see if it's a problem with hardware support in Ubuntu. The Maverick Beta has a newer kernel, so if it's a kernel problem it might have been solved for the new version.

If someone wiser wants to chime in, feel free. :)

Few more questions, Emanuele_Z: Have you had this problem from the beginning with Ubuntu or did it start happening some time ago? If it wasn't there from the start, have you done any hardware/software alteration to your system recently?

1) Done. Let's see what happens...

Btw the fact that I'm not able to set the CPU Frequency when this happens (perhaps with BIOS update happened :) ), do you think might be related with something else?

I was thinking about the Kernel as well, that perhaps is a bit older with 10.04 and my MoBo isn't fully supported...

Btw, Asus EZ Flash 2 worked a charm... ;)

Cheers,

---

### Post by Emanuele_Z on 2010-09-26
Unluckily, even after updating the BIOS this still happens.

It might be the kernel a bit too old as we were saying.
Killing and restarting PA doesn't help... again I think it's a deeper issue (as I said before when this happens I can't touch other things like CPU Frequency, and when I click shutdown it just logs off; I have to *sudo shutdown -h now* to make it shutdown).
Do you know if is there a way to test a new kernel version without having to install an unstable version of Ubuntu?
What do you recommend?

Cheers,

Btw, I always got this issue since I installed 10.04 x86-64 (keep in mind my pc has been assembled in June this year with pretty new components).

---

### Post by blueturtl on 2010-09-26
> **Emanuele_Z said:**
> Unluckily, even after updating the BIOS this still happens.

It might be the kernel a bit too old as we were saying.
Killing and restarting PA doesn't help... again I think it's a deeper issue (as I said before when this happens I can't touch other things like CPU Frequency, and when I click shutdown it just logs off; I have to *sudo shutdown -h now* to make it shutdown).
Do you know if is there a way to test a new kernel version without having to install an unstable version of Ubuntu?
What do you recommend?

Cheers,

Btw, I always got this issue since I installed 10.04 x86-64 (keep in mind my pc has been assembled in June this year with pretty new components).

Well... you can always [compile the kernel yourself]("http://blog.avirtualhome.com/2010/07/14/how-to-compile-a-ubuntu-2-6-35-kernel-for-lucid/"), even one newer than the one in Maverick. It's a bit of a chore though.

The other alternative is to [try a PPA]("http://ubuntuforums.org/showpost.php?p=9763725&postcount=8") where someone else does the compiling for you (all you have to do is apt-get install the package for the new kernel). However it's a third party replacement for the *kernel* of the entire OS, so keep that in mind. :)

Also make sure, if you use closed-source drivers that there is a compatible package available to the kernel version you're going to try (would be a bummer to have working audio and no video acceleration).

Maverick is due next month, so if you can stand the odd reboot for less than a month, you'll soon get to try a certified and new version of Ubuntu.

edit: Just thought I should say that even if you install third party kernels, you can still fall back to the default Ubuntu kernel if you wish, so in that sense there is no danger in trying. Just hit esc to see the boot menu when starting the computer and select the older kernel.

---

### Post by lolzers32 on 2010-09-26
Did you check to see if your audio device is connected? That might be the problem.:popcorn::smile::guitar:

---

### Post by Emanuele_Z on 2010-09-28
> **lolzers32 said:**
> Did you check to see if your audio device is connected? That might be the problem.:popcorn::smile::guitar:

Mate, apart that the motherboard audio is always connected, the USB headphones+mic are connected as well...

Anyway, let's see what happens with next kernel...

---

### Post by Mr_VeRiTy on 2010-09-28
> **blueturtl said:**
> Well... you can always [compile the kernel yourself]("http://blog.avirtualhome.com/2010/07/14/how-to-compile-a-ubuntu-2-6-35-kernel-for-lucid/"), even one newer than the one in Maverick. It's a bit of a chore though.

The other alternative is to [try a PPA]("http://ubuntuforums.org/showpost.php?p=9763725&postcount=8") where someone else does the compiling for you (all you have to do is apt-get install the package for the new kernel). However it's a third party replacement for the *kernel* of the entire OS, so keep that in mind. :)

Also make sure, if you use closed-source drivers that there is a compatible package available to the kernel version you're going to try (would be a bummer to have working audio and no video acceleration).

Maverick is due next month, so if you can stand the odd reboot for less than a month, you'll soon get to try a certified and new version of Ubuntu.

edit: Just thought I should say that even if you install third party kernels, you can still fall back to the default Ubuntu kernel if you wish, so in that sense there is no danger in trying. Just hit esc to see the boot menu when starting the computer and select the older kernel.

In Karmic it's esc, in Lucid you have to keep hold of shift during boot.

---

### Post by rafe101 on 2010-11-07
I am also randomly getting no sound with Mythbuntu 10.04. I don't have any problems restarting or any other issues though. Everything works normally except with no sound.

When this happens, and I try and adjust the volume, the volume always says "0". Has anyone figured out what's going on?

---

### Post by strm0 on 2011-03-29
Hello, 

Have you found a sollution ? I have the same problem with Gigabyte motherboard with AMD 785G chipset. I have also updated my bios, but I don't think it is bios related because in 10.04 I have no problems, only after upgrading to 10.10.

---

### Post by Dany XP on 2012-02-19
Same exact problem, X/Ubuntu 11.10, Realtek ALC888. Any suggestions?

---

