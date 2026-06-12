---
title: "Whats up with getting Multimedia to work?"
date: 2005-12-18
forum: General Help
---

### Post by d33psix on 2005-12-18
I just installed Ubuntu 5.10 
Im trying to get the default totem program that came with it to play .mpg .avi .mp3 .wmv files but its not happening.

I installed win32 codecs package with apt as suggested from a thread posted here.
The package installed fine but totem still wont play any media files.
I dowloaded and installed the latest xine-libs (compiled from source) and installed a newer version of totem....still no go

I installed kaffeine it picked up the win32 codecs at config time but i get the same error message that i get with totem while trying to play media files. (the no codec found that could play the file or something like that)

Ive tried all the other threads on this forum but to no avail.

Is there something i dont know about yet?.

---

### Post by aysiu on 2005-12-18
[QUOTE=d33psix]
Is there something i dont know about yet?.[/QUOTE] Automatix?

---

### Post by BathroomNinja on 2005-12-18
**[Automatix]("http://www.ubuntuforums.org/showthread.php?t=66563")** is your friend.  Your really BIG friend who is also really cool and likes to help you out and by you lunch.

read through that rather long post, the automatix file is at the end of the first post.  Follow the pretty simple directions.  I had to use this to get everything working on my system.  It really does make it easy.


VV-- Learn things! why would anyone want to do that? /sarcasm

---

### Post by bionnaki on 2005-12-19
you can install automatix...

or you can just do it by hand & learn a thing or two.

follow this guide:

> 1. install various codecs from repositories

* sudo apt-get install gstreamer0.8-plugins
* sudo apt-get install gstreamer0.8-lame
* sudo apt-get install gstreamer0.8-ffmpeg
* sudo apt-get install lame
* sudo apt-get install sox
* sudo apt-get install ffmpeg
* sudo apt-get install mjpegtools
* sudo apt-get install vorbis-tools
* sudo apt-get install flac

2. then download and install w32 codec and libdvdcss2

* sudo dpkg -i w32codecs_20050412-0unofficialubuntu2_i386.deb
* sudo dpkg -i libdvdcss2_1.2.8-1unofficialubuntu3_i386.deb

3. REGISTER codecs with the command

* gst-register-0.8

4. Get and install xine (or gxine - what I prefer on gnome)

* sudo apt-get install gxine

---

### Post by ronmarley1 on 2005-12-19
[QUOTE=bionnaki]you can install automatix...

or you can just do it by hand & learn a thing or two.

follow this guide:[/QUOTE]

Hi bionnaki,
You are right!  When I first found out about automatix, I said, "Man, I wish I had this three months ago."  Then I realized that I learned a ton from installing all of that stuff manually.  So true...

---

### Post by bmarilena on 2005-12-22
[quote=bionnaki]you can install automatix...

or you can just do it by hand & learn a thing or two.

follow this guide:[/quote]
Hi there
I just followed the guide you posted here and... is not working...
some of the packages didn't install... no candidate... says the E line.
What should I do in this case?
I would really like to listen to my old mp3's and to see some of the movies my friends are sending to me.
Marilena

---

### Post by KurtB on 2005-12-22
I also had troubles playing multimedia...

My solutions:
1. add the universe repository in synaptic package manager
2. for mp3 -> search & install xmms, it works great
3. for avi, mpeg, divx & video stuff -> search & install VLC (it only hangs when I try to play a DVD, haven't figured out why yet...)

grtz,
KurtB

---

### Post by bmarilena on 2005-12-22
[quote=KurtB]I also had troubles playing multimedia...

My solutions:
1. add the universe repository in synaptic package manager
2. for mp3 -> search & install xmms, it works great
3. for avi, mpeg, divx & video stuff -> search & install VLC (it only hangs when I try to play a DVD, haven't figured out why yet...)

grtz,
KurtB[/quote]
Thanks! can you give me a link to a howto or guide... something to do what you suggested? For now... some files are woking, some not... have no idea why. I mean some vmw are working and some are not... the same tipe...
Thanks again
Marilena

---

### Post by KurtB on 2005-12-22
Sure,

[this](http://www.ubuntuforums.org/showthread.php?t=68056&highlight=installing+vlc) thread got me started.

espacially last post of rwabel that explains that you need to add the universe repository to install it (you can add these simply in Synaptic Package manager and then search for vlc)

The same way you can install xmms for playing mp3s.

Now for the video's that don't always work -> I'm still looking around to get this fixed (as I mentioned, my DVD for example start but then I get a lot of purple/green artifacts and the application hangs)

it works fine for avi's (mostly divx) and plays every mpeg I got. Haven't tested any quicktime trailers though because FireFox always want to start Totem...

---

### Post by bmarilena on 2005-12-22
[quote=KurtB]Sure,

[this]("http://www.ubuntuforums.org/showthread.php?t=68056&highlight=installing+vlc") thread got me started.

espacially last post of rwabel that explains that you need to add the universe repository to install it (you can add these simply in Synaptic Package manager and then search for vlc)

The same way you can install xmms for playing mp3s.

Now for the video's that don't always work -> I'm still looking around to get this fixed (as I mentioned, my DVD for example start but then I get a lot of purple/green artifacts and the application hangs)

it works fine for avi's (mostly divx) and plays every mpeg I got. Haven't tested any quicktime trailers though because FireFox always want to start Totem...[/quote]

Thanks again. I have problems with vmw's. And unfortunately I have to see quite lots of these movies. Some of them are working fine... others... are starting well and after few seconds... are changing frames late... with a bigger and bigger delay until... stucks.
Have no idea why.
Thanks again
Marilena

---

### Post by KurtB on 2005-12-22
I was still looking around on the forum for solving my issues too, when I found this tutorial: [http://ubuntuforums.org/showthread.php?t=75278](http://ubuntuforums.org/showthread.php?t=75278)

It's another program (totem-xine), but it uses w32 codecs you need to install.

I haven't tried it yet (will be something for tomorrow in my case I guess)...but the posters claim that you can play just about any audio/video file afterwards...

which sounds good, because I really want to play DVD's :)

---

### Post by annsachd on 2006-02-06
Xine solved a lot of my problems along with the w32codecs for .mov etc. DVDs play fine in it.

---

