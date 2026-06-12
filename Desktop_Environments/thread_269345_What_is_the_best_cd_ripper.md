---
title: "What is the best cd ripper?"
date: 2006-10-01
forum: Desktop Environments
---

### Post by offramp13 on 2006-10-01
What cd ripper do most people use? I havent found one i particularly like yet, so i would like some ideas.

---

### Post by skymt on 2006-10-01
I use abcde (A Better CD Encoder). It's command-line, but it always works well. It rips, encodes, tags, and files a CD in one step.

---

### Post by ardchoille on 2006-10-01
I use grip (it's a gui app) and I love it. You might need to install lame also for ripping to .ogg.

---

### Post by Josh1 on 2006-10-01
> **skymt said:**
> I use abcde (A Better CD Encoder). It's command-line, but it always works well. It rips, encodes, tags, and files a CD in one step.

Same here, if it works well, I will use it ;).
- Josh

---

### Post by offramp13 on 2006-10-01
i have grip downloaded, havent used it yet (just went through synaptic and installed all i could find) but i will check out abcde

---

### Post by MetalMusicAddict on 2006-10-01
I love Grip. Look in my sig for a guide.

---

### Post by jpkotta on 2006-10-01
abcde.  ~/.abcde.conf below.  In addition to being very easy to use once it's set up, it's the fastest one I've used.

> WAVOUTPUTDIR=$HOME/tmp
OUTPUTDIR=$HOME/music
OUTPUTFORMAT='${ARTISTFILE}/${ALBUMFILE}/${TRACKNUM} - ${TRACKFILE}'
VAOUTPUTFORMAT='Various/${ALBUMFILE}/${TRACKNUM} - ${TRACKFILE}'
OUTPUTTYPE=ogg
OGGENCOPTS='-q 5'
MAXPROCS=2
EJECTCD=y
PADTRACKS=y
EXTRAVERBOSE=y

pre_read()
{
    eject -t $CDROM
}

mungefilename()
{
    # change ':' to ' -'
    # change ' ' to '_'
    # change '/' to '-'
    # remove quotes, '?', '\', and control characters
    echo "$@" | sed s,:,\ -,g | tr \ / _- | tr -d \'\"\?\\\\\[:cntrl:\]
}


---

### Post by Cable on 2006-10-02
I used Grip, which was great, but I missed [EAC]("http://www.exactaudiocopy.de/") too much, and now use that via Wine.

---

### Post by basementgeek on 2006-10-02
> **Cable said:**
> I used Grip, which was great, but I missed [EAC]("http://www.exactaudiocopy.de/") too much, and now use that via Wine.

You might want to have a look at [Rubyripper]("http://wiki.hydrogenaudio.org/index.php?title=Rubyripper") if you want secure rips without Wine.  Inspired by EAC and written by a *nix audiophile.

---

### Post by M!K3_$ on 2006-10-02
GnomeBaker

this is an excellent burner
gnome GUI
it can burn CDs and DVDs
Data, Music, and .iso files (thats y i use it :>)
u can find it in synaptic

5 stars :KS :KS :KS :KS :KS

---

### Post by _asc_ on 2006-10-02
I use Banshee.

---

### Post by MetalMusicAddict on 2006-10-02
> **basementgeek said:**
> You might want to have a look at [Rubyripper]("http://wiki.hydrogenaudio.org/index.php?title=Rubyripper") if you want secure rips without Wine.  Inspired by EAC and written by a *nix audiophile.

Thanx for the link. :)

---

### Post by offramp13 on 2006-10-02
> **basementgeek said:**
> You might want to have a look at [Rubyripper]("http://wiki.hydrogenaudio.org/index.php?title=Rubyripper") if you want secure rips without Wine.  Inspired by EAC and written by a *nix audiophile.

so i downloaded this, and i tried to run it but it says i need a file ruby-libglade2 which isnt in synaptic and when i run ```
sudo apt-get ruby-libglade2
``` it gives me an error.

---

### Post by basementgeek on 2006-10-02
> **offramp13 said:**
> so i downloaded this, and i tried to run it but it says i need a file ruby-libglade2 which isnt in synaptic and when i run ```
sudo apt-get ruby-libglade2
``` it gives me an error.

I think I had that problem too.  I installed libglade2-ruby from Synaptic and it worked.  I don't know why it's reversed like that....maybe in the coding?  IIRC, that happened a few times to me when I first got it running.  Synaptic always has the ruby part last instead of first.

This is very much a work in progress, so it won't be without lumps.  I like it just the same!  I have a lot of scratched cd's :rolleyes:

---

### Post by offramp13 on 2006-10-02
Thanks!

except for one thing..... there is no ruby-freedb or freedb-ruby in synaptic. And i assume that is why it is not working.

---

### Post by basementgeek on 2006-10-03
> **offramp13 said:**
> Thanks!

except for one thing..... there is no ruby-freedb or freedb-ruby in synaptic. And i assume that is why it is not working.

My short term memory isn't what it used to be (just say no! :rolleyes: ), but I must have got it from here then:

[http://ruby-freedb.rubyforge.org/]("http://ruby-freedb.rubyforge.org/")

Pretty easy install from the looks of it.  Should do the trick.

---

### Post by tubasoldier on 2006-10-03
Grip is my favorite. However, if you use KDE at all you can drag and drop files from Konqueror. audiocd:/ will get you to the disk. Then open the folder you want the format to be and copy and paste into where you want them.

---

### Post by ronhaward79 on 2008-03-04
Hi, 
I am using some of the following

I am using this one for convert music files. 
[Easy CD-DA Extractor 10.0.4]("http://www.outyard.com/product/Easy-CD-DA-Extractor-1004,70001,11431.aspx")

and this one to extract and save audio tracks from CDs 

[FreeRip 2.951 - Extract and save audio tracks from CDs ]("http://www.outyard.com/product/FreeRip-2951,70001,1590.aspx")

Just have fun
Ron

---

### Post by Morimando on 2008-05-07
How about using Soundjuicer to rip the CD to FLAC and converting it with Soundkonverter to a chosen format then? That way i encode it to high-quality .m4a. Works like a charm :)

---

### Post by piratesmack on 2008-05-07
I just use the preinstalled Sound Juicer Audio CD Extractor

Applications>Sound And Video>Audio CD Extractor

You should also install the Ubuntu Restricted Extras package so you can rip to mp3

```

sudo apt-get install ubuntu-restricted-extras

```

---

### Post by rburks on 2008-05-12
Hi,

Like you I've been searching the repos for something familiar to EAC.  I found RipperX and so far like it better than all the others.  It's got a simple GUI layout and allows me to choose all the settings I need.

-Rob

---

