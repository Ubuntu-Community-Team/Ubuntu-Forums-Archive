---
title: "m4a to mp3 ?"
date: 2005-02-22
forum: Desktop Environments
---

### Post by bored2k on 2005-02-22
I have some m4a files, playback is ok thru xmms, but id like them on mp3 format.

Anyone knows how to do it ?

---

### Post by kassetra on 2005-02-22
[QUOTE=bored2k]I have some m4a files, playback is ok thru xmms, but id like them on mp3 format.

Anyone knows how to do it ?[/QUOTE]

You'll need lame and faad installed from synaptic first, but here you go:
 ```
sudo faad foobar.m4a
sudo lame foobar.wav foobar.mp3
```

---

### Post by luna6 on 2005-02-22
if you have the time to install wine...db power amp music converter runs pretty well in linux....and you can pick song(s) and select the format the format you want to convert to.....

---

### Post by kassetra on 2005-02-22
[QUOTE=luna6]if you have the time to install wine...db power amp music converter runs pretty well in linux....and you can pick song(s) and select the format the format you want to convert to.....[/QUOTE]

you can with linux as well... this was just the fastest way to convert songs... also you can use a script that automates those two commands and then just click on a song... also most of the components in ubuntu or ubuntu's repository will let you convert to many, many other formats.

---

### Post by bored2k on 2005-02-22
[QUOTE=luna6]if you have the time to install wine...db power amp music converter runs pretty well in linux....and you can pick song(s) and select the format the format you want to convert to.....[/QUOTE]

I have Crossover 4.1 Pro, but i rather do it the Linux way... je voudrais savoir plus  :grin:


Thnx a lot tho !

---

### Post by bored2k on 2005-02-22
[QUOTE=kassetra]
 ```
sudo faad foobar.m4a
sudo lame foobar.wav foobar.mp3
```[/QUOTE]


What file do i need to download to have the lame application? i cant find it thru apt-cache search !

---

### Post by kassetra on 2005-02-22
[QUOTE=bored2k]I have Crossover 4.1 Pro, but i rather do it the Linux way... je voudrais savoir plus  :grin:


Thnx a lot tho ![/QUOTE]

Let me know if you can't find lame & faad in synaptic, you might need some extra repositories.  :)

---

### Post by bored2k on 2005-02-22
[QUOTE=kassetra]Let me know if you can't find lame & faad in synaptic, you might need some extra repositories.  :)[/QUOTE]


yeah , can u please giv me those repositories?

btw, dont like synaptic, using good ol` apt-get  :p

---

### Post by kassetra on 2005-02-22
[QUOTE=bored2k]yeah , can u please giv me those repositories?

btw, dont like synaptic, using good ol` apt-get  :p[/QUOTE]

no worries, here are the extra repositories you'll probably need:

deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) warty-backports main universe restricted multiverse  

deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) warty-extras main universe restricted multiverse  

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

---

### Post by bored2k on 2005-02-22
[QUOTE=kassetra]no worries, here are the extra repositories you'll probably need:

deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) warty-backports main universe restricted multiverse  

deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) warty-extras main universe restricted multiverse  

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse[/QUOTE]


thnx a lot **kassetra** . \\:D/

---

### Post by kassetra on 2005-02-22
[QUOTE=bored2k]thnx a lot **kassetra** . \\:D/[/QUOTE]

I'm glad I could help!  Oh!  Also, if you want to use a more up-to-date xmms version (like say one that uses the gtk2 file chooser and such) try beep-media-player it's essentially xmms2, it uses all of the same themes & plugins, but it's designed for the gnome 2.x libraries.  :)

---

### Post by bored2k on 2005-02-22
[QUOTE=kassetra]I'm glad I could help!  Oh!  Also, if you want to use a more up-to-date xmms version (like say one that uses the gtk2 file chooser and such) try beep-media-player it's essentially xmms2, it uses all of the same themes & plugins, but it's designed for the gnome 2.x libraries.  :)[/QUOTE]


 :-s omG :shock:  you're just to Good  =D>


**btw, i just copied all my /usr/lib/xmms/Input plugins to /usr/lib/bmp/Input
this is really good... and prett-e

---

### Post by kassetra on 2005-02-22
[QUOTE=bored2k]:-s omG :shock:  you're just to Good  =D>


**btw, i just copied all my /usr/lib/xmms/Input plugins to /usr/lib/bmp/Input
this is really good... and prett-e[/QUOTE]

:grin:  I myself just switched from xmms to bmp, after years of using xmms.  I'm super glad you like it too!

---

### Post by SuperDiscoMachine V.5.7-3 on 2005-10-16
[QUOTE=bored2k]:-s omG :shock:  you're just to Good  =D>


**btw, i just copied all my /usr/lib/xmms/Input plugins to /usr/lib/bmp/Input
this is really good... and prett-e[/QUOTE]

Actually, BMP builds on the same crappy technology which lurks around inside XMMS. XMMS2 is a completly diffrent project:

[http://wiki.xmms2.xmms.se/index.php/Main_Page](http://wiki.xmms2.xmms.se/index.php/Main_Page)

---

### Post by cynic on 2005-12-19
For future referance..

Install faad and lame

Create an empty documant and pass this code into it..

```

#!/bin/bash
for i in *.m4a
do
	NO_SPACE=`echo $i | sed -e "s/ /_/g"`
	mv "$i" "$NO_SPACE"
done

for i in *.m4a
do
	faad $i
	lame *.wav
	rm *.wav
	rm "$i"
done

for i in *.mp3
do
	NO_WAV=`echo $i | sed -e 's/.wav//g' -e 's/_/ /g'`
	mv "$i" "$NO_WAV"
done

```

Save it as for example "mp3"

Pass it into the folder where the m4a files are located. Open an terminal and navigate to that folder.

Enter

```
bash mp3
```

All the m4a files will be converted to mp3 files and the source files will be deleted...

If you move the file to /home/<user>/.gnome2/nautilus-scripts you can just right-clik while in Nautilus and select it under scripts.. And all the files in the folder will be converted...

---

### Post by sciurus on 2006-01-03
```
#!/bin/sh
for i in *.m4a
 do
  base=`basename "$i" .m4a`
  faad -o - "$i" | lame -h -b 192 - "$base.mp3"
 done
``` mentioned [here]("http://http://www.togaware.com/linux/survivor/m4a_mp3.shtml") works for me with faad and lame installed. I run this, transfer the resulting mp3's to my mp3 player, then delete them.

---

### Post by sciurus on 2006-01-05
Here's one better- this script will preserve tags. You need to install faad, lame, and id3v2 or id3. If you prefer id3 tags, uncomment that line and comment out id3v2. If anyone can improve my method for extracting the tags, please do. I stuck this in /usr/local/bin/m4a2mp3 and changed the permissions to 755.

#!/bin/bash
for i in *.m4a
do
	base=`basename "$i" .m4a`
	info=`faad -i "$i" 2>&1`
	artist=`echo "$info" | grep artist: | sed s/artist:\ //g`
	album=`echo "$info" | grep album: | sed s/album:\ //g`
	song=`echo "$info" | grep title: | sed s/title:\ //g`
	track=`echo "$info" | grep track: | sed s/track:\ //g`
	year=`echo "$info" | grep date: | sed s/date:\ //g`
	genre=`echo "$info" | grep genre: | sed s/genre:\ //g`
	faad -w "$i"| lame -h -b 128 - "$base.mp3"
	#id3 -a "$artist" -A "$album" -t "$song" -T "$track" -y "$year" -g "$genre" "$base.mp3"
	id3v2 -a "$artist" -A "$album" -t "$song" -T "$track" -y "$year" -g "$genre" "$base.mp3"
done

---

### Post by bored2k on 2006-01-05
Whoa. Old thread. My first one here.

---

