---
title: "Sound card not detected"
date: 2005-04-01
forum: Desktop Environments
---

### Post by spencer on 2005-04-01
Hello,  I have an old Dell Optiplex PIII 450 Mhz 320MB ram and would like to install "Kubuntu" on it. While Running From the live CD it does not detect the sound card. So, before I install, am I able to fix this or is this computer's sound card not supported? Thanks.

-spencer

---

### Post by cwaldbieser on 2005-04-01
What kind of sound card is it?

---

### Post by spencer on 2005-04-01
Hi, Sound card is Crystal WDM Audio System. Ubuntu recognizes soundcard but not Kubuntu and I would like to install Kubuntu. Gnome desktop seems to bog down this old machine compared to KDE. Maybe with next week's release it'll work. Thanks.

-spencer

---

### Post by moopere on 2005-04-02
> Hi, Sound card is Crystal WDM Audio System

This does not tell us what the sound card is - the WDM bit means "Windows driver Model".  Sounds like the description coming from Windows 2K+ in hardware manager.

Why not go to the Dell website and have a look at the specs for your machine?


>Ubuntu recognizes soundcard but not Kubuntu

Does this mean that the live CD for ubuntu recognises your audio cardbut the kubuntu live CD doesn't?  Or does it mean that you've installed ubuntu + kde (kubuntu) and booting into gnome gives you sound but booting into kubuntu doesnt?

Cheers,
Craig

---

### Post by spencer on 2005-04-02
Didn't find anything on Dell site.  I'll try here again.  Sound card is:  cs4236B:wss /SB. If this is incorrect I'll try again.

-spencer

---

### Post by cwaldbieser on 2005-04-02
I found this link on Dell's site:

[http://support.dell.com/support/topics/global.aspx/support/kb/en/document?dn=1040187&c=us&l=en&s=gen&cs=](http://support.dell.com/support/topics/global.aspx/support/kb/en/document?dn=1040187&c=us&l=en&s=gen&cs=)

It applies to Red Hat (I didn't find the sndconfig program they mention on my Ubuntu system), but it may help someone else to help you out.  The sound driver level of any given *NIX system is still somewhat of a mystery to me.

I checked the Cirrus Logic site, too, as it seems they are the ones who manufacture the card, but the only thing I could find were dates they discontinued production of various models of that card.

---

### Post by Whiffle on 2005-04-02
The easiest way to find out which card it is it to run lspci in a terminal.  It should show up there somewhere.

this is what the line for mine looks like:

```
0000:00:09.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24 [CrystalClear SoundFusion Audio Accelerator] (rev 01
``` 

Which is a Turtle Beach Santa Cruz.

---

### Post by spencer on 2005-04-02
Thanks for the help. Did a lspci in terminal and returned the following:

0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0e.0 Communication controller: Motorola: Unknown device 5608
0000:00:0f.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03)
0000:00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)

Don't know which is the souncard.

-spencer

---

### Post by Whiffle on 2005-04-02
[QUOTE=spencer]Thanks for the help. Did a lspci in terminal and returned the following:

0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0e.0 Communication controller: Motorola: Unknown device 5608
0000:00:0f.0 PCI bridge: Digital Equipment Corporation DECchip 21152 (rev 03)
0000:00:11.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 24)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage Pro AGP 1X/2X (rev 5c)

Don't know which is the souncard.

-spencer[/QUOTE]
 hmph, I don't see a soundcard either.  I'm guessing thats why you don't have any sound :D   I'd start googling around, it may be that sound card isn't linux compatable, which is odd.  I'd start by looking up the computer model and going from there...

---

### Post by spencer on 2005-04-03
Thanks. I'll do some more searching and report back later. I sure would like to give Kubuntu a go, I like what I see so far. 8) 

-spencer

---

### Post by moopere on 2005-04-03
From your previous message:


>cs4236B

 I presume you got this information from the Dell website? 

Anyway, its the key info we need to help you out.  This tells us that yes, as suspected its a Crystal based sound chip - more importantly though it tells us that although its doubtless built into the motherboard of your Dell its attached to the ISA bus.

This explains why it won't show up when you do an "lspci".

Try this from a command prompt:

modprobe snd-cs4236

If u don't get any errors it probably means that its loaded the module successfully.  Have a look at the output from lsmod to tell for sure - there should be a whole pile of junk relating to sound in the listing.

Now do this: apt-get install esound-clients

This will help you to debug stuff later (below) by allowing you to play sound from a command line even though X is probably running and hogging the soundcard via esd.

Next thing to try (still from the command line of a virtual terminal) esdplay /usr/share/sounds/startup3.wav

You should hear the rather cool sounding ubuntu startup music.

If this is all good so far you will want to make sure your sound module is loaded upon startup.  To do this modify the file /etc/modules by putting "snd-cs4236" at the bottom (don't use the quotes of course).

That should be it.  I've never had a problem with KDE picking up the sound daemon being used if you leave the kde sound system on 'auto'.

Cheers,
Craig

---

### Post by spencer on 2005-04-10
Hello, I've been out and about and am now back in business. I decided to install ubuntu on hard disk rather than kubuntu. I Have problem with sound in ubuntu too. I thought ubuntu recognized sound card using the live CD last time. I was wrong. I completed all the suggested steps and still have no sound. I tried modifying the /etc/modules but I don't know how to change over to root to change permissions. So I haven't been able to go any further. How do I log in as root? thanks. 

-spencer

---

### Post by moopere on 2005-04-10
>I completed all the suggested steps and still have no sound.

Really?

You did as I suggested above and tried modprobe snd-cs4236 and that didn't work?

The reason I'm so surprised is that I've got a really similar machine to you at work and this method works just fine for the Dell motherboard based Crystal 4236 soundcard that I have (actually I have two of them, both SMP Dell's both with cs4236).

What happens when you do the above?  Anything in the logs?  Anything coming up as an error on the terminal you're trying this from?

Craig

---

### Post by spencer on 2005-04-10
-modprobe snd-cs4236 command returns the following results:

WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-page-alloc.ko): Operation not permitted
WARNING: Error inserting soundcore (/lib/modules/2.6.10-5-386/kernel/sound/soundcore.ko): Operation not permitted
WARNING: Error inserting snd (/lib/modules/2.6.10-5-386/kernel/sound/core/snd.ko): Operation not permitted
WARNING: Error inserting snd_timer (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-timer.ko): Operation not permitted
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-page-alloc.ko): Operation not permitted
WARNING: Error inserting soundcore (/lib/modules/2.6.10-5-386/kernel/sound/soundcore.ko): Operation not permitted
WARNING: Error inserting snd (/lib/modules/2.6.10-5-386/kernel/sound/core/snd.ko): Operation not permitted
WARNING: Error inserting snd_timer (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-timer.ko): Operation not permitted
FATAL: Error inserting snd_pcm (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-pcm.ko): Operation not permitted
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_cs4231_lib (/lib/modules/2.6.10-5-386/kernel/sound/isa/cs423x/snd-cs4231-lib.ko): Operation not permitted
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.10-5-386/kernel/sound/core/seq/snd-seq-device.ko): Operation not permitted
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-rawmidi.ko): Operation not permitted
WARNING: Error inserting snd_mpu401_uart (/lib/modules/2.6.10-5-386/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko): Operation not permitted
WARNING: Error inserting snd_cs4236_lib (/lib/modules/2.6.10-5-386/kernel/sound/isa/cs423x/snd-cs4236-lib.ko): Operation not permitted
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-hwdep.ko): Operation not permitted
WARNING: Error inserting snd_opl3_lib (/lib/modules/2.6.10-5-386/kernel/sound/drivers/opl3/snd-opl3-lib.ko): Operation not permitted
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-page-alloc.ko): Operation not permitted
WARNING: Error inserting soundcore (/lib/modules/2.6.10-5-386/kernel/sound/soundcore.ko): Operation not permitted
WARNING: Error inserting snd (/lib/modules/2.6.10-5-386/kernel/sound/core/snd.ko): Operation not permitted
WARNING: Error inserting snd_timer (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-timer.ko): Operation not permitted
WARNING: Error inserting snd_page_alloc (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-page-alloc.ko): Operation not permitted
WARNING: Error inserting soundcore (/lib/modules/2.6.10-5-386/kernel/sound/soundcore.ko): Operation not permitted
WARNING: Error inserting snd (/lib/modules/2.6.10-5-386/kernel/sound/core/snd.ko): Operation not permitted
WARNING: Error inserting snd_timer (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-timer.ko): Operation not permitted
FATAL: Error inserting snd_pcm (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-pcm.ko): Operation not permitted
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_cs4231_lib (/lib/modules/2.6.10-5-386/kernel/sound/isa/cs423x/snd-cs4231-lib.ko): Operation not permitted
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.10-5-386/kernel/sound/core/seq/snd-seq-device.ko): Operation not permitted
WARNING: Error inserting snd_rawmidi (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-rawmidi.ko): Operation not permitted
WARNING: Error inserting snd_mpu401_uart (/lib/modules/2.6.10-5-386/kernel/sound/drivers/mpu401/snd-mpu401-uart.ko): Operation not permitted
WARNING: Error inserting snd_cs4236_lib (/lib/modules/2.6.10-5-386/kernel/sound/isa/cs423x/snd-cs4236-lib.ko): Operation not permitted
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.10-5-386/kernel/sound/core/snd-hwdep.ko): Operation not permitted
WARNING: Error inserting snd_opl3_lib (/lib/modules/2.6.10-5-386/kernel/sound/drivers/opl3/snd-opl3-lib.ko): Operation not permitted
FATAL: Error inserting snd_cs4236 (/lib/modules/2.6.10-5-386/kernel/sound/isa/cs423x/snd-cs4236.ko): Operation not permitted
FATAL: Error running install command for snd_cs4236



Thanks.

-spencer

---

### Post by Ozitraveller on 2005-04-10
I've just done clean install with Hoary 5.04. I had Hoary installed before and sound was working. I have a SoundBlaster ViBRA16x PnP (CT4170).
I've tried 

sudo modprobe sb
and
sudo modprobe snd-sb16

and neither produce errors, and I still have no sound.

Is there a sound card that just works out of the box?

Cheers!

---

### Post by scotty on 2005-04-10
I too am in the same boat that spencer is in. My sound does not work under Linux but works just dandy under Win98.  I KNOW that the card is an OPLSA3 based card under Linux as I once had Redhat going on this Toshiba model laptop.

It's an older 4005CDS model with a PII under the hood, but a custom install of Ubuntu works great.

How can I get sound working myself?

Thanks!
Scott

---

### Post by spencer on 2005-04-11
I managed to get sound working but only in root. Not sure which one of the commands worked. I think it was the sudo "modprobe cs-4236" command. I was never able to hear the "esdplay /usr/share/sounds/startup3.wav" though. the terminal showed it working I just didn't hear anything. There is now a volume icon next to date/time in menu bar. Cd's play and video works but with no sound. :-? I'll keep searching some more. Thanks.

-spencer

---

### Post by spencer on 2005-04-11
I just added xmms player to Ubuntu and it plays CD. Why do I get sound from xmms player and not with CD Player or Real Player? Any suggestions? Thanks.

-spencer

---

### Post by spencer on 2005-04-12
Hello,

I've checked this entire forum and have read for hours, even googled the entire universe. At least a week solid. I've tried all suggestions and still, I'm stuck. It must be something simple I have overlooked; as it seems I should have sound in other apps after all the suggestions that have been made. I do, but only with xmms player playing CD. There is no sound with default cd player app. There is no sound using Real player or any  other computer sounds. The Volume control preference is using the OSS Mixer. No luck using Alsa mixer either. 

During boot up when the Modules load there is a loud pop out of my external speakers. Anyone else have this experience? Anyway:
ubuntu performs pretty good on this machine. The sound issue is my only obstacle, at least for now. That's pretty good. :wink:   Thanks.

-spencer

---

### Post by Klin'Targ on 2005-04-12
spencer,
Judging by the error message you posted above, you simply needed to use sudo to load the module.
Run```
sudo modprobe snd-cs4236
``` and type in your password when prompted to do so.
Log out and back into your graphical environment and see if sound works. If it does, you should add the module to the autoload list so it will load every boot.
To do this, run this command:```
sudo echo "snd-cs4236" >> /etc/modules
```

---

### Post by spencer on 2005-04-12
Hello,

It is loaded and I've also added "snd-cs4236" to the /etc/modules file. It is very strange why I still have no sound except xmms playing CD. Thanks for your help. :wink: 

-spencer

---

### Post by spencer on 2005-04-21
[QUOTE=moopere]From your previous message:


>cs4236B

 I presume you got this information from the Dell website? 

Anyway, its the key info we need to help you out.  This tells us that yes, as suspected its a Crystal based sound chip - more importantly though it tells us that although its doubtless built into the motherboard of your Dell its attached to the ISA bus.

This explains why it won't show up when you do an "lspci".

Try this from a command prompt:

modprobe snd-cs4236

If u don't get any errors it probably means that its loaded the module successfully.  Have a look at the output from lsmod to tell for sure - there should be a whole pile of junk relating to sound in the listing.

Now do this: apt-get install esound-clients

This will help you to debug stuff later (below) by allowing you to play sound from a command line even though X is probably running and hogging the soundcard via esd.

Next thing to try (still from the command line of a virtual terminal) esdplay /usr/share/sounds/startup3.wav

You should hear the rather cool sounding ubuntu startup music.

If this is all good so far you will want to make sure your sound module is loaded upon startup.  To do this modify the file /etc/modules by putting "snd-cs4236" at the bottom (don't use the quotes of course).

That should be it.  I've never had a problem with KDE picking up the sound daemon being used if you leave the kde sound system on 'auto'.

Cheers,
Craig[/QUOTE]



Craig,

It's been awhile and wanted to let you know  I finally figured out why I had no sound. I followed all your steps except this time I ran "alsamixer" in terminal before testing the .wav file and the master volume in "alsamixer" was off. So, I turned the volume up, ran the .wav file and I had sound. :-)  If anyone else has a similar problem, these steps do work. Thank you very much.

-spencer

---

### Post by steen on 2006-10-21
Sorry to dredge this ancient thread up, but I've just come across this exact problem with Ubuntu 6.0.6.1 on a bunch of Gateway E-3200 P3-850s. These are essentially the same hardware as the OP's Dell. I had assumed it was the PnP ISA CS4235 ALSA driver not loading. Just type "sudo gedit /etc/modules" & append "snd-cs4236" to the bottom. Save, exit, then re-start. These old systems run surprisingly OK with 384MB SDRAM...

---

