---
title: "Can someone help me interpret what this does? (W ine Config related)"
date: 2007-08-23
forum: Gaming &amp; Leisure
---

### Post by RudolfMDLT on 2007-08-23
Hi there,

I'm a complete noob when it comes to wine and I'm following this HowTo for Tiberian Sun,

 [http://appdb.winehq.org/appview.php?iVersionId=7440](http://appdb.winehq.org/appview.php?iVersionId=7440)
 
and I couldn't get the sound working. I set the AutoScanCards property in the registry to Y and then I had sound - though this kills my framerate by about 25%. I also enabled the Pixel Shader and now the game is dead slow! Can some one please help me interpret what this means in english so that I can go hunt for the sound problem and get a little better performance in my game! :)


> # Create the file ~/.asoundrc, and put the following in it:
pcm.cnc {
type asym
playback.pcm "hw:0"
}
# Run 'regedit', and navigate to 'HKEY_CURRENT_USER\Software\Wine', then add the key 'ALSA Driver'. In it, add the following strings with the values
AutoScanCards = N
DeviceCount = 1
devicePCM1 = cnc

What does the text in the above .asoundrc file mean? I sort of follow the logic in the registry hack.


Thanks for any help!

Rudolf

---

### Post by cogadh on 2007-08-23
The .asoundrc file creates a PCM device (Pulse Code Modulation), otherwise known as a digital audio device, and the registry edits tell Wine to use that device for sound output. You can use the .asoundrc file to create any number of PCM devices with unique settings that are basically custom configurations for your sound card. You don't actually need the .asoundrc file for sound to work in everyday situations. In fact, it appears this particular PCM device has no real custom configuration, it is just a generic device with the default settings. I think the only reason the how-to tells you to do it is so that Wine has a clearly defined single device to access, rather than using the autoscan, which will often find several different default PCM devices, depending on your default ALSA config.

I don't know if that made anything more clear, if it didn't, take a look at the ASLA Wiki page for the .asoundrc file:
[http://alsa.opensrc.org/index.php/.asoundrc](http://alsa.opensrc.org/index.php/.asoundrc)

---

### Post by RudolfMDLT on 2007-08-23
Thanks a lot man! :) Apreciate it!

---

