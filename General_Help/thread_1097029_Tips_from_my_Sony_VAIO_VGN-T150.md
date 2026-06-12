---
title: "Tips from my Sony VAIO VGN-T150"
date: 2009-03-15
forum: General Help
---

### Post by jsg24 on 2009-03-15
Hello all.

I installed Ubuntu 8.10 on my inherited laptop. A 2004 Sony VAIO VGN-T150.
Here is it's review by PC Magazine: 
[http://www.pcmag.com/article2/0,2817,1750760,00.asp](http://www.pcmag.com/article2/0,2817,1750760,00.asp)

I encounted some problems and through checking ubuntu forums and patience I managed to solve most of them to make this a pretty usable personal computer.

These are just tips for anyone else who wants to install ubuntu on the exact same hardware as my laptop, because I wish someone else would have written this when I was trying figure out all my pc problems.

NOTE: Just because you have the same hardware and are installing the same ubuntu version, it does not mean that when you try my advise it will not stuff up your computer in a very very bad way. You follow this at your own risk.
Now with that being said, these are the problems and solutions I got. With problems I'm still having listed at the bottom.

After installing ubuntu 8.10:


First thing I noticed was that the sound didn't work.
My fix: I went to Add/Remove and installed the GNOME ALSA Mixer. Once installed I started the program and turned off 'External Amplifier' which was ticked by default.

I was forced to turn off compiz because every time I started Firefox, it would appear as if I had pressed F11 while running it. So it would start up in "F11 Mode" until I turned compiz off.

Then I found that YouTube videos were not playing correctly. They were sluggish even when fully loaded before playing. I tried installing the Adobe Flash from Adobes website, but that didn't solve it. So a terrible way was downloading the videos and using VLC to play them.
My fix: Using synaptic package manager, I uninstalled adobe flash and installed a package for firefox called: flashplugin-nonfree
YouTubes videos worked for me after that.

Games:
Another thing I found was when playing games like Tremulous, the mouse cursor would sit in front of the screen and not move. It was irritating.
My fix: Funnily enough, I installed a game called "The Mana World" and in that games options, I selected something along the lines of "Use systems mouse cursor" instead of using the games mouse cursor. And them when going back to Tremulous, it was solved.

The Arhive Type: .rar is was supported on my pc. I could not "Extract Here" .rar files.
My fix: Using synaptic I installed a package called: unrar

FALSE HOPES:
I use USERPLANE chat quite a lot. And when trying to connect to a chat group, it always showed "Connecting" and never connected.
Initially I solved it by using synaptic to install the sun-java5-plugin .
But now its doing the same thing again. Still trying to figure this out.

PROBLEMS PERSISTING:
The sound +(plus) and -(minus) buttons do not work. And the DVD option buttons do not work.

My computer has an inbuilt Microphone. I use Skype a lot. But I can not get my microphone to work for skype. I went through every single Skype option and none of them picked it up. So I am forced to plug in an external mic.

Multimedia:
I can not get VLC or other media players to play the video files transferred from my W800 Sony Ericsson phone. (.3gp files)

INTERESTING TO NOTE:
I tried use the online game Second Life. Installing the version for linux from its website. It did install and run, BUT. I found that my hardware is was too downgrade for it and my internet connection is not great either. So I could not use it.

Also, the game Tremulous does work on my pc but just barely. This is not a great laptop for serious games. The only hope of running Tremulous or maybe even SL tolerably, is to install more RAM in your laptop. Get it up to 1 Gig or maybe even 2 Gig if thats possible. (Have not tried this yet.)

I found that using Brasero to copy CD/DVD's is problematic. I found it was much better to use Ubuntu's "Copy Disc..." function

Thats where I stand right now. Other than those problems, this is computer is nice to use.

Thats all from me. Maybe when I upgrade to Ubuntu 9.04 more of my problems will be sovled.

---

### Post by shakespit on 2011-08-22
Thank you for your post.

I did some more tweaking to get VGN-T150 to work. I had problems connecting to wi-fi networks - thought it was encryption, which is WPA/WPA2 PSK for my network, but figured out that this is a problem with adapter - not able to connect to channels 12 and 13 (allowed in europe, but banned in US). So I tweaked eeprom of my wireless card (do it at your own risk).

Here are [nice instructions]("http://www.fx.cz/sklad/intel/") on how to do it - but drivers and link to a Knoppix kernel is outdated, so [here]("http://www.jeremycole.com/blog/2008/04/10/installing-an-oem-intel-2200bg-mini-pci-card-into-a-bios-locked-hpcompaq-nc8000/") you will find a valid ISO link and drivers for Intel 2200BG card. I patched only those three lines and it works fine for me:
```
#ethtool -E ethX magic 0x2200 offset 0x4c value 0x5a
#ethtool -E ethX magic 0x2200 offset 0x4d value 0x5a
#ethtool -E ethX magic 0x2200 offset 0x4e value 0x52
```

---

