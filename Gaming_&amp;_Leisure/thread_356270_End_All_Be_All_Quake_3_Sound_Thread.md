---
title: "End All Be All Quake 3 Sound Thread"
date: 2007-02-08
forum: Gaming &amp; Leisure
---

### Post by ghandi69_ on 2007-02-08
Hi All,

I've been trying to get sound to work in quake 3 for about the past 3 days with no luck.  I have tried all of the following known solutions on this forum..  I'll explain in a little more detail.  The error when starting the game shows up in the terminal as 

> Could not mmap dma buffer PROT_WRITE|PROT_READ
trying mmap PROT_WRITE (with associated better compatibility / less performance code)
/dev/dsp: Input/output error
Could not mmap /dev/dsp


This does not stop the game from being playbale.. you just can't hear anything.  I have tried the following steps

> sudo echo "guake3.x86 0 0 direct > /usr/local/card0/pcm0p/oss

note also.. I usually just go in and edit the oss file manually, and I also do the same command with disable instead of direct in the pcm0c oss file.  I have no idea why to do this, but when run, quake 3 will start up with sound. but will crash usually as soon as the skirmish is started.

I have also tried going to my ~/.q3/baseq3/q3.confile file or whatever and changing my

seta snddevice = "/dev/dsp"

to dsp0, dsp1, dsp2, adsp0, adsp1, adsp2.. and so on..

this fix for me appears to have no effect.

There is also a method I have found in these forums for installing 3rd party binaries that fixes the issue.  But then you lose internet community gaming support...

Now, on to the possible fix... apparently 

> f anyone's interested, the solution was to add -fno-stack-protector to the CFLAGS variable in the Joss makefile and recompile it.

except.. I do not know how to do this.. could someone give me instructions for how to do this last step?  Thanks!

---

### Post by tribaal on 2007-02-08
Don't know if it'll solve your issue here, but I have sound working in quake 3 only if I issue the following command before running the game:

```
sudo killall esd
```

Hope this helps.

- trib'

---

### Post by ghandi69_ on 2007-02-08
Shucks.. Yep. I've tried that too... however. when I run that it says..

no processes were stopped....

or something like that... maybe thats a hint as to whats going wrong?

(sorry about the double thread)

---

### Post by pharcyde on 2007-02-08
You can try running quake3 using the joss sound wrapper.  A lot of people have had success using it. Check it out here [http://www.craknet.net/joss/](http://www.craknet.net/joss/)

---

### Post by ghandi69_ on 2007-02-10
Hey guys.. just wondering if anyone has a sure answer for gettting quake 3 sound to work.

I have one question.. I have looked into using IOquake3 .. and am willing to sacrifice online play for sound.. but I ran the .sh and installed fine but can't get it to run.. is there a useful HOWTO for installing IOquake3 outhere?

---

### Post by Sidster on 2007-02-12
Hi there

Could I ask what hardware you have? I'm have the same problem and was wondering if it could be related to hardware.

I also haven't been able to figure it out. :confused:

---

### Post by ghandi69_ on 2007-02-13
Hey, sorry for the late response...

I have a GIGABYTE GA-K8N-SLI Socket 939 NVIDIA nForce4 SLI ATX AMD Motherboard, which has built in audio.  I think the problem has been common for people who do not have a seperate sound car from what I can tell.....

Wondering.. is this a problem with all id games?  so if I try to play doom3 I can expect the same results.

---

### Post by Sidster on 2007-02-19
I don't think Doom 3 will be a problem. I've installed it and it works perfectly. Same with Quake 4.

I think our problem comes down to the onboard audio chipset. I have the exact same chipset as you. Only difference is I have an Asus A8N Sli deluxe nForce4 mobo. I had a look at the Asus and Gigabyte websites. The two Mobo's have the same audio controller: Realtek ALC850

I would imagine that this can be one of two problems. Either it's the audio driver or it's a bug in the game. I'm gonna test my theory by trying to get an earlier version of the game installer ie: something pre 1.32b

Anyway, it could be that the same bug exists in previous versions of the game as well. In that case we'll have to either wait for a new version of the installer or try to contact id and let them know about the problem.

Just to back my theory up...

I've installed Quake 3 on machines with different audio controllers, my Compaq Evo n610c laptop for example, and it works fine. However on both the nForce4 mobo's I have at home (Yes I have two, one's an Asus the other's a Gigabyte :) ) the audio refuses to play.

In any event, all this probably means we won't see Quake 3 sound on nForce4 mobo's any time soon :(

---

### Post by Sidster on 2007-02-28
I found something of interest in the one of the documents that come with the source ALSA drivers. For those you don't know, ALSA is responsible for making most soundcards work on linux.

Anyway here's what I found in a file called "OSS-Emulation" in the latest (1.0.13) audio drivers from ALSA:

> PCM Mode
========

As default, ALSA emulates the OSS PCM with so-called plugin layer,
i.e. tries to convert the sample format, rate or channels
automatically when the card doesn't support it natively.
This will lead to some problems for some applications like quake or
wine, especially if they use the card only in the MMAP mode.

In such a case, you can change the behavior of PCM per application by
writing a command to the proc file.  There is a proc file for each PCM
stream, /proc/asound/cardX/pcmY[cp]/oss, where X is the card number
(zero-based), Y the PCM device number (zero-based), and 'p' is for
playback and 'c' for capture, respectively.  Note that this proc file
exists only after snd-pcm-oss module is loaded.

The command sequence has the following syntax:

	app_name fragments fragment_size [options]

app_name is the name of application with (higher priority) or without
path.
fragments specifies the number of fragments or zero if no specific
number is given.
fragment_size is the size of fragment in bytes or zero if not given.
options is the optional parameters.  The following options are
available:

	disable		the application tries to open a pcm device for
			this channel but does not want to use it.
	direct		don't use plugins
	block		force block open mode
	non-block	force non-block open mode
	partial-frag	write also partial fragments (affects playback only)
	no-silence	do not fill silence ahead to avoid clicks

The disable option is useful when one stream direction (playback or
capture) is not handled correctly by the application although the
hardware itself does support both directions.
The direct option is used, as mentioned above, to bypass the automatic
conversion and useful for MMAP-applications.
For example, to playback the first PCM device without plugins for
quake, send a command via echo like the following:

	% echo "quake 0 0 direct" > /proc/asound/card0/pcm0p/oss

While quake wants only playback, you may append the second command
to notify driver that only this direction is about to be allocated:

	% echo "quake 0 0 disable" > /proc/asound/card0/pcm0c/oss

The permission of proc files depend on the module options of snd.
As default it's set as root, so you'll likely need to be superuser for
sending the command above.

The block and non-block options are used to change the behavior of
opening the device file.

As default, ALSA behaves as original OSS drivers, i.e. does not block
the file when it's busy. The -EBUSY error is returned in this case.

This blocking behavior can be changed globally via nonblock_open
module option of snd-pcm-oss.  For using the blocking mode as default
for OSS devices, define like the following:

	options snd-pcm-oss nonblock_open=0

The partial-frag and no-silence commands have been added recently.
Both commands are for optimization use only.  The former command
specifies to invoke the write transfer only when the whole fragment is
filled.  The latter stops writing the silence data ahead
automatically.  Both are disabled as default.

You can check the currently defined configuration by reading the proc
file.  The read image can be sent to the proc file again, hence you
can save the current configuration

	% cat /proc/asound/card0/pcm0p/oss > /somewhere/oss-cfg

and restore it like

	% cat /somewhere/oss-cfg > /proc/asound/card0/pcm0p/oss

Also, for clearing all the current configuration, send "erase" command
as below:

	% echo "erase" > /proc/asound/card0/pcm0p/oss



Seems like there is a workaround but I'm nowhere near competent enough to know where to begin. :confused:  Any help pointing me in the right direction would be muchly appreciated. :)

---

