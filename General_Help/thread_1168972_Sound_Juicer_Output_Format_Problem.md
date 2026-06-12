---
title: "Sound Juicer Output Format Problem"
date: 2009-05-24
forum: General Help
---

### Post by faustism on 2009-05-24
Hello,
I recently installed Sound Juicer on my Xubuntu system. I want to rip to MP3, that does not show up as an option when selecting the format.  I checked the profiles, and there are seven listed, but only 4 of them show up as options.  They are all set as "active".  Has anyone had this problem?

---

### Post by vk4ebp on 2009-07-16
I am having the same problem with Sound Juicer and opted for other rippers such as Asunder, ripperX, Ripoff or Grip. I would like to know what's causing this bug though. Anyone knows the answer?

---

### Post by CatKiller on 2009-07-16
For ripping to MP3, read [this]("https://help.ubuntu.com/community/CDRipping#MP3%20Encoding").

Profiles will not be displayed if the GStreamer pipeline is invalid. For example, if you try to ogg-encode an integer stream it will be invalid and be removed from the visible list. Similarly, if you don't have the libraries that will make a given pipeline element work, such as using lame in a pipeline without having LAME installed.

---

### Post by axm on 2009-09-13
> **CatKiller said:**
> For ripping to MP3, read [this]("https://help.ubuntu.com/community/CDRipping#MP3%20Encoding").

Profiles will not be displayed if the GStreamer pipeline is invalid.

Darn. That was it - I would have never expected a silently failing validation in this place.

But it is not completely true - checking might be done on startup. My first "workaround" was to change the pipeline of a selectable output method. That produced faulty output, but proved at least changes to existing entries were possible, even if not displayed in the selection.  I tried another pipeline with this way, it worked. So I stuck to the method of copying that (mp3) pipeline over that (ogg) entry pipline whenever I needed it, then reverting it.

But a new entry with this working pipeline shows up as it should in the selection. Definitely a usability issue, that there is no error if the validation fails.

---

### Post by jtellerelsberg on 2009-12-20
I'm having the same problem--mp3 is shown as an option if I click the "edit profiles" button, but is not an option in Sound Juicer output format drop list. On top of that, I'm totally new to all things linux and never was super tech savvy in windows or mac for that matter. Any chance someone has the patience to explain the "pipeline" concept further? I've seen in the synaptic package manager that several of the many gstreamer options are installed. And I've been trying to get any kind of cd-to-mp3 program working for several days now, and have been failing across the board. After having trouble at first, I managed to get Kaudiocreator to convert one cd for me, but without having changed anything or doing anything differently, it won't do it again. Grip won't work for me either. And now Sound Juicer is a fail. Argh! (And my wife wants to kill me for buying a linux box, so problems I can't solve are bigger than just a lack of mp3s!) I'm sorry to beg for hand holding, but this is getting to be more frustrating than I think it deserves to be.

---

### Post by Guitar John on 2009-12-20
Do you have all of the GStreamer plugins installed?  

FWIW, I burned the cd's into FLAC format, copied them over to my remote HDD (archived) and then used SoundConverter to transcode into mp3 format.  It gives you better control over what quality mp3's are rendered.  

SoundJuicer defaults to 128kbps for mp3 and 160kbps for ogg.

---

### Post by jtellerelsberg on 2009-12-20
Thanks for the swfit reply! Looking at Synaptic package manager, no not everything is installed. Is that really necessary? Being a newbie and all, I'm nervous about installing things labelled as being "bad" or "ugly". You've inspired me to try installing the FFmpeg plugin and see how it goes from there. I'm not picky at all about the sound quality of the resulting mp3s. 128 bit rate will be fine if that's what I get. My ideal would be vbr a little higher than that, but so be it. What matters most at this point is just plain simple functionality. With 2 toddlers at home, I get so little time to do anything on the computer that I need as much click-and-it's-done as I can find. Hmm... having now done that, the mp3 output option is still missing from Sound Juicer. I'll keep plugging away at this.

---

