---
title: "Inspiron 6000 sound issues"
date: 2007-11-22
forum: Dell  Ubuntu Support
---

### Post by wormser on 2007-11-22
I do not have sound with my speakers but there is sound with a headset. This is a fresh install of Gusty 7.10.  Sound worked fine in Feisty.  

uname -a
> Linux computer 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

lspci
> 00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)

aplay -l
> **** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [Intel ICH6 Modem], device 0: Intel ICH - Modem [Intel ICH6 Modem - Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


cat /proc/asound/cards
>  0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with STAC9752,53 at irq 16
 1 [Modem          ]: ICH-MODEM - Intel ICH6 Modem
                      Intel ICH6 Modem at irq 18

> [AlsaMixer v1.0.14 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; Card: Intel ICH6 &#9474;
&#9474; Chip: SigmaTel STAC9752,53 &#9474;
&#9474; View: [Playback] Capture All &#9474;
&#9474; Item: Master [dB gain=-33.00, -33.00]

I tried to provide as much info as possible because I am going to take off soon and will check back later.  Thanks.

---

### Post by derby007 on 2007-11-23
May sound stupid, but....are the speakers plugged into the right socket ('sound-out') of your sound card. Maybe something is muted in Alsamixer, master, or surround or similar. Maybe you've tried this already...

---

### Post by wormser on 2007-11-23
> **derby007 said:**
> May sound stupid, but....are the speakers plugged into the right socket ('sound-out') of your sound card. Maybe something is muted in Alsamixer, master, or surround or similar. Maybe you've tried this already...

The Inspiron 6000 is a laptop so there is nothing to plug in.  In alsamixer everything looks fine but there is only a "PC Speak" and no head phones to adjust.

Are there any other Inspiron 6000 users out there with working sound?  Other threads I have found talked about adding a line to the end of /etc/modprobe.d/alsa-base.  If you have a working 6000 post the last line of this command **gksudo gedit /etc/modprobe.d/alsa-base**

Any other ideas?

---

### Post by Skuzniak on 2007-11-24
Try the following.

sudo gedit /etc/modprobe.d/alsa-base

and add the line "options snd-hda-intel model=5stack" without quotes under the heading # Prevent abnormal drivers from grabbing index 0.



Then the following commands:

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

You will need your ubuntu disc in your drive for the third command.

Reboot.

---

### Post by jdelaros1 on 2007-11-24
Verify your alsa-mixer settings are correct, check for any items that might be muted. Run alsa-mixer, then use F3 for playback options and F4 for capture options. Use the left/right arrows to navigate, press m to mute/unmute an option.

---

### Post by thecure on 2007-11-24
I have an Inspiron 6000 and sound has worked fine. Like others have said... run alsamixer in terminal and make sure nothing is muted. Once the PCM was muted for me... also make sure it's trying to use the right device.

---

### Post by wormser on 2007-11-24
> **Skuzniak said:**
> Try the following.

sudo gedit /etc/modprobe.d/alsa-base

and add the line "options snd-hda-intel model=5stack" without quotes under the heading # Prevent abnormal drivers from grabbing index 0.

Then the following commands:

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa

You will need your ubuntu disc in your drive for the third command.

Reboot.

I tried that and it did not work.  From [another thread]("http://ubuntuforums.org/showthread.php?t=314383") I believe that there is a line at the bottom of /etc/modprobe.d/alsa-base I need to add.  I have tried a few for Dell with no success.


> **thecure said:**
> I have an Inspiron 6000 and sound has worked fine. Like others have said... run alsamixer in terminal andi make sure nothing is muted. Once the PCM was muted for me... also make sure it's trying to use the right device.

Attached is alsamixer screen shot.  Everything looks fine to me but I do not see headphones.  Does your alsamixer look the same?  Can you also post your last line of /etc/modprobe.d/alsa-base? 

One thing I have noticed is that I do not have "external amplifier".  Other threads regaurding Intel ICH6 soundcards needing external amplifier enabled to solve this issue.  How can I make it visible so I can enable it.

Thanks for your help so far,  Any other ideas?

---

### Post by thecure on 2007-11-25
> **wormser said:**
> 
Attached is alsamixer screen shot.  Everything looks fine to me but I do not see headphones.  Does your alsamixer look the same?  Can you also post your last line of /etc/modprobe.d/alsa-base? 

Thanks for your help so far,  Any other ideas?

Here's my alsamixer screen shot and copy of my alsa-base if this is any use to you. (Inspiron 6000)

---

### Post by wormser on 2007-11-25
> **thecure said:**
> Here's my alsamixer screen shot and copy of my alsa-base if this is any use to you. (Inspiron 6000)

Thanks for the response.  Everything looks good in alsamixer.  I tried replacing my alsa-base file with yours and it did not work.

I am pretty convinced after all my searching that the external amplifier needs to be enabled.  The problem is that it's not listed under the switches tab in the gnome volume manager.  External amplifier is not even listed on preferences to make it show up under the switches tab.

What needs to be done to make external amplifier an option?

Thanks

---

### Post by thecure on 2007-11-26
> **wormser said:**
> Thanks for the response.  Everything looks good in alsamixer.  I tried replacing my alsa-base file with yours and it did not work.

I am pretty convinced after all my searching that the external amplifier needs to be enabled.  The problem is that it's not listed under the switches tab in the gnome volume manager.  External amplifier is not even listed on preferences to make it show up under the switches tab.

What needs to be done to make external amplifier an option?

Thanks

I've installed/reinstalled Ubuntu and other linux distros a bunch of times and never had a problem with the sound on the first start up on any, except for Puppy linux but that's off a USB pendrive.
 It would be a lot easier to make sure you have an error free copy of Gutsy and reinstall. Or at least see/hear if your sound works when the "Live" CD boots up. If it doesn't I would think you had a hardware problem.

---

### Post by wormser on 2007-11-26
> **thecure said:**
> I've installed/reinstalled Ubuntu and other linux distros a bunch of times and never had a problem with the sound on the first start up on any, except for Puppy linux but that's off a USB pendrive.
 It would be a lot easier to make sure you have an error free copy of Gutsy and reinstall. Or at least see/hear if your sound works when the "Live" CD boots up. If it doesn't I would think you had a hardware problem.

Yeah, I have installed other distros and had no problems.  This started with the upgrade to Gusty, so I did a clean install and the problem was still there.  I just booted into XP (its been over 6 months) and the sound from the speakers was not working but I did get sound from the headset.  That pretty much says it is a hardware issue.  I think the upgrade to Gusty broke my hardware.  I am going to pull apart my laptop to check no wires came unplugged.  Have anybody ever heard of linux breaking sound hardware?  I have heard that it has broke monitors before.

Thanks

---

### Post by timbounceback on 2007-11-27
ditto, i have a 6000 and exactly the same thing happened to me - it seemed to brick my sound hardware. A temporary workaround is to use PCM, but it would be nice to have "real" sound.

---

### Post by wormser on 2007-11-27
> **timbounceback said:**
> ditto, i have a 6000 and exactly the same thing happened to me - it seemed to brick my sound hardware. A temporary workaround is to use PCM, but it would be nice to have "real" sound.

I do believe my hardware got bricked with the upgrade to Gusty.  I believe something happens to the external amplifier because it does not get recognized in Gusty.  Sound from the speakers does not work in Gusty, XP and a Slax live CD.  There should be a warning for other Inspiron 6000 users and any other laptops that might have been effected.

Is there anybody else this has happened to?

---

### Post by timbounceback on 2007-12-08
It might be worth filing a bug report and seeing if anyone else can confirm it :confused:..

---

### Post by wormser on 2007-12-13
> **timbounceback said:**
> It might be worth filing a bug report and seeing if anyone else can confirm it :confused:..

Bug report filed [here]("https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/176238").

---

