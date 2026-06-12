---
title: "guitar utils on ubuntu"
date: 2005-08-15
forum: Desktop Environments
---

### Post by clapton on 2005-08-15
I'm a music lover, and a guitar lover.
And I've got difficulty to get utilitys from guitar to my ubuntu.

somebody can Help?
guitar processors, tuner's like we found easily to m$, guitarFX for example.

---

### Post by PeP on 2005-08-15
if you want an overview of the guitars program available with ubuntu:
allow extra repositories (-> ubuntuguide.org for a howto)

then open synaptic and search for guitar (set the search to name and contents)

---

### Post by RastaMahata on 2005-08-15
[QUOTE=PeP]if you want an overview of the guitars program available with ubuntu:
allow extra repositories (-> ubuntuguide.org for a howto)

then open synaptic and search for guitar (set the search to name and contents)[/QUOTE]
 heh...> **guiTAR** is a TAR extraction tool written in GTK+ and including GNOME
support. It currently supports the tar, tar.Z, tar.gz, tar.bz2, lha,
lzh, rar, arj, zip, and slp formats.

---

### Post by matthew on 2005-08-15
In the repositories you can try gnometab, gtkguittune, and songwrite.

Next, try a google search using the key words "guitar linux" and see what you find. Report back with any interesting looking stuff.

---

### Post by PeP on 2005-08-15
[QUOTE=RastaMahata]heh.. heh...
Quote:
guiTAR is a TAR extraction tool written in GTK+ and including GNOME
 support. It currently supports the tar, tar.Z, tar.gz, tar.bz2, lha,
 lzh, rar, arj, zip, and slp formats. .[/QUOTE]

well then? that's why I wrote search for name **and contents**

then the package description is explicit enough to make the difference between packages associated with the archiver and those associated with music.

---

### Post by clapton on 2005-08-18
I can findo creox, but It didn't work good.

BEcause a jack-sever ou something :X.

I want something to guitar processor :)

---

### Post by RaymondQE on 2005-08-18
Haven't tried it yet, but there is a program called GNUitar.  You'd have to compile it from source though since it is not in the repositories.

---

### Post by clapton on 2005-08-18
I've tried, but without results, is it ubuntu anti-guitar? ;)

---

### Post by matthew on 2005-08-18
[QUOTE=clapton]I've tried, but without results, is it ubuntu anti-guitar? ;)[/QUOTE]
No. (See my avatar...that's one of my 7 guitars) There just hasn't been anyone with the time/inclination to write a lot of guitar-related software for Linux that has made its way into Debian and then Ubuntu. Looking for a job? No money, but you would earn the respect of all us Ubuntu guitar players.

---

### Post by clapton on 2005-08-23
[QUOTE=matthew]No. (See my avatar...that's one of my 7 guitars) There just hasn't been anyone with the time/inclination to write a lot of guitar-related software for Linux that has made its way into Debian and then Ubuntu. Looking for a job? No money, but you would earn the respect of all us Ubuntu guitar players.[/QUOTE]

Hmm, your avatar seems a telecaster =)
Yes, I'm interested to help, tell me how  :-P

---

### Post by shanghaipi on 2005-08-23
while you guys are at it, can you port sonar4 for me?

chuckle chuckle....

---

### Post by matthew on 2005-08-23
[QUOTE=clapton]Hmm, your avatar seems a telecaster =)
Yes, I'm interested to help, tell me how  :-P[/QUOTE]
It is a Telecaster! Since that picture was taken it has been modified with a humbucker in the neck position and a 5 way pickup switch.

The help I was referring to was this: if you know how to program and have an idea for something you would like to see available for Linux...specifically for guitar users...the guitar playing community would cheer your name loudly and you would be a very popular man. I didn't really have anything specific in mind. I have found, though, most good programs in te OSS world are written by people who are just excited about something they love and didn't find what they wanted so they wrote it with the specific features they were looking for.

I wish I had a project myself, but I'm not a programmer, I'm a musician and a writer that enjoys being a wanna-be techno-geek. :)

---

### Post by matthew on 2005-08-23
[QUOTE=shanghaipi]while you guys are at it, can you port sonar4 for me?

chuckle chuckle....[/QUOTE]
lol.  You might take a look at Rosegarden, Audacity, or Ardour. There are a few others as well. I haven't found anything that is a complete solution yet, though, put there are definitely projects in the works for recording (yep, even multitrack) and processing in the works that are getting better all the time.

---

### Post by sickdude on 2005-08-24
it would be very cool if there are packages for this kind of stuff.

building packages is not a easy job but for people that want to give it a go there should be a wiki or a clean "how to", how to make them.

this might be a good idea, that way ubuntu users can contribute and use there favorite app on there favorite OS

the packages can be added to the ubuntu reposatory if the ubuntu-people aprove it

well spank my ass and call me grandpa that sounds like a great idea right?

---

### Post by clapton on 2005-09-03
I've try to find some source code or classes to begin a program, but without sucess.
Somebody can help? :-P

---

### Post by lompolo on 2006-02-04
Installing creox: If this works I will rename it howto install creox. Any comments and ideas are welcome.

This is my main source.
[http://fort.xdas.com/~kor/oss2jack/install.html](http://fort.xdas.com/~kor/oss2jack/install.html)

instructions:
```
sudo apt-get install creox jackd libjack0.80.0-dev qjackctl
```
or install them with synaptic

Use mixer from gnome panel. edit -> preferences should have microphone and PCM on. At playback mute microphone and toggle audio capture from microphone with mic and loudspeaker buttons. Adjust volumes. (Screenshot would be nice)

run qjackctl. I have error Could not open alsa sequencer as client. If so, press cancel. Setup -> Choose Realtime if you have realtime modules installed otherwise don't choose that. Choose input and output devices with > there should be your soundcard. OK. Start jack server with start button. You can test jack connecting alsa_pcm capture_1 to alsa_pcm playback_1. Then guitar should work without effects. Disconnect it.

Run creox. effector -> options Input=alsa_pcm:capture_1 output=alsa_pcm:playback_1 both left and right channels if having just one guitar.
effector -> play :) 

installing realtime-lsm and rtai modules: (I managed to install them to breezy just can't remember what is needed)

there is realtime-lsm, realtime-lsm-module, realtime-lsm-source, rtai, rtai-doc and rtai-source packages. Install them. Maybe you need module-assistant package and install these modules with it. 

Miscancellous:
arts or esd might be problem but qjackctl stops arts. Realtime modules solves latency problems

---

### Post by janek87 on 2007-04-23
hey... i installed gtkguitune from synaptic, but where is it?

---

### Post by tripleee on 2007-12-16
> **PeP said:**
> if you want an overview of the guitars program available with ubuntu:
allow extra repositories (-> ubuntuguide.org for a howto)

then open synaptic and search for guitar (set the search to name and contents)

The problem is that a lot of the utilities you might want to install do not explicitly mention "guitar" anywhere.

I'm also just starting to figure this out, but here are some links so far.  (Creox you already found.)

[LIST]
[*][http://quitte.de/dsp/caps.html](http://quitte.de/dsp/caps.html) (available as package "caps")
[*][http://ardour.org/node/523](http://ardour.org/node/523)
[*][http://audiores.uint8.com.ar/blog/?p=172](http://audiores.uint8.com.ar/blog/?p=172)
[/LIST]
These are fairly random links; I hope people will post more to this thread.

This guy seems to be happy with Ubuntu Studio, but that's a fairly broad set of packages.  It would be interesting to hear what packages exactly he ended up using:
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=637503](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=637503)

---

