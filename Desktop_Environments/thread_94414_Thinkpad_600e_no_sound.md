---
title: "Thinkpad 600e no sound"
date: 2005-11-24
forum: Desktop Environments
---

### Post by HankB on 2005-11-24
I just installed 5.10 on a Thinkpad 600e and there is no sound. lspci -v reports:

```
0000:00:06.0 Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
        Subsystem: IBM CS4610 SoundFusion Audio Accelerator
        Flags: medium devsel, IRQ 9
        Memory at 50100000 (32-bit, non-prefetchable) [size=4K]
        Memory at 50000000 (32-bit, non-prefetchable) [size=1M]

```
for the sound hardware. This is using kernel 2.6.12.10-386 (and right now I'm downloading the -686 version.)

It looks like the cs46xx driver is the right one for this but it does not work. 
There seem to be a bunch of modules loaded:
```
root@apple:~# lsmod|grep cs46
snd_cs46xx             86088  0
gameport               14824  4 analog,ns558,snd_cs46xx
snd_rawmidi            24704  1 snd_cs46xx
snd_ac97_codec         83932  1 snd_cs46xx
snd_pcm                88840  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd                    54884  8 snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         10600  2 snd_cs46xx,snd_pcm
root@apple:~#


```
aumix reports "no mixer" and dmesg reports:
```
root@apple:~# dmesg | grep cs46
[4294739.861000] ERROR: snd-cs46xx: never read ISV3 & ISV4 from AC'97

```

I had this working with Debian. I'm not sure how to resolve the issue with Ubuntu.

thanks,
hank

---

### Post by grumpymole on 2005-11-24
Hank,

Known problem with the TP600E.  The soundcard is incorrectly identified as CS462x.

There are plenty of web pages out there describing solutions to this.  But here is the Reader's Digest version:

1.  Blacklist the incorrect sound card in /etc/hotplug/blacklist.  Add lines for 

snd-cs46xx
cs46xx

as written above - with the xx's

2.  Add the following lines into /etc/modprobe.d/alsa-base

alias char-major-116 snd
alias char-major-14 soundcore
alias snd-card-0 snd-cs4236
options snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0
alias sound-slot-0 snd-card-0
alias sound-slot-1 snd-card-1

alias sound-service-0-0 snd-mixer-oss
alias sound-service-0-1 snd-seq-oss
alias sound-service-0-3 snd-pcm-oss
alias sound-service-0-8 snd-seq-oss
alias sound-service-0-12 snd-pcm-oss

alias /dev/mixer snd-mixer-oss
alias /dev/dsp snd-pcm-oss
alias /dev/midi snd-seq-oss

options snd cards_limit=1

NOTE: When copying and pasting the above, make sure that the line starting with 'options...' is one line ending with '...dma2=0'.  

3.  Add the line 

snd-cs4236

to the file /etc/modules

Reboot.

Also important: During power up, if you press F2 (I think), you get into change the config.  In this you need to make sure that the Fastboot option is *disabled*.

If you are still having no success: try adding 'acpi=off pnpbois=off' at the end of the kernel boot params.  Press 'esc' during Grub countdown and select 'e' to edit the boot command and add these to the end.  I need these to allow my Xircom PCMCIA ether card to work.

Regards

Warren

---

### Post by grumpymole on 2005-11-24
Edited the line 'NOTE:..' above.  Should be less confusing now.

---

### Post by HankB on 2005-11-25
Yes, Thanks Warren!

That seems to have solved the problem. It's still a little quirky. The volume widget on the top menu panel shows a red "X" indicating a problem, but as soon as I run 'aumix' to set volume, that goes away. And I can play music with 'mpg321' which is where I want to get with this.

thanks again,
hank

---

### Post by poptones on 2005-11-25
The thinkpad onboard resources need to be properly configured. 

[http://tpctl.sourceforge.net/configure-thinkpad.html](http://tpctl.sourceforge.net/configure-thinkpad.html)

I've installed linux on dozens of these and it works like a champ.

---

### Post by grman3 on 2006-01-01
i am haing the same problem with my sound. i have tried to follow the directions that were posted but i am very new to this. this is my first time with linux. the only question i have is when you say "When copying and pasting the above, make sure that the line starting with 'options...' is one line ending with '...dma2=0'."
do you mean this should be one line "options snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0"  
or add it to this line "options snd cards_limit=1"

sorry for the question but like i said this is my first time with linux.

~jonathan

---

### Post by grumpymole on 2006-01-02
Jonathan,

Only refers to this line: "options snd-cs4236 isapnp=0 cport=0x538 port=0x530 sb_port=0x220 fm_port=0x388 irq=5 dma1=1 dma2=0".

Sorry for the confusion, but I just wanted to make sure that when you cut and paste this one long line, that it doesn't get chopped in half.

Otherwise, feel free to ask any more questions.

Regards

Warren

---

### Post by grman3 on 2006-01-02
ok on now that i have every thing set the way you said it should be I still have no sound. at startup when i log in i get an error saying

 "sound server informaion message: error while initializing sound driver: device /dev/dsp cant be opened (no such file or directory) The sound sever will continue, using the null output device." 

are there other settings i need to change.

~jonathan

---

### Post by grumpymole on 2006-01-03
Jonathan,

I have seen other peoplpe with this problem (not only with 600e), but I have not had to deal with it myself.

From reading a few other posts, check that /dev/dsp exists.  If it does, then it may be a permissions problem.

I will search around a bit more myself.

Regards

Warren

---

### Post by grman3 on 2006-01-03
I have looked for /dev/dsp and it is not there. i dont know if it's a permission problem because I am making all changes as root. Do you know if this is a file that needs to be made and if so how.

~Jonathan

---

### Post by grumpymole on 2006-01-08
One option is to create this yourself.   See instructions  [here]("http://lists.debian.org/debian-user/2000/06/msg00953.html").

Also, you have definitely disabled the Fastboot option in the BIOS?

Regards

Warren

---

### Post by becatlibra on 2006-03-08
oops

---

### Post by becatlibra on 2006-03-08
I'll start out by saying I'm not new to linux.  I have been a user for around 8 years and manage a few linux servers at my office.  I have used many distros and currently am using debian, slackware and rh9.  I wanted to give my wife my old thinkpad 600e (which I had slackware on) and thought I'd put ubuntu on it.  I liked the look and thought it might be easier for her to use.

I have been trying for 2 days to get the sound going (and I thought the pain would be the wireless PCMCIA card.)  I have made it work before in RH9 and slackware.  I can't seem to get it going here.

I tried the blacklist/alsa-base mod without any real results.  The volume icon in the 'systray' does not have an x through it but the sound does not function (testing with an audio cd.)  The System>Pref>Multimedia Sys Select tells me "Failed to construct test pipeline for '<insert soundsystem name here>'"  I have tried ESD,OSS and Alsa.  Currently I have the setup suggested where I have blacklisted and then modified alsa-base.  I have pnpbios=no acpi=off and pci=noacpi in my menu.lst The acpi was set to force due to someone elses suggestion.

I can't afford to spend any more work hours on this and I can't surprise her if I work on it at home.

SOMEONE PLEASE help.  I can post ANY info requested.

Regards,

Benjamin

---

