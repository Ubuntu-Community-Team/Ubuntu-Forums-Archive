---
title: "Sound in ET&gt; /proc/asound/card0/pcm0p/oss"
date: 2005-04-28
forum: Gaming &amp; Leisure
---

### Post by charel on 2005-04-28
Hello,

to have Sound in Enemy Territory, i have to open a root console, and type in:

echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss 

and it works fine. (it was the same for SuSe) Sound in KDE/Gnome is working fine, but for Et I need these commands.

But I have no idea what it means. Can someone explain me what these commands are doing exactly?

A second question about the Soundmixer. I want to use Teamspeak. Which Soundmixer is the right one to use?

thank for any help

---

### Post by jdodson on 2005-04-28
[QUOTE=charel]
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss 
[/QUOTE]

basically you are "forcing" the program to direct the sound output to oss sound module and not alsa.  i have to use that command to get quake1 to work.

---

### Post by charel on 2005-04-28
Thank you!  :smile: 

I dont like using commands whithout understanding what it means.

---

### Post by zuzuzzzip on 2007-07-30
didn't work for me, i think i need alsa and not oss (had to set this in wine for half-life 2 also)

and how do you undo these commands? :P

nm worked like a charm :D

---

### Post by zuzuzzzip on 2007-08-01
is there a way to automate this at startup? I have to do it everytime a startup my pc and I have to do it otherwise my sound doesn't work in my 32 bit applications...

edit:  its not true. It was just rhytmbox using my sound device

---

