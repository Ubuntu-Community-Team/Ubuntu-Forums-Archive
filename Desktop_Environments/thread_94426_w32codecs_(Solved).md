---
title: "w32codecs (Solved)"
date: 2005-11-24
forum: Desktop Environments
---

### Post by migueljacq on 2005-11-24
Can anyone help me locate the w32codecs? I can't watch any video media and they won't install through apt-get with that name like they did in Hoary. Are they located somewhere else/got a new name/not available anymore?

Thanks

---

### Post by aysiu on 2005-11-24
It's out of the Ubuntu repositories for legal reasons.
Download [this](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb) to your desktop. Pop open a terminal and type in ```
cd Desktop
sudo dpkg -i w32codecs_20050412-0.0_i386.deb
```

---

### Post by manicka on 2005-11-24
[http://doc.gwos.org/index.php/PLF](http://doc.gwos.org/index.php/PLF)

---

### Post by migueljacq on 2005-11-24
Cheers for the quick responses :)

---

### Post by Azyx on 2005-11-24
I don't know what w32codecs are, but is you problem that you don't can see any video?

The is a videoplayer vlc that you can get thuoght apt-get or synaptic, and it can show almost any videoformat and it has no external codecs you have to search for.
/azyx

---

### Post by cheirekov on 2005-11-24
OK .
The codecs were installed, but now what..
how to choose wich codec "totem " to use instead of gstramer 0.8 codecs ?
wich movie player to chouse when i whant a DivX and XviD support (something like MV2Player or BSPplayer) and how to adjust cyrilic subtitles ....
i made some test.
1. from AddAplications i can not install Mplayer (My hardware platform error somting)
2. from Synaptic mplayer were installed but someting like subfond.ttf missing and no subtitles
3. Totem player can`t display CD1251 subtitles i try which totem_config thing but nothing happened
4. I Use VLC player and yes It Playes Everything but it has it`s own codec and you can`t change it
What Player should i use to plasy Everykind of movies (DivX XviD mpeg2 wmv asf) that has cyrilic subtitle support and multi codec support  ??? :confused:

---

### Post by Biased turkey on 2005-11-24
It's all there:
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-music-and-movies")

Consult the Applications-> Music and movies section.
And it works if you follow the procedure line by line. It's long but not complicated.

---

### Post by jimbob on 2005-11-24
Every time I run vlc it has no audio even though I turn the volume all the way up.   

Mplayer works fine.    Anyone else had this problem?

---

### Post by aaso on 2005-12-08
[QUOTE=aysiu]It's out of the Ubuntu repositories for legal reasons.
Download [this](ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb) to your desktop. Pop open a terminal and type in ```
cd Desktop
sudo dpkg -i w32codecs_20050412-0.0_i386.deb
```[/QUOTE]

this doesn't work in my Breezy for Totem of Gxine
are there more steps to follow?


previously I followed all the codecs steps in the ubuntuguide.org

---

### Post by Ampersand on 2005-12-08
[QUOTE=jimbob]Every time I run vlc it has no audio even though I turn the volume all the way up.   

Mplayer works fine.    Anyone else had this problem?[/QUOTE]

Have you tried going through the audio section in the VLC preferences? Changing the output module between OSS and ALSA sometimes helps (you'll have to enable Advanced options at the bottom). Also, do you have any other programs running that use the soundcard? That sometimes stops it from working.

---

### Post by manicka on 2005-12-08
[QUOTE=aaso]this doesn't work in my Breezy for Totem of Gxine
are there more steps to follow?


previously I followed all the codecs steps in the ubuntuguide.org[/QUOTE]

Try the advice here  [http://doc.gwos.org/index.php/PLF](http://doc.gwos.org/index.php/PLF)

---

