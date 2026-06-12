---
title: "Inspiron 1420 no sound through external speakers in Maverick"
date: 2011-01-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mlsquad on 2011-01-02
I have a Dell Inpsiron 1420 laptop running Ubuntu 10.10 Maverick on a fresh install.  I get sound through headphones, if I plug them in, but I cannot get any sound through my external speakers.
I have tried adding the following line in /etc/modprobe.d/alsa-base.conf to no avail.
```
options snd-hda-intel model=dell-m26
```
I'm not really sure where else to go from here.  I have made sure that the volume is all the way up, and not muted, in the sound settings.
The following are the results from lspci.
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

---

### Post by dfrandin on 2011-01-03
I have a Vostro 1400, which is identical to the Insp 1420 and am seeing the same problem myself but in Windows 7 (I dualboot the laptop). The speakers work fine in Ubuntu 10.04, but do not work in Win 7. I can plug headphones in, and the audio is normal in Win 7. Any ideas here??

---

### Post by lidex on 2011-01-05
OK. So the line out doesn't work but headphones do, correct? What about internal speakers? Can you run externals from headphone output?

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by mlsquad on 2011-01-05
> **lidex said:**
> OK. So the line out doesn't work but headphones do, correct? What about internal speakers? Can you run externals from headphone output?

Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

Essentially, if no headphones are plugged in, then I don't have any sound.  If the headphones are plugged in, I can hear sound through the headphones.
I'm not sure how I would redirect the sound to the internal speaker.

Sound initially worked, and stopped working during some version of Ubuntu, though I'm not sure.  I think it was Jaunty when it started not working, and I've more-or-less been living with it since then.

Thank you.  The link is [http://www.alsa-project.org/db/?f=20c54cd0679586b93bb11e2c4c49ac6fb99dbd31](http://www.alsa-project.org/db/?f=20c54cd0679586b93bb11e2c4c49ac6fb99dbd31)
Edit: I'm a moron at 1am, apparently, and ran that script on the wrong computer.  Here's the correct URL. [http://www.alsa-project.org/db/?f=647676eb094407807975700b3dd2d82844f1508f](http://www.alsa-project.org/db/?f=647676eb094407807975700b3dd2d82844f1508f)

---

### Post by lidex on 2011-01-05
Alsa could use an upgrade. Probably simplest to do this:
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by AlexisCC on 2011-01-06
I also have a Dell 1420 and am experiencing sound only through the headphones.  It started after I plugged in external USB/Headphone jack speakers to listen to Christmas Carols--worked fine, the next day after reboot and no sound through laptop speakers.  I lived with it. Then after watching SpongeBob on TV through my laptop-headphone jack to RCA left Right and the video out, mysteriously my sound began working again. Then I reinstalled Maverick, no sound.  Fresh install of Lucid, no sound.  Fresh install of Windows 7 (just to see) no sound.  I'm back using Mint (10) and still no sound. I have been researching this for sometime and have tried many tutorials, when/if I understand the problem I will post what I learn.
Forgive the rant.

---

### Post by lidex on 2011-01-06
Any progress?
Some other model names to try:
```
auto
6stack-dig
6stack-dig-demo
6stack-dell
```

---

### Post by mlsquad on 2011-01-07
I have added the repo and updated and installed as per your instructions.  I have also tried each of the configurations with no love.

---

### Post by AlexisCC on 2011-01-07
I have been following this and other forums closely to see what happens with this.  I believe I am experiencing the same problem.  I have tried everything suggested by Lidex, also to no avail.  Below is my alsa-info script link, I hope this helps.

[http://www.alsa-project.org/db/?f=36decca7492dc62152b7472e867f4b0e4913b27e](http://www.alsa-project.org/db/?f=36decca7492dc62152b7472e867f4b0e4913b27e)

---

### Post by lidex on 2011-01-07
> **AlexisCC said:**
> I have been following this and other forums closely to see what happens with this.  I believe I am experiencing the same problem.  I have tried everything suggested by Lidex, also to no avail.  Below is my alsa-info script link, I hope this helps.

[http://www.alsa-project.org/db/?f=36decca7492dc62152b7472e867f4b0e4913b27e](http://www.alsa-project.org/db/?f=36decca7492dc62152b7472e867f4b0e4913b27e)
Your alsa libs are borked. Try this:

```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

---

### Post by mlsquad on 2011-01-09
Please note that I update the link to the alsa test, as I ran it originally from the wrong computer.

---

### Post by lidex on 2011-01-09
> **mlsquad said:**
> Please note that I update the link to the alsa test, as I ran it originally from the wrong computer.

Well, duh...that might make a difference :)
Anyway, remove whatever you put in alsa-base.conf and reboot. Now check your mixer. Try gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

No joy - here are some models to try - do not add 'positon_fix'
```

  ref		Reference board
  ref-no-jd	Reference board without HP/Mic jack detection
  3stack	D965 3stack
  5stack	D965 5stack + SPDIF
  5stack-no-fp	D965 5stack without front panel
  dell-3stack	Dell Dimension E520
  dell-bios	Fixes with Dell BIOS setup
  volknob	Fixes with volume-knob widget 0x24
  auto		BIOS setup (default)
```

---

### Post by mlsquad on 2011-01-09
No love on any of those models.  The gnome-alsamixer confirms that the sound devices are there and at full volume.

---

### Post by lidex on 2011-01-09
Alsa sees two headphone outs:
```
	control.1 {
                comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -4800
		comment.dbmax 0
		iface MIXER
		name 'Headphone Playback Volume'
		value.0 64
		value.1 64
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		[COLOR="Red"]name 'Headphone Playback Switch'
		value.0 false
		value.1 false[/COLOR]
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -4800
		comment.dbmax 0
		iface MIXER
		name 'Headphone Playback Volume'
		index 1
		value.0 64
		value.1 64
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Headphone Playback Switch'
		index 1
		value.0 true
		value.1 true
	}
```

One of these may be your line out. You'll note the switch for control 2 is off.

---

### Post by reliagility on 2011-02-20
same exact problem here.  Freshly installed Ubuntu 10.10 (32-bit) on a Dell Inspiron 1420.  Followed all suggestions in this thread, but no sound through internal speakers.

My Alsa Script info is here:

[URL="http://www.alsa-project.org/db/?f=0145afcb39214545d9036cbaff0b11f6bf58f8f3"]http://www.alsa-project.org/db/?f=0145afcb39214545d9036cbaff0b11f6bf58f8f3

[/URL] Any help would be appreciated.

---

### Post by lidex on 2011-02-20
> **reliagility said:**
> same exact problem here.  Freshly installed Ubuntu 10.10 (32-bit) on a Dell Inspiron 1420.  Followed all suggestions in this thread, but no sound through internal speakers.

My Alsa Script info is here:

[URL="http://www.alsa-project.org/db/?f=0145afcb39214545d9036cbaff0b11f6bf58f8f3"]http://www.alsa-project.org/db/?f=0145afcb39214545d9036cbaff0b11f6bf58f8f3

[/URL] Any help would be appreciated.

First you should remove the asla-base.conf edit you made. Replace it with one of these lines at a time. Reboot to initialize.
```
options snd-hda-intel model=ref
options snd-hda-intel model=ref-no-jd
options snd-hda-intel model=dell-bios
options snd-hda-intel model=auto
```

---

### Post by reliagility on 2011-02-26
Well, I finally got it to work using the following addition to the alsa-base.conf file:

options snd-hda-intel model=dell-3stack  (a setting I saw on another post).

The funny thing is, that, after changing this setting, and rebooting (multiple times), the internal speakers still did not work.

So, I plugged in my headphones (that was my only way to hear sound), and, then happened to reboot my laptop with the headphones plugged in.  At some point after that, I unplugged my headphones, and noticed that I was getting sound from my internal speakers!  And, they are still working.  I don't know if having the headphones plugged in while rebooting had any causal effect on the fix (seems unlikely), but I thought I'd mention it....

---

