---
title: "VirtualBox no sound"
date: 2008-05-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by GraemeJohnAuchterlonie on 2008-05-18
Dear Ubuntu Forum,
I have 3 dual boot systems all running initially installed XP and then post XP installed Ubuntu.
They all run VirtualBox. The two desktops 32-bit and 64-bit work correctly. However my Dell Latitude D510 has no sound in either Ubuntu or VirtualBox XP. Reinstalling Ubuntu solves the sound problem even after reloading VirtualBox the sound is still there. After rebooting the laptop computer no sound is available in Ubuntu or Virtual XP.
VirtualBox XP does not recognise Dell CD's to install drivers in virtual-XP mode.
Any help for what appears Dell specific driver issues would be appreciated.
Graeme

---

### Post by garyedwardjohnston on 2008-05-18
The VB add-ons dont help?

---

### Post by niteshifter on 2008-05-19
Hi,

What version of VBox?
What version of Ubuntu?
What version of XP (SP1? SP2? SP3?)

Regarding the Dell drivers for XP: Not needed, indeed not usable - it's not Dell hardware that XP is running on in the virtual machine. VBox is "pretending" to be the hardware - and the VBox Guest Additions provide improved version of video, networking, etc. over just plain VBox.

I gather Ubuntu is the Host OS, which Audio adapter setting are you using in VBox?

---

### Post by GraemeJohnAuchterlonie on 2008-05-21
Hi niteshifter,
I have Ubuntu 8.04
In Ubuntu the sound stops working after VirtualBox 1.5.6 OSE is loaded and the computer rebooted.
So Ubuntu loses sound as well as VirtualBox Windows XP SP2?
Thanks kindly
Graeme

> **niteshifter said:**
> Hi,

What version of VBox?
What version of Ubuntu?
What version of XP (SP1? SP2? SP3?)

Regarding the Dell drivers for XP: Not needed, indeed not usable - it's not Dell hardware that XP is running on in the virtual machine. VBox is "pretending" to be the hardware - and the VBox Guest Additions provide improved version of video, networking, etc. over just plain VBox.

I gather Ubuntu is the Host OS, which Audio adapter setting are you using in VBox?

---

### Post by niteshifter on 2008-05-22
Hi,

Hmmm, don't know that I can help you on this one: 8.04 introduced Pulse Audio, I'm running 7.10 which uses ALSA.

In the VBox GUI, for this Win XP entry what is the Audio Adapter set as? I'm thinking that for 8.04 it should be Pulse Audio.

---

### Post by AdamsJourney on 2008-05-24
I have a Inspiron 1720 Dual boot with Vista and Ubuntu 8.04 running XP on Vbox.  I had to set the audio on the Vbox to PulseAudio.  When I used the out of box settings I had no XP sound.  After messing with it I found that PulseAudio IHC AC97 worked for me.  Oh I'm also running VirtualBox 1.6... hope that helps.

---

### Post by nutsy.ben on 2011-02-17
Ubuntu 10.10 .....

None of the options work for me.

---

