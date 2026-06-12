---
title: "UrbanTerror working perfect. all suggested methods failed me"
date: 2010-01-02
forum: Gaming &amp; Leisure
---

### Post by Torchmann on 2010-01-02
I got Urban Terror working smooth, nothing anyone else said worked here for me, this how I did it...experimenting blindly
 
Here is my report on how I fixed sound for UrbanTerror:

I was told..."Try and install libsdl1.2-debian-pulse so that sdl uses pulseaudio directly, and see if that helps."

I actually had libsdl1.2-debian-pulse installed. changing it to alsa as someone else recommended just killed my sound.
pulseaudio is just the sound server not a driver.
pulse actually controls alsa from what I've read on other threads.
libsdl-sound1.2 was missing along with libsdl1.2debian which is the SIMPLE DIRECTMEDIA LAYER.

SOLVED
I tried going all alsa found out pulse is only a server between alsa and the application running alsa. screwed it all up and had to re-install.

running compiz the game was quiet but I could play a few minutes using metacity...still crashed...

I tried debian and slackware...no luck
I installed Ultimate Edition 2.5...everything else working fine...back to no sound in Urban Terror. no metacity to switch to

Ultimate Edition might have given me a better repository or other libraries for success, anyway this is what I have going that makes UT work perfect. very perfect...

Made sure adobe 10 flashplayer that was lagging gnome and firefox wasn't the problem by leaving it out of this install.

I had to install the alsa mixer gui to get my mono base channel working on the soundcard but Urban Terror still kept crashing.

I found out that if your sound crashes instead of trying to back out of UT and locking up your system forcing a restart just hit alt+tab
and it will minimize the window and you can close the app with a right-click close

I tried switching to Libsdl-debian-alsa and I had absolutely no sound
I had to open pulse audio preferences and select the analog stereo duplex option, the digital feed was not working with my sigmatel 97 soundcard.
I tried switching to Libsdl-debian-all and that still worked for everything else but not urban terror.
I noticed that Libsdldebian1.2 (Simple Directmedia Layer) was NOT installed by default so i installed it.
No change yet...
I switched back to ubuntu 9.10 default Libsdl-debial-pulseaudio from the Libsdl-debian-all everyone was reccomending

Urban Terror works perfect,
No crash, no lag and I have compiz desktop cube active and am running under the ubuntu drivers so it was never an ati driver problem strictly audio. some people have said UT ran better under metacity and it did for me but still kept crashing the soundcard until I installed the missing 2 libraries.

Here is a list of what I have installed in synaptic under a search for sdl
libsdl-gfx1.2-4
libsdl pango1
libsdl-sound1.2
libsdl-ttf2.0-0
gambas2-gb-sdl
gambas2-gb-sdl-sound
libsdl1.2debian-pulseaudio
libsdl1.2debian
libsdlmpeg0
mplayer-skins
libsdl-image 1.2
libsdl-mixer 1.2
vlc-nox
mplayer
mplayernogui

Here is what's showing as manually altered under sdl (the ones I changed)
You have to have all 3 of these installed...
libsdl1.2debian-pulseaudio
libsdl1.2debian
libsdl-sound1.2

and just for posterity if it had anything to do with alsa at all when I installed the alsa mixer and alsa gui...
this is what's showing up in synaptic filtering for manually installed under a search for alsa
alsamixergui
alsaplayer-common
libsd-alsa0
alsa-utils
gnome-alsamixer
alsa-oss
alsa-base
libsound2
alsa-tools-gui
libsound2-plugins
linux-sound-base
gstreamer0.10-alsa
qamix
libclalsadrv (this is the alsa driver c++ access library)
gamix
bluez-alsa

I'm sorry I cannot say if the sdl libraries I installed cured the problem alone...
Or if it was in combination with the alsa utilities I added.
All I can say is if you have the same sdl installs and UT still doesn't work try checking out the sdl file dependancies and see if you have the alsa installs I do.

I can definitely say it has nothing to do with the graphics card or drivers
I was getting lag and rough frames in UT but it was due to:
The UT default internet connection setting was set to 8, I'm on a cable modem so I set it to 24
The UT refresh rate was over 80 exceeding the 60 hz of my monitor and the setting of 50 in the compiz options.
I set the UT refresh rate to 50
I also maxed out the # of sends to the server
It works perfectly smooth now with no sound crashing.

6 year old Dell Inspiron 9100 with P4 1mb on die cache and 1gig ram with hyperthreading and a usb keyboard
I have the troublesome radeon mobility 9700 graphics card. It's actually a dell built 9600 with 128 pin bus and 128 ram.
I wish I had the 9800 with the 256 pin bus and 256 ram. my old 9700 won't run DOD source or RedOrechestra smoothly anymore even with rendering turned down
UT is playing better on my machine than dod non source, painkiller and doom3 ever did UT rocks

Compiz-fusion wasn't working for me under jaunty because the legacy drivers were not supported but works great under the stock Karmic setup...

---

### Post by Torchmann on 2010-01-03
Oh, buy the way I also tried installing the flash 10 codec
no UT problem with that...
but when I tried installing:
flashplugin-nonfree extrasound
swfdec-gnome
swfdec-mozila
to see if these would get the garbage adobe flash junk to stop lagging up all my browsers the flash kept lagging and the UrbanTerror started crashing the soundcard again.
I tried viewing flash content with hardware acceleration disabled in flash and it still lagged firefox. 
firefox still runs lickety smooth without slowdoughbee ffffcrash 10
I don't know whats up with flash but it's really making me angry...it only works under microsoft...not under wine only under true xp.
wine lags like a brontosaurus trying to do anything with it even on a virgin install with or without adobe installed. I think it's too intrusive. using flash is like how your browser locks up when a windows .exe trojan downloader from a pornsite is trying to get in to your linux.

I uninstalled the above 3 codecs and UT is back to running good.

---

### Post by Torchmann on 2010-01-03
I couldn't resist... I installed flash.:(
I remembered when flash wasn't working for me UT wasn't either.
Now that UT is working I'm thinking well whatever was conflicting running UT prolly was causing conflict in flash so if I install flash now it might work good too:P
NOT. Not only did the flash 10 plugin play video choppy with the appearance of looking through tear filled eyes, it lagged out firefox when there was no video content available. the pages were rendered so choppy you couldn't scroll down the page.

I could not send an email because some of the yahoo text entry boxes like for entering the address your emailing were lagging. The letter you wanted appeared 3-5 seconds after you struck the key. most other text entry boxes worked fine. It was consistent for each site; what was working smoothly and what was not using either firefox or Konqueror.

My gnome application selection menu's were rendering extremely slow, My window effects were lagging too.
I thought maybe flash10 might be incompatible with my Dell ati radeon mobility 9700 128 bit graphics card, or with my sigmatel STAC 9750 sound card. I was grasping for understanding.
I tried un-installing Flash and re-booting but all the lagging remained and UT still failed to play the intro splash cleanly or function well or drop to the desktop with <alt><tab> when it locked up.

I tried re-installing 9.10 from scratch with deleting the partitions and repartitioning the drive. 
After it installed the lag was all still there and UT freshly installed from scratch failed to run with the exact same dependencies It had when it was running fine before installing Flash  and now running successfully without any flash installed.
When there are no problems I usually run 1-5k network traffic staying connected.... 
After installing flash and up until performing a pre-install random data drive-wipe, System info was showing higher ram and cpu usage than normal. I was also getting 2-3 times the normal network traffic through the firewall. 
after the wipe it's back to normal

I got it working again!
How did I get it working? I used a drive wipe program and recorded random data on the drive then re-installed ubuntu9.10, That's it...I didn't do anything else different from the failed installs.
It's highly likely that the Flash10 Install did not uninstall cleanly.
From my perspective of a club-fisted dolt just trying not to mash too many keys at once as I try to spell one syllable words...The flash related problems act JUST like when you get trojans on a window system and the antivirus misses or ignores it... Or when a program is trying to run and the firewall or anti-virus is preventing it from running but not stopping it from trying.
*Or when I'm trying to play Counterstrike Source on my windoze partition and I forget to disable the ATI hotkey poller*??? could that be related???
Something ugly got on my drive
I can't see any other explanation

The other times I could not get UT running under jaunty, debian lenny, slackware 13, ubuntu studio, and 3 installs of Karmic; I also had flash installed.
The only time I could get UT to run sweet was under karmic with NO flash installed
Installing flash fu-bar'ed my system and killed UT...every time.
Same problems were persistent through subsequent installs...every time.
except when doing a pre-install drive wipe then NOT installing flash...every time.

Heres is my synaptic report for a serch using the term sdl:

libsdl-gfx1.2-4
libsdlpango-1
libsdl-sound1.2
libsdl-ttf2.0-0
gambas2-gb-sdl
gambas2-gb-sdl-sound
libsdl1.2debian-pulseaudio
libsdl1.2debian
libsmpeg0
mplayer-skins
vlc
libsdl-image1.2
libsdl-mixer1.2
vlc-nox
mplayer
mplayer-nogui

The only thing I had to change on this fresh brand new install on a wiped drive is installing the libsdl1.2debian-pulseaudio as has been suggested in the other threads. I was wrong, the common fix worked for me too, after I got rid of the gremlins that are related to installing flash10 on my system.
I never have any problems with non flash media
I presume that if I were to install flash 10 again It would fubar my system and break UT again
I don't want that to happen again.
 I'm just going to have to watch You-tube from my Windoze partition and keep the flash out of my linux.
  Not just because it breaks UT for me but because it damages the way most things run that should not have anything to do with watching a movie...

P.S. running nekked firefox in wine is really slow and flash videos almost will not play at all with flash installed into wine. I have not been able to use wine for anything usefull and can't install my windoze drivers get it to work smooth so I just reboot into xp instead.

sorry if I led anyone on a wild goose chase..
Maybe this history can point a more knowledgeable person in the right direction as to why flash is killing UT and lagging everything else for me.

---

### Post by ogromano on 2010-01-07
[-o< \\:D/

Praise the UT Lords!!!

I was having a huge issue with my UT since I installed Karmic... everytime I played it was choppy as hell and the sound would cut in and out and UT would crash everytime on exit. I had the same issue on Teeworlds...
Also if I ran it windowed with the system monitor in in view to see what happened, both my cpu's (Core 2 Duo) would skyrocket to 99% and as soon as I was able to shutdown UT they'd drop back down to normal.
I found your post looking for something else and I gotta say that as soon as I installed libsdl1.2debian-pulseaudio (which removed libsdl1.2debian-alsa) and libsdl-sound1.2 everything worked fine. UT works, doesn't run my cpu's like mad anymore!!!

Thanks for your hard experimenting sessions... I had no idea how to even start to check where the problem might be (too much of a Linux/Ubuntu noob still). But I was sure it wasn't a video problem!

Cheers and happy UTing!!!

---

### Post by KyleG545 on 2010-02-11
All i can say dude is THANK YOU i have been trying to get UT to work on my ubuntu partition for quite some time! 

now i can resume my duties as a ref without using windows

thanks again and happy fragging!

---

### Post by milia on 2010-03-09
> **Torchmann said:**
> 
Here is a list of what I have installed in synaptic under a search for sdl
libsdl-gfx1.2-4
libsdl pango1
libsdl-sound1.2
libsdl-ttf2.0-0
gambas2-gb-sdl
gambas2-gb-sdl-sound
libsdl1.2debian-pulseaudio
libsdl1.2debian
libsdlmpeg0
mplayer-skins
libsdl-image 1.2
libsdl-mixer 1.2
vlc-nox
mplayer
mplayernogui

Here is what's showing as manually altered under sdl (the ones I changed)
You have to have all 3 of these installed...
libsdl1.2debian-pulseaudio
libsdl1.2debian
libsdl-sound1.2


Thank you !!! Ater installing the above, finally, I have sound in UT, even if it is sometimes distorted.

UT 4.0, Ubuntu 8.04.3 :).

---

### Post by ziffolo on 2010-11-02
I tried this but... works only the first time ! I don't understand why when I restart my system, after a switch off or just a restart UT got the same problem as before: choppy sound and choppy frame rate.

I solved the problem lots of times, and after every restart I'm back to the issue. Instlling and deinstalling libraries randomly till I find a definitive solution ?

And why, when a configuration is ok, after I restart it it's not good anymore oO ?

---

