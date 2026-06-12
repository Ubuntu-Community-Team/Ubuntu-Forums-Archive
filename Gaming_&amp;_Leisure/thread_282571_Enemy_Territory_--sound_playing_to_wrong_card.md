---
title: "Enemy Territory --sound playing to wrong card"
date: 2006-10-22
forum: Gaming &amp; Leisure
---

### Post by dav3yb0y on 2006-10-22
Hey Guys,

Linux newbie here running Dapper, though I must say every problem I've had has been resolved be reading thru the forums--until now.

I have two sound cards, a SB Live and an onboard SIS SI7012.  I have default set to SB Live.  Sound works with everything except Enemy Territory.

I read thru the threads here and did all recommended changes before I decided just to plug speakers into the onboard card.  and the sound worked just fine.

any ideas why its trying to play to the wrong card?  could i change something in the config file?

I guess at worst I can use the onboard card, but eww.

Thanks

---

### Post by jdunn on 2006-10-23
Well, SB Live series (excluding the new 24-bit card) are probably the best sound cards you can use for Linux.  Some of the Audigy cards are good too.

Anyway, if you are not at all using your onboard sound, did you disable it in your BIOS settings?  Also, try this:

Determine which sound card you want to use...example 'ls /proc/asound/card0/'. Use your favorite text editor to create a file called /etc/init.d/gamesound and add a line similar to this:

echo "et.x86 0 0 direct">/proc/asound/card0/pcm1p/oss
You may also need to add this line:
echo "et.x86 0 0 disable">/proc/asound/card0/pcm1c/oss

(Sound cards often have several playback and/or capture devices.  In this example, pcm1 is a combination playback/capture device on card0.  Older games like quake3 and et sometimes have problems with such devices so the capture component needs to be disabled for the game.  As an alternative, you can simply route the audio to a dedicated playback device for the game.)

Then create a symbolic link named S99gamesound in /etc/rc2.d so that your configuration in the file /etc/init.d/gamesound is used automatically every time you reboot.

This site may also be of some help:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound)

---

### Post by dav3yb0y on 2006-10-23
the bios trick worked, can't believe i didn't think of that!  :oops: 

Thanks!!  Now I can play ET and TCE!!

---

### Post by Garyu on 2006-10-23
Congrats, I see you got things working by turning off your hardware. However...

[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)
This guide will let you do it through software, look down at the bottom of the page, it will tell you how to configure default sound cards. 8)

---

