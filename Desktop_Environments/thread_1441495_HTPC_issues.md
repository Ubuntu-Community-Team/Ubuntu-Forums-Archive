---
title: "HTPC issues"
date: 2010-03-28
forum: Desktop Environments
---

### Post by tlarkin on 2010-03-28
Hello everyone,

I just rebuilt my HTPC and decided I did not want to pay for an OS so I downloaded and installed the newest version of Ubuntu.  I have the following hardware configuration

Processor:  Intel Core 2 Duo e6300
RAM:  2 Gigs DDR 2 800
Motherboard:  Intel DG965wh
Sound card:  Intel 82801HR/HH ICH8
Video Card:  Nvidia GeForce 210 512mb
Desktop Environment:  Gnome

Ubuntu is installed, the Nvidia drivers loaded. It displays awesome over HDMI into my TV @ 1920x1680 with no issues.  I am using the HDMI out of my Nvidia card into my TV.  Now, my sound card has optical audio out, which goes into an older Sony receiver.  Basically, my receiver doesn't support HDMI, and I will be shopping around for a new one in the near future.  Until then, I would like to get the optical audio to work on PC into my receiver.

However, no matter what I seem to try, the audio will not work at all.  I know that HDMI also has 7.1 audio going through it, so I am wondering if the HDMI audio is disabling the optical audio out?  

Anyone seen this happen before?  Basically once I get the audio to work I am going to live with it until I can save up some more cash and get a new receiver.  Thanks.

-T

---

### Post by tlarkin on 2010-03-28
Upon further googling of the subject, it seems optical audio out in Ubuntu is something that cannot be done?   I am not finding any answers anywhere.  Has anyone ever got optical audio out to work in Ubuntu?

---

### Post by JoelOFH on 2010-03-29
I don't have much expertise with Ubuntu, but I am using the OS on my HTPC (which is working out nicely). ;)

The first thing you may want to try:
Select the specific sound output device. It may be set to HDMI by default (?).
***System > Preferences > Sound > Output*** tab. You may need to select your option in that panel.

If that doesn't work, perhaps you can just do what I do. Connect your HTPC to your TV via HDMI, and have the TV send the audio signal to your AVR (via optical cable, in most cases). This works, damn near flawlessly, for me. 

Good luck!

---

### Post by tlarkin on 2010-03-29
tab or button?  I don't have a preference tab called output.  I think it is just lack of driver support as unfortunately, it works when booting Windows.

Oh well I am going back to best buy tomorrow after work and just going to buy a HDMI compliant receiver and run everything over HDMI since HDMI also runs 7.1 audio through it.

---

### Post by JoelOFH on 2010-03-29
> **tlarkin said:**
> tab or button?  I don't have a preference tab called output.  I think it is just lack of driver support as unfortunately, it works when booting Windows.

Oh well I am going back to best buy tomorrow after work and just going to buy a HDMI compliant receiver and run everything over HDMI since HDMI also runs 7.1 audio through it.

It's a tab. Are you unable to try my second option?

>  Connect your HTPC to your TV via HDMI, and have the TV send the audio signal to your AVR (via optical cable, in most cases).

---

### Post by tlarkin on 2010-03-29
For some reason it doesn't like the optical audio output from the TV to the receiver.  I am not sure if HDMI is outputting audio properly in Ubuntu.  

I am going to get a new receiver soon anyway which will make everything run over HDMI.

---

### Post by tlarkin on 2010-04-06
I finally got everything wired, tied down, and organized and my audio and receiver fully hooked up after rearranging my place.  HDMI audio still does not work.  I downloaded and compiled the newest ALSA drivers and [COLOR="RoyalBlue"]aplay -l[/COLOR] still does not list my Nvidia device as a possible audio device.

I have the GeForce 210 512mb with HDMI out using the latest Nvidia driver.  

Anyone got any pointers?

***update

Well, I got the drivers loaded, and I can see the card when I run the alsamixer binary from the command line, but I get no options to enable it for audio out.....DO I just have a card that is not compatible?  I also see the asound.conf and another conf file that are not created on my computer when I ran the installer script.

---

### Post by tlarkin on 2010-04-06
I was able to read a few things on my lunch break.  I think if I disable the onboard audio and remove the nvidia module from the blacklist config file for ALSA it should maybe then give me a config...

Going to try when I get home from work tonight and will post back results.

---

### Post by tlarkin on 2010-04-07
Well after attempting a plethora of fixes and methods to get the sound to work I decided to return the Nvidia card.  I returned it for a slim, no fan, low power consumption ATI Radeon 4350 and out of the box the proprietary ATI drivers not only worked, but also allows sound over HDMI with no loops or fussing.

I know this doesn't really solve my problems with the GeForce 210, but if anyone reads this thread and wants to run HDMI audio out of a Linux box, please highly consider getting an ATI card.  They work out of the box, the Nvidia one I could only get half way to work.  By half way I mean I could get the system to recognize the card, and recognize it was HDMI but it had no options to configure audio out.

###########edit########

Well, it is working but I cannot control the surround sound output from the HTPC.  I went into VLC and told it to use the HDMI over the ATI and surround sound works.  However I cannot control the outputs with the sofware..

I have come so close to making it work perfect, any ideas or pointers?

---

