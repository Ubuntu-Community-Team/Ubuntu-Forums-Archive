---
title: "Ripping to mp3"
date: 2006-03-13
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-03-13
I want to rip my CD collection to mp3 (to burn it on a DVD and play it).
I'm looking for a good ripper, preferrably command line, that will rip, encode, and mainly organize the albums by artist and album.
No ogg ripper, as I don't know any DVD player that reads ogg. Does any one?

G

---

### Post by hw-tph on 2006-03-13
If you want a command line ripper, try abcde. It is in the universe repositories.

For encoder I suggest Lame 3.97b. The new VBR algorithms make it very quick and the quality is excellent. Grab it at Sourceforge. The tarball includes a debian directory so building a .deb is a breeze (**cd /path/to/source && fakeroot debian/rules binary**).


Håkan

---

### Post by Madpilot on 2006-03-13
SoundJuicer isn't command line, but it does everything else you're asking about.

You need to do a little bit of tweaking to get it to burn mp3, but that's nicely laid out here: [https://wiki.ubuntu.com/CDRipping](https://wiki.ubuntu.com/CDRipping)

---

### Post by codejunkie on 2006-03-13
[QUOTE=GabrielWolff]I want to rip my CD collection to mp3 (to burn it on a DVD and play it).
I'm looking for a good ripper, preferrably command line, that will rip, encode, and mainly organize the albums by artist and album.
No ogg ripper, as I don't know any DVD player that reads ogg. Does any one?

G[/QUOTE]
try lame & grip```
sudo apt-get install lame grip
```and grip will rip the .wav files and use lame to automatically convert them to mp3 and organize them.

---

### Post by GabrielWolff on 2006-03-13
[QUOTE=hw-tph]If you want a command line ripper, try abcde. It is in the universe repositories.

For encoder I suggest Lame 3.97b. The new VBR algorithms make it very quick and the quality is excellent. Grab it at Sourceforge. The tarball includes a debian directory so building a .deb is a breeze (**cd /path/to/source && fakeroot debian/rules binary**).


Håkan[/QUOTE]

Thanx. I think I'll go with abcde.
Next question: How do I make the application rip the CD in a foöder with the Artist's name, and a subfolder with the Album's name (like grip does)
For example: An Album called "Rumpelstilzchen" recorded by Hänsel und Gretel would be there: XXX/Music/Hänsel und Gretel/Rumpelstilzchen
Any idea?

---

### Post by dpaint4 on 2006-03-13
I just switched from Windows and something I miss so far has been being able to use the latest codecs. You mentioned being able to use LAME 3.97b2, which was my favorite MP3 codec because of the new algorithms and faster encodes.

I downloaded the source, compiled and attempted to install the resulting .deb.

It would have gone well, but the install failed because it was going to overwrite some files from my 3.96 installation.

So I went to my package manager to uninstall 3.96, assuming it'd be no big deal because I'd be replacing it with 3.97.  

Well, Synaptic was just about to uninstall like ALL of my media applications when I told it to uninstall 3.96.

Is there a safe way?

The thing I miss about Windows was that the entire codec lived in a cute little dll file that just sat in my home folder with my other codecs and conflicted with nothing, replaced nothing, and was only used by the applications that I pointed to it with.

Get my drift? Am I just missing something. Being 2 weeks into using Ubuntu as my only OS, I have to say that I'm shocked and impressed both by the complicated things that have become easy and by the easy things that have become complicated.

How are you using your 3.97 installation? Is there some way that I can make it independant such as not to destroy all the applications that seemingly depend on 3.96?

---

### Post by dpaint4 on 2006-03-13
AND ANOTHER THING!!! :)

What's up with Grip's Lame switches? The look like no lame switches I've ever seen. I'm used to getting to say like... 

```
--preset fast extreme 
```

I tried to edit the switches in Grip, and the default was:

```
-h -b %b %w %m
```

What the heck is ***that?!***

I'm so lost. I thought Lame was basically lame. But it's like I landed on Mars or something.

Basically all I want in the whole wide world is a good old lame 3.97b2 MP3 at --preset fast normal.

I will do absolutely anything you tell me to do to be able to make those again. I'm okay with the terminal. Whatever it takes. Anyone?

---

### Post by littlewing0906 on 2006-03-31
[QUOTE=dpaint4]AND ANOTHER THING!!! :)

What's up with Grip's Lame switches? The look like no lame switches I've ever seen. I'm used to getting to say like... 

```
--preset fast extreme 
```

I tried to edit the switches in Grip, and the default was:

```
-h -b %b %w %m
```

What the heck is ***that?!***

I'm so lost. I thought Lame was basically lame. But it's like I landed on Mars or something.

Basically all I want in the whole wide world is a good old lame 3.97b2 MP3 at --preset fast normal.

I will do absolutely anything you tell me to do to be able to make those again. I'm okay with the terminal. Whatever it takes. Anyone?[/QUOTE]

grip uses some placeholders for the information in the config tab.  The placeholders are similar to the lame command line switches.

I recommend visiting [http://sourceforge.net/mailarchive/forum.php?thread_id=9246192&forum_id=5958](http://sourceforge.net/mailarchive/forum.php?thread_id=9246192&forum_id=5958) from the grip help.  There is an interesting thread on switches etc.  You should be able to find out what is going on better with grip and lame there.

---

