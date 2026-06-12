---
title: "AAC Encoding"
date: 2006-07-16
forum: Desktop Environments
---

### Post by maiden30403 on 2006-07-16
I've been using Ubuntu for about a week now and I'm not going back to m$ windows. But I've just bought a new CD and I want to rip it to my iPod and I can't encode to AAC. I read the wiki installed everything and configured it but the files it makes don't play :( .

Any ideas?

---

### Post by Jagot on 2006-07-16
Was this what you read:

[https://help.ubuntu.com/community/CDRipping#head-61f3b32e3a56a998568cad44e305d1557e7ffee0](https://help.ubuntu.com/community/CDRipping#head-61f3b32e3a56a998568cad44e305d1557e7ffee0)

---

### Post by maiden30403 on 2006-07-16
> **Jagot said:**
> Was this what you read:

[https://help.ubuntu.com/community/CDRipping#head-61f3b32e3a56a998568cad44e305d1557e7ffee0](https://help.ubuntu.com/community/CDRipping#head-61f3b32e3a56a998568cad44e305d1557e7ffee0)

Yep that's what I followed.

---

### Post by Jagot on 2006-07-16
OK, so what do you mean they don't play?  Do you mean on your computer or on the Ipod?  If it's the computer, then you need to make sure you have the correct codecs for AAC playback:

```
sudo aptitude update
sudo aptitude install gstreamer0.10-plugins-bad-multiverse
```

---

### Post by maiden30403 on 2006-07-16
> **Jagot said:**
> OK, so what do you mean they don't play?  Do you mean on your computer or on the Ipod?  If it's the computer, then you need to make sure you have the correct codecs for AAC playback:

```
sudo aptitude update
sudo aptitude install gstreamer0.10-plugins-bad-multiverse
```


That's already installed.

I get this error in Rhythmbox

```
The MIME type of the file could not be identified
```

---

### Post by Jagot on 2006-07-16
OK, not too sure what the problem is.  Clearly not recognising the format properly, but I have installed it and my Itunes encoded .aac's play fine.

---

### Post by maiden30403 on 2006-07-16
Yea all my iTunes encoded stuff is playing just not the stuff I rip myself. Presume I'll have to use mp3 or something :( .

---

### Post by maiden30403 on 2006-07-16
Bump. Really wanna get AAC working for ripping CD's

---

### Post by perun on 2006-07-16
I've been waiting for this for awhile too. As I understand it, ffmux hasn't been ported to gstreamer-0.10 yet. Basically, you can rip to raw aac, but will not be able to play it until someone ports it over. You can always just install the old gstreamer.

---

### Post by maiden30403 on 2006-07-16
I think I have both installed how would I tell it to use the old one?

---

### Post by netztier on 2006-10-11
> **perun said:**
> I've been waiting for this for awhile too. As I understand it, ffmux hasn't been ported to gstreamer-0.10 yet. Basically, you can rip to raw aac, but will not be able to play it until someone ports it over. You can always just install the old gstreamer.

DOH!

Thanks for this info. I've been cracking my head over this back and forth, wondering why Sound Juicer when configured according to the "CDRipping" and "Restricted Formats" section in [Wiki]("https://help.ubuntu.com/community/CDRipping") with the pipeline ...

```
audio/x-raw-int,rate=44100,channels=2 ! faac ! ffmux_mp4
```

... would produce a file that no gstreamer-based application would play. XMMS did, but in the end, I'd like to have .m4b files to use as audiobooks on my iPod.

Today, I started playing around with **gst-inspect-0.10** and discovered that while there is info available for the element id3v2mux (which is suggested to use in the gstreamer pipeline to enable MP3 ripping in Sound Juicer), there is no info available for ffmux_mp4. It's not even listed when you run gst-inspect-0.10 without any parameters.

Do I conclude that the Wiki-suggested pipeline just can't properly work with gstreamer-0.10 because it would be calling an element that is not available?

best regards

Marc

---

### Post by netztier on 2006-10-11
*[double post deleted]* 

We apologize for the inconvenience

---

### Post by maiden30403 on 2007-01-05
Anyone figure this out yet. I still can't get it to work.

---

### Post by mrphd on 2007-01-05
> **maiden30403 said:**
> Anyone figure this out yet. I still can't get it to work.

I've managed to encode in AAC using the free nero digital audio aac command line encoder running under wine. The nero encoder is meant to be the highest quality aac encoder out there. I can provide more info if you are interested in using this.

---

### Post by CarsomyrXIII on 2007-03-12
To all trying to get .m4a/aac encoding in Linux, I've found a workable solution. The two programs, [soundKonverter]("http://kde-apps.org/content/show.php?content=29024"), which is a graphical front end for [audioKonverter]("http://kde-apps.org/content/show.php?content=12608"), work together to allow you to rip into just about anything. I've tested ripping CDs with it into AAC/m4a format and loaded it onto my iPod [nano] with gtkpod. It works well. Just make sure to get all the utils that audioKonvert needs. The needed packages are in Universe/Multiverse repostiories, not the gstreamer ones. I hope this helps!

---

### Post by maestrobwh1 on 2007-03-24
I had the same issues with ripping and sound juicer. AAC files were choppy and a mess. I had to rip to MP3 and then use wine with iTunes 6.05  to convert the files to aac and it was very cumbersome.

I had all the necessary items installed but it just did not work well natively in Kubuntu.  I use adept, but I suppose you can do a search in synaptic.  Just put in aac into search and install all things that look relevant.  gstreamers for aac, faac, etc.

I found this to be the most useful site in the world when it comes to multimedia
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")
Do the very first shaded area.  I changed apt-get to aptitude, as I just think it is a better thing to do.

I found this on the web:
[http://wiki.hydrogenaudio.org/index.php?title=Guide_aac_kaudiocreator]("http://wiki.hydrogenaudio.org/index.php?title=Guide_aac_kaudiocreator")
and I changed the 150 to 128 and the 21000 to 44100 to suit my needs.

So you will need kaudiocreator.  You can do this in regular ubuntu I assume.  Follow  the instructions given in the second url.

It works very well.

Peace,
Brian

---

### Post by sloggerkhan on 2007-07-15
Try using GRIP to rip the tracks. For me it seems to work way better than serpentine or sound juicer when it comes to AAC.

---

### Post by zenobiaflex on 2007-07-23
I am also having these problems with AAC... I looked at the GRIP site but it wasn't clear that I could use AAC... I have tried Sound Juicer and it gives the terribly choppy audio files... I can play iTunes ripped M4A files just fine, though.

How do I go about setting up GRIP for AAC?  Does it use gstreamer 0.1 as well?  If so, is 0.1 the problem?

Thanks for any help.. this is pretty much the last thing keeping me with Windows...

---

### Post by sloggerkhan on 2007-07-25
grip uses faac. The way to go about it is to get grip and faac from repos, click on the config tab of grip, then the encode subtab, and then the encoder subtab, and choose faac as the encoder. When you rip with grip, it will rip the whole CD as temporary raw full quality audio and then convert that to aac/m4a with faac.

---

### Post by chriswyatt on 2007-12-29
soundKonverter worked great for me, thanks.  Did require a little bit of configuration i.e. changing the CD ripping app.

---

### Post by daengbo on 2007-12-30
maiden,

I've got two answers for you. 

1) If you install the GStreamer0.10-plugins for bad and bad-multiverse, you should get the codecs you need. Open Synaptic and make sure that faac and faad are installed. Serpentine should then have an option for "CD Quality, AAC" which you can use. You don't need to follow the advice of the page you linked to. It's not necessary if you just install the restricted format package.

2) If that still doesn't work for you, you can rip the CD to WAV and encode using faac on the comman line. The command looks like *faac -o output_file.m4a --artist Metallica --album ""Kill 'Em All" --title "Seekand Destroy" track 9.wav*

I've tested both of these and they work fine for me on Gutsy 64 bit.

Cheers

Daeng
[http://ibeentoubuntu.blogspot.com](http://ibeentoubuntu.blogspot.com)

p.s. Kill 'Em All was an awesome album and got me through high school. I stopped listening to their stuff after Master of Puppets, though I still bought all their albums through to Metallica.

---

