---
title: "Play DVDS"
date: 2006-06-05
forum: Desktop Environments
---

### Post by atomic16 on 2006-06-05
so after reading the documentation on playing DVDs im confused, ok I have totem installed I ran sudo /usr/share/doc/libdvdread3/examples/install-css.sh. I can't find xine or gxine to install. How can I play DVDS on ubuntu?

---

### Post by rado_london on 2006-06-05
You need specific codecs to play any. I dont remember the name but if you install multimedia codecs via Automatix you will get it for sure.

---

### Post by Sutekh on 2006-06-05
This is the appropriate link for getting encrypted DVDs to play.

[Ubunu Wiki - Restricted Formats - DVD Playback]("https://wiki.ubuntu.com/RestrictedFormats#head-49d7b89e22f864732e033a68a77cfe144f23af8c")

So you are saying totem-xine or gxine won't install? What happens if you use this command to install them?
```
sudo apt-get install totem-xine gxine
```Have you enabled the universe repository?  Can you post your sources.list?
 ```
cat /etc/apt/sources.list
```

---

### Post by yteh on 2006-06-05
I use totem-xine to play DVDs.

In the "About" for Totem, do you see gstreamer or xine? If gstreamer, maybe try to un-install Totem-gstreamer and install Totem-xine. You can search for Totem-xine in Synaptic.

At least this is what works for me.

---

### Post by atomic16 on 2006-06-05
Ah, Automatix works great, DVDS work, now they are watachable but jerky. I have an old pc with a slow procesor so it may be that but it is not that jerky so I was wondering if it was somthing I could fix.

---

### Post by titus1950 on 2006-06-05
[QUOTE=atomic16]Ah, Automatix works great, DVDS work, now they are watachable but jerky. I have an old pc with a slow procesor so it may be that but it is not that jerky so I was wondering if it was somthing I could fix.[/QUOTE]


Look here....

[https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

---

### Post by CybaCowboy on 2006-06-06
I followed the instructions at [https://wiki.ubuntu.com/RestrictedFormats#head-49d7b89e22f864732e033a68a77cfe144f23af8c](https://wiki.ubuntu.com/RestrictedFormats#head-49d7b89e22f864732e033a68a77cfe144f23af8c), but when I try to play a DVD movie, I am told (when I insert the disc and Totem player starts automatically):
[i]Totem could not play 'dvd:///media/cdrom1'.

No URI handler implemented for "dvd".[/i]

And when I try to play the movie by selecting "Play Disc '*title*'":
[i]Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.

Please install the necessary plugins and restart Totem to be able to play this media.[/i]


What's going on?

---

### Post by DavidW2 on 2006-06-07
[QUOTE=yteh]I use totem-xine to play DVDs.

In the "About" for Totem, do you see gstreamer or xine? If gstreamer, maybe try to un-install Totem-gstreamer and install Totem-xine. You can search for Totem-xine in Synaptic.

At least this is what works for me.[/QUOTE]

Thanks for the tip.  I was looking for a way to get Totem to work.  Also, I had been trying to find a way to make Xine the default movie player but I haven't had any luck with that.  I like this fix and will try this for a while.

---

### Post by mgmiller on 2006-06-07
totem gstreamer0.10 plays DVD's fine.  You need all the codecs installed.  It sounds like you got them if it plays.  Make sure the DMA setting for your optical drive is correct.   hdparm /dev/hdx will show what is going on in my systems drives, change the x to whatever the letter is for the correct drive.  By default, Dapper has DMA turned on.  If not,  sudo gedit /etc/hdparm.conf and change the DMA switch to on for the drive in question.  

Another thing you can try is mplayer.  Sometimes it will give a smoother playback than Totem.  You need to right click the player and go to preferences and then the misc tab.  near the bottom is the path to the optical drive you want it to use.  The DVD device line should have the path to the optical drive you want it to use.  Mine says /dev/hdc for example.  

If you find mplayer works better for DVD's for you, then in System>Preferences>Removable Drives and media go to the multimedia tab and for the Video DVD disks entry change the entry from totem dvd:// to read gmplayer dvd://  (notice it says gmplayer, not mplayer.  gmplayer starts the gui frontend for the player so you have easier control of the movie that's playing)  there are lots of skins available for mplayer to make it really pretty if you want.

good luck

Hope this helps.

---

