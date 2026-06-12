---
title: "Added 1GB RAM: volume control (sound) doesn't work"
date: 2009-02-12
forum: Desktop Environments
---

### Post by lotuseclat79 on 2009-02-12
I see a red symbol over the volume control in my Ubuntu Live CD (8.10) environment after changing RAM from 2 x 512MB chips to 2 x 1GB chips which prohibits any volume control, and the sound feedback for ubuntu login countdown does not occur on Live CD bootup.

My sound card is a Soundblaster which worked fine with 1GB of RAM.

I get the following message window when I try to left-click Open Volume Control:  No volume control or GStreamer plugins and/or devices found.

My Award BIOS automatically detected the new memory.

Is this a bug with the Live CD?

Do I simply need to install gstreamer plugins?  While that may solve the current volume control problem after bootup, I don't see how it will help a Live CD that does not have the plugin at bootup time for the ubuntu login bongo beat sound count down of 10 seconds.

-- Tom

---

### Post by ddmdllt on 2009-02-12
Hi,

Could you try alsamixer in text mode?

---

### Post by lotuseclat79 on 2009-02-13
> **ddmdllt said:**
> Hi,

Could you try alsamixer in text mode?
Hi ddmdllt,

alsamixer execution got message: No mixer elems found

I suspect the sound driver's location in memory may have changed and cannot be resolved, e.g. when I load a music CD on my CD drive, and launch the Rhythmbox music player, the gray shade over the application occurs and I use Force Quit to exit.

-- Tom

P.S.  Synaptic Package Manager says GStreamer (gstreamer0.10-alsa + 8 other gstreamer related packages are installed in the Live CD environment, including plugins: -base, -good, and -base-apps).

---

### Post by ddmdllt on 2009-02-13
> **lotuseclat79 said:**
> 
alsamixer execution got message: No mixer elems found


So, it's sure it's more than just a problem with the graphical tool.

> **lotuseclat79 said:**
> 
I suspect the sound driver's location in memory may have changed and cannot be resolved


I have serious doubts about it.

Are you able to revert your hardware modification (if you still have your old RAM) and test if the problem really disappears by doing so? (testing exactly with the same LiveCD)

> **lotuseclat79 said:**
> 
when I load a music CD on my CD drive,


Just being curious, you didn't removed the LiveCD after the boot process? (I suppose you have 2 CD/DVD drives)

---

### Post by lotuseclat79 on 2009-02-13
> **ddmdllt said:**
> 
...
Are you able to revert your hardware modification (if you still have your old RAM) and test if the problem really disappears by doing so? (testing exactly with the same LiveCD)

Just being curious, you didn't removed the LiveCD after the boot process? (I suppose you have 2 CD/DVD drives)
Hi ddmdllt,

Yes, I do have two CD/DVD drives, and the Live CD stays in the primary bootable drive for the duration of the session.

After reading last night's exchange, I thought I might collect data with the current setup and label the files with suffix (.2gb), then revert back to the 1GB RAM and collect the setup labeled (.1gb).  However, it appears that with this mornings bootup w/2GB, the problem has gone away.

I did check the BIOS w/o changing anything, and it does look like I have to change the CL settings as the 1GB memory was CL=4, and the 2GB is CL=5.  Also, I believe the frequency of RAM was 533 MHz with the 1GB RAM, and with 2GB it is 800 MHz - and those changes to the BIOS should finalize the RAM modification.

The volume icon control appears to be working ok now.  I have no idea what was causing this problem, as long as it does not reappear.

-- Tom

---

### Post by ddmdllt on 2009-02-13
If you haven't done it yet, it may be a good idea to check your new memory with memtest86+ during a long time (during the night, or whenever you don't use your computer).

Memory problems and hardware problems in general may have consequences that are not always easy to understand.

---

### Post by syms on 2009-02-13
try to change ram socket place.

---

