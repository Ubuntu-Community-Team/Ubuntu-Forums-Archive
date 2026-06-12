---
title: "Issues with Creative Audigy ZS 2 Notebook PCMCIA card"
date: 2006-01-13
forum: General Help
---

### Post by Myranti on 2006-01-13
Okay.

This post is partly 5.10 related, and partly 6.04 related.

So I've been using Kubuntu 5.10 for a bit recently, which I quite like, and can probably replace windows with it (or some variant of Linux at least). There's one major problem stopping me. I can't get my Audigy 2 ZS notebook card to work. In Kubuntu 5.10 if I plug in my card before boot, it'll get to where it load/starts the ALSA cards, which without it plugged in, number 0 and 1. If I plug in the card, it gets 'ok' with card 0, but just stops after that. This is also reflected in the fact that anytime I plug my card in while Kubuntu is running, it hangs the machine completely and I have to turn it off and on again. I tried compiling the latest 'dev' release of ALSA to try get it working, but didn't completely understand how to go about loading everything properly. As far as I can tell, it could just be an issue with the Texas Instruments cardbus device not being detected properly (There's 2 listings as CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller) 

This leads me to Kubuntu 6.04, the Flight 2 Dapper Drake release that i'm running on now. I can plug the card in and boot up, it can see the card in the Info Center and is one of two devices listed in KMix. I'm using an HP nx6120 notebook, which has 'Intel ICH6' audio as the other device (mine is listed as Audigy 2 ZS Notebook [SB0530] by KMix). I've checked numerous posts that i've found through google, most talking about making sure the 'Audigy Analog/Digital' switch is set right. No matter what I do to it, it doesn't give me sound, just hiss when there should be audio.

I'm not sure what to do next, I could compile the very latest dev release of the ALSA drivers and such, though i'm not sure how much that will help me (and some instructions would be helpful if someone reckons I should, the alsa-project.org instructions confused me a bit). The lspci results give me this:

0000:03:00.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
        Subsystem: Creative Labs: Unknown device 2001
        Flags: bus master, medium devsel, latency 64, IRQ 177
        I/O ports at 3000 [size=64]
        Capabilities: <available only to root>

Note: This PCMCIA card has Digital (Optical) capabilities that are turned off and have any related volume down completely (checked this with KMix and alsamixer). There is 2 ways of connecting my speakers however. I can use the Optical jack area as it doubles as a headphone/speaker out and an optical out. However, the card also comes with a cable that connects into the card much like how modem/nic dongles do on PCMCIA cards and has 3 connections (which I use as I have a 7.1 speaker setup). I'm not sure if this in turn effects anything in regards to getting the sound working either. Plugging my speakers into either the three cables connected card properly or just using my main green connection (default speaker connection) in the Optical/Headphone jack just gives me hiss. I've also tried selecting ALSA as my audio Device in System Settings > Sound and Multimedia > Sound System on the Hardware tab and using Override device location as hw:1,0. I've also fiddled with things such as full duplex, custom sampling rate, etc.

If anyone has any ideas, please let me know. I've tried to give as much info as I can think of at the moment. I'd really like to use Kubuntu to replace windows because there's not much need for me to use windows all that much, the only thing making it difficult being the sound issues. Also if anyone knows of any way to get the Cardbus issue resolved in Breezy, that would be handy, though from what I remember there was no specific support in Breezy for it. If anyone wants me to do an extended lspci or anything else and post information, let me know.

Thanks in advance to anyone that can help me figure this out

---

### Post by phico on 2006-03-07
Same problem on an Acer 1700.  I was hoping this could work in
6.04 ..  Is there any chances ?

---

### Post by adolfotregosa on 2006-03-08
mines working since last kernel update and ALSA! try that :s then make audigy the primary sound card

---

### Post by phico on 2006-03-09
Thanks for your feedback.  I'll try that and let you know.

---

### Post by FloSynergy on 2006-03-17
hi there,

same issue. how do i make audigy the primary sound card?
and since i'm quite new to linux, how do i recompile a kernel to achieve this?

thanks,

flo

---

### Post by cmikos on 2006-04-26
Did anyone figure this out???

---

