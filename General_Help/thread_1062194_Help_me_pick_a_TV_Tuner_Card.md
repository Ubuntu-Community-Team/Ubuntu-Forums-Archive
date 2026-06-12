---
title: "Help me pick a TV Tuner Card"
date: 2009-02-06
forum: General Help
---

### Post by PsychedelicWonders on 2009-02-06
I have no idea what to look for.

I would like to be able to use my HTPC as a tivo also.

What should I be looking for exactly in a tv tuner card?

---

### Post by whitegourd on 2009-02-06
I have a Hauppauge PVR-150 and it's a pretty good card.

---

### Post by mb_webguy on 2009-02-06
I don't have one myself, but I was shopping around for one a while ago when I was thinking of building a MythTV box.  Hauppauge cards seem to be fairly well supported on Linux.  pcHDTV produced the first video capture cards supported by Linux, so that's a pretty safe choice.  And I've seen several people suggest the Silicondust HDHomeRun, which is a pretty nifty network device with two HDTV tuners that allows you to watch TV from any computer on your network.

Even if you're not planning on using MythTV, you can check card compatibility on the [MythTV website]("http://www.mythtv.org/wiki/Tuner_Card").

---

### Post by PsychedelicWonders on 2009-02-07
But what specs should I be looking for?

What kind of ports should I make sure it has on the back?

I know nothing about them and what particulars are needed to be built into them?

---

### Post by FluffyElmo on 2009-02-07
I second the PVR-150, it will capture analog cable or a video signal from a VCR. Well supported, good recording quality and it also includes a remote. You will need another video card to output video, your computer may already have TV-Out, if it doesn't then get an add on video card (I've had good luck with NVidia) that has the same type of video output as your TV.

For digital cable or satellite the approach is to have the PVR-150 send signals to your box to change it to the correct channel then record the signal. This is clearly less than ideal but there is no standard way around it. 

For digital cable, if it's a Motorola box I think you can connect to it via Firewire and get the signal that way. For satellite some people get a satellite card for their computer and crack the signal but I don't know anything about that. 

I realize that this raises more questions than it answers but if you tell us what type of TV service you have, what type of TV you have (analog, LCD, etc)  and what video card your current computer has it will help narrow things down.

---

### Post by PsychedelicWonders on 2009-02-07
This will be hooked up to a new Samsung lcd, either 40 or 46", havent bought it just yet.

The video card is open for debate right now.

It will be a dual video card, with a HDMI port & a dvi port.

I think I will probably do satellite... I prefer it... but I would like the card to be able to do either cable or satellite if at all possible.

Do I really have to have a different card just for satellite?

---

### Post by mb_webguy on 2009-02-07
One thing to keep in mind is that no video card on the market can process encrypted QAM channels.  That means that you'll need a cable or satellite box to receive any channels you couldn't get from an antenna or from cable without a cable converter box.  And if you're planning on having a cable/satellite box and using the Linux computer as an HTPC, you'll need to look into ways to control the cable/satellite box from the Linux computer, which may affect your choice of video capture cards.

Some cable/satellite boxes have a firewire port that allows both control of the box and transfer of video.  If that's the case, then you don't necessarily need a video capture card, but you would need a firewire card.

I would strongly suggest browsing the MythTV website.  There are many informative articles concerning different aspects of building a Linux-based HTPC, most of which aren't necessarily specific to MythTV.

---

