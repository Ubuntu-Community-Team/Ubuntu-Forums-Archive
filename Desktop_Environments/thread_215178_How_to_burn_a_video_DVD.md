---
title: "How to burn a video DVD ?"
date: 2006-07-13
forum: Desktop Environments
---

### Post by abelthorne on 2006-07-13
Hello,
I have files from a video DVD (i.e. VOB, BUP, IFO, etc.) and I need to burn a disc.
I've found no way so far to burn a video DVD, either with the burning application integrated to Gnome or with other software like GnomeBaker. All I can burn is data CD, audio CD or data DVD.
Is there no way to burn a video DVD ? I find amazing that a function available for years on others OS has no equivalent with Linux software, so I guess I'm missing something there, but what ?

---

### Post by Billquinn1 on 2006-07-13
The burning software K3B has that choise built in. You may like that program a bit better.

---

### Post by someusernoob on 2006-07-13
Make a Data DVD with 2 folders:

AUDIO_TS (leave this empty)
VIDEO_TS (put here your files in)

and burn it. I've always burned my DVD's this way with Nero...under Windows tho, but should work fine with Gnomebaker, havent test it myself. Video and sound = data too.

---

### Post by Dubbayoo on 2006-07-13
[http://smorgasbord.net/convert_video_linux](http://smorgasbord.net/convert_video_linux)

you might want to view it with Opera.

---

### Post by user1397 on 2006-07-13
If the above don't work, try [this]("http://www.ubuntuforums.org/showthread.php?t=183936") guide

i would just pay attention to steps 6 and 7 since you already have the vob, bup, and ifo files.

EDIT: actually, I don't know how well my guide would do you when you're already at that stage.  o try it, and if it doesn't work, oh well.

---

### Post by abelthorne on 2006-07-13
[quote="Bilquinn1"]The burning software K3B has that choise built in. You may like that program a bit better.[/quote]

Is there no Gnome/GTK app ? I don't like KDE ones a lot... :-?

[quote="someusernoob"]Make a Data DVD with 2 folders:
AUDIO_TS (leave this empty)
VIDEO_TS (put here your files in)

and burn it. I've always burned my DVD's this way with Nero...under Windows tho, but should work fine with Gnomebaker, havent test it myself. Video and sound = data too.[/quote]

That was my main interrogation, in fact : with Nero under Windows, I've always burned video DVDs with the correct option (not data DVD). Before trying to burn with Gnome, I wondered if the fact that I couldn't find a video DVD option in softwares was du to the fact that a video DVD is only a data DVD with a certain hierarchy and type of iles.

I thought to burn my DVD in tha same way that the one you suggest, creating a VIDEO_TS directory and such but it led to nothing : the resulting DVD gives me an error message in Totem ("can't open file" or something like that), is seen as an unplayable audio CD by VLC and is not recognized by my home video player (it seems to be recognized as a DVD, but nothing is played).

So I guess that some specifications differ between a data DVD and a video DVD (like block size, filesystem used, etc.).

[quote="Dubbayoo"]http://smorgasbord.net/convert_video_linux

you might want to view it with Opera.[/quote]

[quote="erik1397"]If the above don't work, try this guide

i would just pay attention to steps 6 and 7 since you already have the vob, bup, and ifo files.[/quote]

Thanks for both links. The ISO image creation is the option that suits me the best. I'll try this.

---

### Post by abelthorne on 2006-07-13
The ISO creation method went well and the disc works as expected. Thanks a lot everyone.

---

### Post by someusernoob on 2006-07-13
> **abelthorne said:**
> 
That was my main interrogation, in fact : with Nero under Windows, I've always burned video DVDs with the correct option (not data DVD). Before trying to burn with Gnome, I wondered if the fact that I couldn't find a video DVD option in softwares was du to the fact that a video DVD is only a data DVD with a certain hierarchy and type of iles.

I thought to burn my DVD in tha same way that the one you suggest, creating a VIDEO_TS directory and such but it led to nothing : the resulting DVD gives me an error message in Totem ("can't open file" or something like that), is seen as an unplayable audio CD by VLC and is not recognized by my home video player (it seems to be recognized as a DVD, but nothing is played).

So I guess that some specifications differ between a data DVD and a video DVD (like block size, filesystem used, etc.).Interesting. I thought i had one blank DVD left, but i found out its only a cdrw, what is that doing in my blank dvd case? I want to give it a try too. So ive got to get some dvd's sometime to test it. Can play all my dvd's burned that way under Windows fine, both with stand alone players and Mplayer, VLC and Totem under Ubuntu. I've had some troubles with it in the past tho, one of the first threads i made here, that was when i used a Dapper beta release. Ubuntu didnt recognise the disks at all. Now its working great.

With Ubuntu i can even play (and rip) some old original cd's which wont work under Windows or my stand-alone cd player anymore.

---

### Post by abelthorne on 2006-07-13
> **someusernoob said:**
> Interesting. I thought i had one blank DVD left, but i found out its only a cdrw, what is that doing in my blank dvd case? I want to give it a try too. So ive got to get some dvd's sometime to test it. Can play all my dvd's burned that way under Windows fine, both with stand alone players and Mplayer, VLC and Totem under Ubuntu. I've had some troubles with it in the past tho, one of the first threads i made here, that was when i used a Dapper beta release. Ubuntu didnt recognise the disks at all. Now its working great.

Maybe Nero is smart enought to assume that if you try to burn a data DVD containing a VIDEO_TS folder, you want in fact to burn a video DVD and automatically changes the useful options ?

---

### Post by someusernoob on 2006-07-13
> **abelthorne said:**
> Maybe Nero is smart enought to assume that if you try to burn a data DVD containing a VIDEO_TS folder, you want in fact to burn a video DVD and automatically changes the useful options ?
Thats possible yes. Although it was getting a little bloated, it was a fine program for burning stuff. Havent burned that much with Gnomebaker yet (one audio cd, working fine everywhere), when i got some blank dvd's im gonna test some more. I dont burn that much (video) dvd's anymore actually. The .iso creation method looks good tho.

---

