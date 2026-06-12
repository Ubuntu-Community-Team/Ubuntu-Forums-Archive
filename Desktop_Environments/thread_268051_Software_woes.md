---
title: "Software woes"
date: 2006-09-29
forum: Desktop Environments
---

### Post by kauf on 2006-09-29
I'm still very new to Ubuntu and Linux in general... so bear with me if these seem simple to fix.

I love to download torrents, I was an early adopter of uTorrent and loved running that on windows.  Now, under linux I ran the simple BitTorrent program that comes bundled with Ubuntu, it sucks in my opinion.  I read some reviews of Linux torrent clients and tried qBitTorrent... doesn't meet my needs (my ISP throttles).  

I then thought "Hey, I can just install WINE and run uTorrent through that."    I went to the WINE main site, did all the stuff they said I should to install it and get it working... but no dice.  It doesn't show up in my Applications menu or in the add/remove list.  I probably messed up the install, so I'll just redo it... but then there is another issue I have.

Mplayer... I like it, but I don't have the right codecs installed, supposedly you just need to paste them in the codec folder, yet I cannot find it (I looked where some people have written to look).  I also read that the codecs need to be placed in the folder prior to installing Mplayer.  Logically I thought I should uninstall Mplayer then paste the codecs in /usr/local/share/codec (that's where people say to put 'em... or something to that effect) and reinstall Mplayer.  Why haven't I done that?  Because Mplayer isn't in my add/remove list, however unlike WINE it is in my Applications menu and I can run it.

I have done searches for WINE/Mplayer/codec on my system and haven't found any folder for either that would help me much.


Any help?

---

### Post by Kateikyoushi on 2006-09-29
I also used utorrent in windows but rtorrent does it for me, give it a try and do not let the terminal scare you it is quite good.

This can help with installing the codecs.

[Restricted formats.]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by kauf on 2006-09-29
I just read in another thread "You probably need to click on the 'Show unsupported applications' and 'Show commercial applications' checkboxes to see it." It was in reference to Java... but still applies to me... I have found WINE and Mplayer in the add/remove list... sweet.

edit: The terminal does seem daunting and I only use it when someone posts specific code that I should use.  I grasp the concepts of it but am not comfortable to just fool around with it.

---

### Post by Kateikyoushi on 2006-09-29
Erm it does not mean you have to type commands to use rtorrent.
It means does not have a gui and can not use it with the mouse.

[Screenshots]("http://linux.softpedia.com/progScreenshots/rTorrent-Screenshot-2673.html")

To install w32codecs you have to add repositories.

[Here is a guide]("https://help.ubuntu.com/community/Repositories/Ubuntu").

---

### Post by kauf on 2006-09-29
Damnit... I had all this stuff written out then hit go advanced (not post quick reply)... lost it all.

So, I see WINE in add/remove but I don't know where the program should appear so I can run it, I've looked through all the drop down menus.  Where should it be?  Should I just reinstall it because I messed it up somehow?  

My ISP throttles connections so I cannot efficiently use torrents unless the client uses encryption or whatever it was that uTorrent basically pioneered.  Hence I need WINE since I haven't seen a Linux client which will get past the throttling.

I didn't realized you meant rTorrent's lack of GUI, I thought you meant the terminal in general.

I've installed the w32codecs, yet I still get an error while trying to play TV shows I have on my computer... XVID's.  

> Error!
alsa-control: unable to find simple control 'PCM',0

Another problem I have, related through alsa, is my flash player.  I can watch videos on youtube fine, kinda... no audio.  I went through all the steps to fix it in that Restricted Formats page but got lost when it says I need to get the alsa-oss package.  I tried sudo apt-get alsa-oss... no dice.

That's all for now... thanks for the help.

---

### Post by pseudonym on 2006-09-29
> **kauf said:**
> My ISP throttles connections so I cannot efficiently use torrents unless the client uses encryption or whatever it was that uTorrent basically pioneered.  Hence I need WINE since I haven't seen a Linux client which will get past the throttling. First make sure utorrent is working before worrying about the menu. Fire up a terminal and cd to the folder which contains the utorrent.exe . It's probably somewhere on your 'fake' c_drive in the /home/<your_user_name>/.wine directory. Then type - ```
wine utorrent.exe
``` or whatever the filename is.

> **kauf said:**
> I've installed the w32codecs, yet I still get an error while trying to play TV shows I have on my computer... XVID's. What program are you using to play them with?  

> **kauf said:**
> Another problem I have, related through alsa, is my flash player.  I can watch videos on youtube fine, kinda... no audio.  I went through all the steps to fix it in that Restricted Formats page but got lost when it says I need to get the alsa-oss package.  I tried sudo apt-get alsa-oss... no dice That should be - ```
sudo apt-get install alsa-oss
```

---

### Post by kauf on 2006-09-30
I was using Mplayer, however I am installing VLC right now.  Maybe that will work?  I tried to install alsa-oss but it still doesn't work
> Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package asla-oss

I dunno, maybe it's something to do with repositories, but I already did that, opening up to multiverse and universe.

I'll try some more with wine later, but I really don't see any folders relating to it, yet it appears in the add/remove list as being installed.  I'll probably uninstall and reinstall WINE, thats the only thing I can think of on my own.  

Night.

---

### Post by pseudonym on 2006-09-30
> **kauf said:**
> I was using Mplayer, however I am installing VLC right now.  Maybe that will work?   Try installaing the ffmpeg plugin - ```
sudo apt-get install gstreamer0.10-ffmpeg
Ctrl-Alt-Backspace to restart Gnome
```

> **kauf said:**
> I tried to install alsa-oss but it still doesn't work Try this for your flash issue - ```
sudo apt-get install alsa-oss
sudo gedit /etc/firefox/firefoxrc

FIREFOX_DSP=”aoss”
```

> **kauf said:**
> I'll try some more with wine later, but I really don't see any folders relating to it, yet it appears in the add/remove list as being installed.  I'll probably uninstall and reinstall WINE, thats the only thing I can think of on my own. It's in a hidden directory. In linux, all directories/files with a '.' at the beginning are hidden. Locate your wine directory by enabling 'show hidden folders and files' (or whatever the option is) in Nautilus, or in the terminal cd to /home/<yourusername>/.wine .

---

### Post by liquilife on 2006-09-30
Having the same issue with Firefox and flash with no sound. I tried your trick to resolve the issue. No dice. I've still got no sound in flash and Firefox.

---

### Post by kauf on 2006-09-30
VLC works like a charm, really don't know why Mplayer is having trouble with certain videos.  One of the first things I did was to install a lot of those gstreamer codecs... I have them but Mplayer is just whack.  

I can't really use your code to fix firefox-flash sound... when I input the first line I get that error I posted last night.  I assume the other lines of code depend on the first line being successful.

Thanks for the insight in how linux works (.'s = hidden), yet I flicked on show hidden files, looked at my home folder and found nothing... but folders for other programs not WINE.

So, I don't care for Mplayer got VLC now, WINE is more hidden than it should be (planning to reinstall sometime soon), and flash still has no sound in firefox with a bleak future.

---

### Post by liquilife on 2006-10-02
Well, I was able to get my sound in flash resolved as well as numerous little issues I was having in Firefox for all types of media. I was using swiftfox this whole time. Once I went back to Firefox the flash sound and embedded wmv files and realplayer files worked like a charm. Good enough for now.

---

### Post by kauf on 2006-10-04
I'm pretty sure I messed something up along the way with regards to installing codecs.  EasyUbuntu won't work because I messed stuff up earlier.  
I think it's best if I just reinstall Ubuntu and now with some experience under my belt get it working without any hitches.  Then maybe I can mess it up again by doing something more advanced. lol

---

