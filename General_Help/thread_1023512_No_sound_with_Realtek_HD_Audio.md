---
title: "No sound with Realtek HD Audio"
date: 2008-12-28
forum: General Help
---

### Post by Guticb on 2008-12-28
2 things to get out of the way first.

1) I'm a COMPLETE Linux noob. I had a spare hard drive and installed Ubuntu on it and am getting very upset.
2) I started with 8.04 and didn't have sound either, on 8.10 now

That basically sums it up though. I've tried googling it and have installed Realtek's Linux driver for it but with zero luck, and I have found people that had the same issue and fixed it and provided instructions that I'd swear were in another language.

I'm seriously thinking installing Ubuntu was a huge mistake and I should have gone with some other version of Linux. =/

Someone please help me get this stupid sound working. >_>

---

### Post by ITAndrew on 2008-12-28
I guess obvious question would be is this a new PC build, or have you had another OS on this system that has had sound before? What motherboard or sound card are you using?

Also, you may want to see if ubuntu is even recognising your audio hardware. Easy way to check would be to type "lspci" (w/o quotes) and see what your output is. You also may want to post this output here as well.

---

### Post by Guticb on 2008-12-28
> **ITAndrew said:**
> I guess obvious question would be is this a new PC build, or have you had another OS on this system that has had sound before? What motherboard or sound card are you using?

Also, you may want to see if ubuntu is even recognising your audio hardware. Easy way to check would be to type "lspci" (w/o quotes) and see what your output is. You also may want to post this output here as well.

Nah, I built this PC a while back. I've got 2 hard drives, one is running Vista flawlessly and one has Ubuntu on it.

Some basic specs:
Intel Q6600
Gigabyte GA-965p-DS3 motherboard
4GB DDR2 ram (2GB Corsair, 2 Supertalent. Newegg sold out of Corsair so i asked for the Supertalent because I"d already paid for 2 anyways)
Sapphire X1950XT

Here's what lspci popped up:

bojan@Ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc R580 [Radeon X1900]
01:00.1 Display controller: ATI Technologies Inc Device 7264
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
05:01.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)
bojan@Ubuntu:~$

---

### Post by ITAndrew on 2008-12-28
Unfortunatly I am away from my ubuntu box so I cant really test my own advice beforehand so you will have to excuse me if I am inaccurate.

Have you checked System > Prefrences > Sound? Are the top few devices set to Autodetect? You may want to try changing the output devices, the autodetect option may not have worked...it can happen. Also you may want to run via terminal
> alsamixer
to check for any muted channels. PCM will also need to be unmuted and turned up.

---

### Post by Guticb on 2008-12-28
> **ITAndrew said:**
> Unfortunatly I am away from my ubuntu box so I cant really test my own advice beforehand so you will have to excuse me if I am inaccurate.

Have you checked System > Prefrences > Sound? Are the top few devices set to Autodetect? You may want to try changing the output devices, the autodetect option may not have worked...it can happen. Also you may want to run via terminal

to check for any muted channels. PCM will also need to be unmuted and turned up.

I've tried every option in sound preferences with no luck. =/

I opened ALsamixer but what do I do there? The only thing it lets me do is turn the volume up and down but that doesn't do anything when I don't have sound.

---

### Post by Zorael on 2008-12-28
Have a look at [http://tinyurl.com/alsamodels](http://tinyurl.com/alsamodels) and see if anything applies.

---

### Post by Guticb on 2008-12-28
> **Zorael said:**
> Have a look at [http://tinyurl.com/alsamodels](http://tinyurl.com/alsamodels) and see if anything applies.

No luck at all. =/

---

### Post by Zorael on 2008-12-29
Well, we'd need more information than that. Output of the following?
```
$ lshw -C multimedia
$ aplay -l
```
Run the following and make sure to unmute channels (sliders with MM are muted, 00 are unmuted).
```
$ alsa-mixer
$ alsa-mixer -Dhw
```
Run the following to test.
```
$ speaker-test -twav -c2
```

---

### Post by Guticb on 2009-01-07
bojan@Ubuntu:~$ lshw -Cmultimedia
Hardware Lister (lshw) - B.02.13
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.13)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-c CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
	-numeric        output numeric IDs (for PCI, USB, etc.)

bojan@Ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
bojan@Ubuntu:~$ 


Alsa mixer gets me a command not found:

bojan@Ubuntu:~$ alsa-mixer
bash: alsa-mixer: command not found
bojan@Ubuntu:~$ alsa-mixer -Dhw
bash: alsa-mixer: command not found

Speaker test got me this:

bojan@Ubuntu:~$ speaker-test -twav -c2

speaker-test 1.0.17

Playback device is default
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 96 to 1048576
Period size range from 32 to 349526
Using max buffer size 1048576
Periods = 4
was set period_size = 262144
was set buffer_size = 1048576
 0 - Front Left
 1 - Front Right
Time per period = 3.032729
 0 - Front Left
 1 - Front Right
Time per period = 3.026556
 0 - Front Left
 1 - Front Right
Time per period = 3.017102
 0 - Front Left
 1 - Front Right
Time per period = 3.017202
 0 - Front Left
 1 - Front Right
Time per period = 3.017606
 0 - Front Left
 1 - Front Right
Time per period = 3.016879
 0 - Front Left
 1 - Front Right
Time per period = 3.017295
 0 - Front Left
 1 - Front Right
Time per period = 3.017574
 0 - Front Left
 1 - Front Right
Time per period = 3.016828
 0 - Front Left
 1 - Front Right
Time per period = 3.017237
 0 - Front Left
 1 - Front Right
Time per period = 3.017229
 0 - Front Left
 1 - Front Right
Time per period = 3.017329
 0 - Front Left
 1 - Front Right



It kept going on and on and on. >_>

I'm seriously considering giving up on Linux. Linux for people? I prefer a simple install and use instantly interface, something Ubuntu is majorly lacking for me. Honestly, Vista has given me less problems than Ubuntu, and I've had Vista since launch.....

I might just try another Linux type. Or better yet, I could just try the Windows 7 beta?

---

### Post by bhanja_Trinanjan on 2009-07-21
Me in the same boat buddy... Vista runs rock solid with ZERO ISSUES, Ubuntu gives me no sound out of the box. My Canon MP450 wouldn't print.... pop a DVD movie into the drive and it will throw some permission error!

WTF... Linux has a loooong way to go... go figure! :mad:

---

