---
title: "can't rip CD to mp3"
date: 2009-05-03
forum: General Help
---

### Post by mamboze on 2009-05-03
I installed 8.10 on an Acer Aspire 4520 laptop a few weeks ago. I want to rip a CD to mp3 but neither sound juicer nor rhythmbox rips to mp3. I've checked out online and found this suggested as a way to implement mp3 capability in sound juicer:

sudo apt-get install ubuntu-restricted-extras

Is this an OK way to go? or are there better alternatives, like other linux CD rippers? 

Thanks for any help

---

### Post by squaregoldfish on 2009-05-03
[grip]("http://nostatic.org/grip/") works pretty well for me. It's available in the repositories.

Steve.

---

### Post by vitaraq1962 on 2009-05-03
It should work, although if you go to add remove programs and set all avaiable applications. You should then find the restricted extras package there. That is the method i always use and i have never had a problem with mp3's. Also this package gives you ms fonts and loads of other usfull things. I hope this helps.

Gaz

---

### Post by delcypher on 2009-05-03
grip never worked for me. I use ripperX which works fine. It's in the repositories.

---

### Post by Linux&amp;Gsus on 2009-05-03
Necessary codecs installed? Like Lame or what ever they're called.
Can you play MP3 files? Can you rip to OGG?

---

### Post by mamboze on 2009-05-03
Sorry for the delayed reply, my ISP went ultra slow last night.

Tried to install ubuntu-restricted-extras thru add/remove but got this message:

[B]Cannot install 'ubuntu-restricted-extras'

This application conflicts with other installed software. To install 'ubuntu-restricted-extras' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.[/B]

This may be due to my installing MS fonts for OpenOffice. I don't know which software is conflicting tho

Can rip to .oga, is this OGG format? sorry for my ignorance. I haven't installed LAME, this is part of the restricted-extras package, I think.

---

### Post by SuperSonic4 on 2009-05-03
The restricted extras is just a metapackage, you can grab lame on it's on from synaptic or terminal: ```
sudo apt-get install lame
```

---

### Post by zvacet on 2009-05-03
Sound juicer have problems with ripping mp3

> WARNING: the gstreamer LAME plugin, used in the instructions below, is broken and will produce substandard quality MP3s. You can track the bug here. If you want to create MP3s, it is recommended not to use Sound Juicer; use a program that doesn't interface with LAME through gstreamer instead. Good examples are RubyRipper and ABCDE.

Taken from [here.]("https://help.ubuntu.com/community/CDRipping")

---

### Post by SuperSonic4 on 2009-05-03
There is always those two programs or another codec. Perhaps using lame proper instead of gstreamer lame may work?

---

### Post by mamboze on 2009-05-04
Well, some progress to report:

I did 'sudo apt-get install lame' and rebooted.

Now sound juicer edit>preferences>edit profiles   shows  'CD Quality, MP3' among the Gnome Audio Profiles,  
selecting 'Edit' shows
**Profile name:** CD Quality, MP3 
**Profile description:**  Used for converting to CD-quality audio, but with the lossy MP3 codec. Use this for preparing files for copying to devices that only support the MP3 codec. Note that using this format may be illegal in your jurisdiction; contact your lawyer for advice. 
**Profile name:** CD Quality, MP3
**GStreamer pipeline:** audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux
**File extension:** MP3
Active box ticked
but the MP3 profile doesn't come up in the Preferences Output Format drop down box. I can't see how to select the MP3 option when extracting.

---

### Post by TunaCanTommy on 2009-05-04
Make sure you have the "Active?" box ticked in the profile editing window.

---

### Post by mamboze on 2009-05-04
Yes, I have the Active box ticked, but still no joy. So I've installed ripperX from the repositories and it works OK. I'll go with it.

Thanks to all for your help, it is really very much appreciated. 

Ubuntu forums rock, for sure. :)

---

### Post by logos34 on 2009-05-04
> **mamboze said:**
> Yes, I have the Active box ticked, but still no joy. So I've installed ripperX from the repositories and it works OK. I'll go with it.


Just as well--ripperX is better than Sound juicer (anything is, frankly).  SJ and the gstreamer engine, with its finicky, convoluted pipelines, is just more hassle than it's worth

---

### Post by greazeball on 2009-05-07
> **SuperSonic4 said:**
> The restricted extras is just a metapackage, you can grab lame on it's on from synaptic or terminal: ```
sudo apt-get install lame
```

Thanks for this!

^^^ and about ripperX too!

---

### Post by gregb49 on 2009-05-18
Plus, remember to change the configuration of **GRIP** to use **Lame**, once you've installed **Lame**; (**Config - Encode - Encoder**). Obvious to some, I'm sure, but it wasn't to me! Mine was set to **mp3encode**, probably by me during an earlier attempt to get the MP3 encoding to work.

---

