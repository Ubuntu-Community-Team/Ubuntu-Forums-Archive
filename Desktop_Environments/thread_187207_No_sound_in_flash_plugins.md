---
title: "No sound in flash plugins"
date: 2006-06-02
forum: Desktop Environments
---

### Post by johann_p on 2006-06-02
While the flash plugin for Firefox does work visually, there is no sound. E.g. when playing one of the videos on video.google.org or youtube.com, it shows the video but does not play sound.

---

### Post by johnc4510 on 2006-06-02
This may not be your fix, but it was mine. If I had anyother sound program open, such a XMMS the sound would not work in flash. Even if XMMS was not playing, and just open flash would not work. Once I closed it out, flash worked fine. Also video google works okay, but I have never gotten youtube to work. For flash, did you install: flashplugin-nonfree?

---

### Post by beuno on 2006-06-02
I do the exact same thing.
I close whatever Im using to play music
close Firefox
Open it again and all flash (even youtube) plays sound.

---

### Post by johann_p on 2006-06-02
[quote=johnc4510]This may not be your fix, but it was mine. If I had anyother sound program open, such a XMMS the sound would not work in flash. Even if XMMS was not playing, and just open flash would not work. Once I closed it out, flash worked fine. Also video google works okay, but I have never gotten youtube to work. For flash, did you install: flashplugin-nonfree?[/quote]

Yes, flashplugin-nonfree is installed. 
No other sound applications playing and no sound in flash.

---

### Post by detour on 2006-06-02
You may be experiencing this bug: [https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760](https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760)

This fix worked for me (roughly from the comments in launchpad):

sudo apt-get install alsa-oss
sudo nano /etc/firefox/firefoxrc

change: FIREFOX_DSP="none"
to: FIREFOX_DSP="aoss"

repeat for: /etc/mozilla-firefox/mozilla-firefoxrc

---

### Post by cbudden on 2006-06-02
Does this fix work if you have firefox installed in /opt/firefox ?

---

### Post by DarkStarDeity on 2006-06-02
I found this worked for me, but then I still had the problem described in [this thread]("http://www.ubuntuforums.org/showthread.php?t=89827") with flash freezing on some sites (mostly games). The fix in that thread (to install and use arts) worked to fix both of these problems (although I think the sound might be ever-so-slightly out of synch, but I can live with that. It's better than Firefox freezing up! 

If you're on Dapper, you need to modify the instructions slightly -
flashplayer-mozilla is no longer recognised, it's now flashplugin-nonfree 
and the Firefox rc file is now in /etc/firefox/firefoxrc

---

### Post by BoyOfDestiny on 2006-06-03
Man I can't wait until ESD is phased out... The never ending cause of problems with apps that use OSS... Seriously, since hoary... 

open a terminal

sudo killall esd

If flash gets sound, then go ahead to
System -> Preferences -> Sound

Disable sound server.

If the sound is out of sync (blame macromedia for using OSS). Install alsa-oss as was mentioned, then either launch firefox as 
aoss firefox
or change some setting (I've never bothered to since this is easy enough)

---

### Post by brin on 2006-06-04
Yes the problem is caused by esd but esd seems to be well supported by firefox hence does not require installation of arts.

On Dapper, I have found that by simply installing the esound-client package solved the sound problem. Run "sudo apt-get install esound-client" and reboot the system.

By using a sound server such as esd or arts, you do not have to kill all other applications that are sending audio feeds and allows for multiple audio input to the dsp device.

---

### Post by MadL on 2006-06-04
[QUOTE=BoyOfDestiny]

If the sound is out of sync (blame macromedia for using OSS). Install alsa-oss as was mentioned, then either launch firefox as 
aoss firefox
or change some setting (I've never bothered to since this is easy enough)[/QUOTE]

Tried this -- Flash audio's still out-of-sync for me (tried downloading the esound-clients package and restarting, too; same result).

---

### Post by ZipoTe on 2006-06-04
Yes. The same problem. Sound on flash it's out of sync :( i tried lots of things but they did not work.

Any Jesuscrist over there? :p

---

### Post by beuno on 2006-06-05
This fixed the problem for me:

sudo apt-get install alsa-oss
sudo nano /etc/firefox/firefoxrc

change: FIREFOX_DSP="none"
to: FIREFOX_DSP="aoss"

Thanks!

---

### Post by ZipoTe on 2006-06-05
Thanks but... i have already done this :P

By the way, when i'm watching youtube's videos my firefox crashes :S i don't know if it's the flash pulggin or maybe it has something to do with the sound... 

This Dapper Drake is giving me lots of headaches buff!!

See You!!

---

### Post by johann_p on 2006-06-06
[quote=beuno]This fixed the problem for me:

sudo apt-get install alsa-oss
sudo nano /etc/firefox/firefoxrc

change: FIREFOX_DSP="none"
to: FIREFOX_DSP="aoss"

Thanks![/quote]

This seems to fix the sound problem, but since I installed this, I have seen a couple of unusal crashes of FF. :(
I guess I will try and live with no sound in Flash until Macromedia hopefuly comes out with a version that does this right.

---

### Post by zba78 on 2006-06-06
one quickfix for this is to simply type ```
aoss firefox
``` at the terminal. You could also edit the shortcut that launches firefox to run the same command.

---

### Post by ZipoTe on 2006-06-06
Continuing with that... i found that link... and i wasn't able to reproduce it, firefox or epiphany.

_[COLOR="Blue"][http://yonkis.com/mediaflash/animacionflashera.htm]("http://yonkis.com/mediaflash/animacionflashera.htm")[/COLOR]_

I first opened with epiphany without sound and.., IT WORKS!! but when i do "aoss epiphany" it crashes!!

what is happening?? ](*,)

---

### Post by srunni on 2006-06-06
Take a look at the videodownloader FF extension; you can use it to download videos (the actual files, not the stupid flash crap) from Google Videos and YouTube, along with some other sites, and watch it in Totem (but I reccomend VLC :-)) right on your box.

---

### Post by InsaneBeast on 2006-06-13
I followed the solution from a similar thread: [http://ubuntuforums.org/showthread.php?t=187752&highlight=macromedia+flash+sound](http://ubuntuforums.org/showthread.php?t=187752&highlight=macromedia+flash+sound)
[QUOTE=Corvillus]The problem is that Flash is old and doesn't support Ubuntu's directory structure for esd properly. It wants to use /tmp/.esd/socket for the sound connection. But Ubuntu uses /tmp/.esd-<uid>/socket for the sound (the uid for the user that installed Ubuntu is 1000). A quick hack you can do to fix this is to symbolic link that directory. To do that, go to System - Preferences - Sessions - Startup programs and add
```
ln -s /tmp/.esd-1000 /tmp/.esd
```
to the list (assuming your uid is 1000, change it accordingly if it isn't), then logout and log back in. After doing this, Flash sound should work properly.[/QUOTE]

This fixed the problem for me at least.

---

### Post by Blaatann on 2006-07-11
At this point it seems to me that my choices are crappy sound using esd in firefox or really unstable firefox but good sound using aoss. 

Is there no way of using alsa with firefox in a stable fashion?

Really bummed out over this

---

### Post by Kevf on 2006-07-12
Pretty new at Ubuntu: can someone tell me how I can save the changes I've made to the sound file, using Nano?

---

### Post by detour on 2006-07-12
Ctrl-O (for write-Out), Enter to accept the filename. Ctrl-X (for Exit) to close

---

### Post by Kevf on 2006-07-13
tnx! But since I've installed the flash pluging, I've got no sound at all ](*,) 

No matter if it's on aoss or none, not even mp3's will produce any sound and it sure did before the install :-?

edit: what will happen if I deinstall Wine, while still having firefox windows installed under Wine?

---

### Post by nathandh on 2006-07-27
>  Originally Posted by Corvillus
The problem is that Flash is old and doesn't support Ubuntu's directory structure for esd properly. It wants to use /tmp/.esd/socket for the sound connection. But Ubuntu uses /tmp/.esd-<uid>/socket for the sound (the uid for the user that installed Ubuntu is 1000). A quick hack you can do to fix this is to symbolic link that directory. To do that, go to System - Preferences - Sessions - Startup programs and add
Code:

ln -s /tmp/.esd-1000 /tmp/.esd

to the list (assuming your uid is 1000, change it accordingly if it isn't), then logout and log back in. After doing this, Flash sound should work properly.
Anyone could help this newbie out where you can do this in kde?

---

### Post by dimatrod on 2006-07-28
So I'm in the no sound while having an audio program on boat.  I tried the aoss thing, but still get no sound.  Help?

---

### Post by danembraceddc on 2006-08-17
> Originally Posted by **Corvillus**
The problem is that Flash is old and doesn't support Ubuntu's directory structure for esd properly. It wants to use /tmp/.esd/socket for the sound connection. But Ubuntu uses /tmp/.esd-<uid>/socket for the sound (the uid for the user that installed Ubuntu is 1000). A quick hack you can do to fix this is to symbolic link that directory. To do that, go to System - Preferences - Sessions - Startup programs and add
Code:

ln -s /tmp/.esd-1000 /tmp/.esd

to the list (assuming your uid is 1000, change it accordingly if it isn't), then logout and log back in. After doing this, Flash sound should work properly.

Worked like a charm for me.

---

### Post by LeFou on 2006-08-20
> **nathandh said:**
> Anyone could help this newbie out where you can do this in kde?

Ditto. Trying out kubuntu...

---

### Post by jinxed on 2006-08-20
> **detour said:**
> You may be experiencing this bug: [https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760](https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760)

This fix worked for me (roughly from the comments in launchpad):

sudo apt-get install alsa-oss
sudo nano /etc/firefox/firefoxrc

change: FIREFOX_DSP="none"
to: FIREFOX_DSP="aoss"

repeat for: /etc/mozilla-firefox/mozilla-firefoxrc

Hey, thanks detour! This is exactly what the doctor ordered. It worked great.:biggrin:

---

### Post by raydar on 2006-11-21
Drat. Sure didn't work for me. 

Running Edgy with Firefox 2. To get sound, I have to kill Firefox.  To get around the fact that meant I couldn't play embedded video & hear anything, I wound up installing a standalone-player-launcher plugin.

But I had problems getting any controls or blank "screen" on pages which claimed to be showing me embedded video.  That's remedied with the plugin I mentioned, but I have been having these intermittent Firefox crashes I've heard other folks've been having.  What's the connection to the sound problem?

---

### Post by maki_03 on 2007-05-20
> **detour said:**
> You may be experiencing this bug: [https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760](https://launchpad.net/distros/ubuntu/+source/flashplugin-nonfree/+bug/29760)

This fix worked for me (roughly from the comments in launchpad):

sudo apt-get install alsa-oss
sudo nano /etc/firefox/firefoxrc

change: FIREFOX_DSP="none"
to: FIREFOX_DSP="aoss"

repeat for: /etc/mozilla-firefox/mozilla-firefoxrc

thanks! this worked perfect for me. :D I was able to play sounds in firefox while playing mp3s. :D

---

### Post by EnricoFermi on 2008-03-02
Some update, no idea what, in ubuntu managed to jack everything up.

I first managed to get audio working in general by going into System->Preferences->Sound and setting everything to OSS. I played the test sound and noticed it now was working. This then allowed mp3's to play within Rhythmbox. 

Now everything but firefox had sound.

I followed the FIREFOX_DSP="aoss" fix suggested above, with no luck.

After trying nearly everything, I realized that somehow PCM volume had just been turned down to nothing, essentially muting firefox. 

To fix this, I went into Applications->Sound Video->Sound Recorder and clicked on File->Volume control

This is where I saw that PCM had been turned down to nothing. Turned it to 11. The aoss fix above may also be necessary, so don't neglect that step.

I realize there is probably a simpler path, just opening the volume control or something, but hopefully this helps someone. It's a bit frustrating sometimes.

---

