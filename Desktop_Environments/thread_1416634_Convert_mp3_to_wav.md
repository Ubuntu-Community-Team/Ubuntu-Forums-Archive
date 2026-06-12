---
title: "Convert mp3 to wav"
date: 2010-02-26
forum: Desktop Environments
---

### Post by carsonrose on 2010-02-26
I think if I convert a bunch of mp3's to wav, then burn to a blank DVD, it should work as one long audio dvd right?

I have about 400 mp3 files in a folder. How do I convert them all at once, Im sure it would take a while, but how would I convert them all at once and then burn to a blank DVD?

Please help.

Thanks, 

Doug

---

### Post by Kakers on 2010-02-26
Depends on what you playing it on really... if your playing it on the pc... won't really matter if it is wav or mp3.. a lot of cd/dvd players will play mp3 not all of them will play wav files.

So sort answer yes, depending on how you play it.

Could try Pearl audio converter: [http://linuxappfinder.com/package/pacpl](http://linuxappfinder.com/package/pacpl)

---

### Post by cozmicharlie on 2010-03-06
Yes PACPL will work for this.  Follow the tutorial here [http://ubuntuforums.org/showthread.php?t=712064&highlight=pacpl](http://ubuntuforums.org/showthread.php?t=712064&highlight=pacpl)
Note though that PACPL is now in the repository (multimedia universe repository)so you can install it right from Synaptic.

You run pacpl in the terminal (unless you are using kubuntu or have KDE).  It is easy though and you could write a simple script if needed.

The command to use:
$ pacpl --to wav your/files

You can just drag the entire folder over to the terminal or individual files. One item you need to watch for is if you have files with spaces - make sure and put quotes around them (example: /home/music/Over The Rainbow should be "/home/music/Over The Rainbow"). There are other options such as moving to a new directory, some tagging etc etc.  See the tutorial or if you need any help post back.  

In Ubuntu, Soundconverter (install from apt-get or synaptic)is a good program.  I also like SoundKonverter but it is kde and some people don't like to install all the dependencies.  Both have a nice GUI so they are easy.  Make sure you install all the proper codecs.  If you have the Ubuntu restricted extras installed you should be good to go.

Lots of options.
Enjoy!

---

### Post by wojox on 2010-03-06
Audacity is another good one.

---

### Post by asmoore82 on 2010-03-06
> **carsonrose said:**
> I think if I convert a bunch of mp3's to wav, then burn to a blank DVD, it should work as one long audio dvd right

If you're trying to make a true Audio DVD, your burning software should handle
the conversion from *.mp3 to CDDA(which is pretty much wav) for you.

If you still want/need to convert hands-on, I would use `sox`
just make sure you have the sox's mp3 package installed as well...

```
sudo apt-get install sox libsox-fmt-mp3
```

and then:
```
find Music/ -iname "*.mp3" -exec sox -V3 {} {}.SOX-CONVERTED.wav \; 
```

---

### Post by andrea000 on 2010-03-07
Sound converter is another it converts to and from
about any format and has a easy to use gui.

---

### Post by carsonrose on 2010-07-05
> **asmoore82 said:**
> If you're trying to make a true Audio DVD, your burning software should handle
the conversion from *.mp3 to CDDA(which is pretty much wav) for you.

If you still want/need to convert hands-on, I would use `sox`
just make sure you have the sox's mp3 package installed as well...

```
sudo apt-get install sox libsox-fmt-mp3
```and then:
```
find Music/ -iname "*.mp3" -exec sox -V3 {} {}.SOX-CONVERTED.wav \; 
```


Worked great!! Thanks!

---

