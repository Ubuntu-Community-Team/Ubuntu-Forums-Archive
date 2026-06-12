---
title: "Kaffeine can't play anything"
date: 2005-10-18
forum: Desktop Environments
---

### Post by nixhead on 2005-10-18
Kaffeine is unable to play any files, claiming decoders weren't found or that there is no sound decoder. Sound works and the w32codecs are installed.

Any hints?

---

### Post by Segovia on 2005-10-18
[QUOTE=nixhead]Kaffeine is unable to play any files, claiming decoders weren't found or that there is no sound decoder. Sound works and the w32codecs are installed.

Any hints?[/QUOTE]
Well the w32codecs wont be used unless you switch to the xine backend.  Kubuntu Kaffeine is using GStreamer by default.  So what you need to do is:

sudo apt-get install kaffeine-xine

Then fire up kaffeine, and go to the Settings menu > Player Engine > and select Kaffeine (not Kaffeine GStreamer)  Restart Kaffeine and you should be good to go.

---

### Post by nixhead on 2005-10-18
[QUOTE=Segovia]Then fire up kaffeine, and go to the Settings menu > Player Engine > and select Kaffeine (not Kaffeine GStreamer)  Restart Kaffeine and you should be good to go.[/QUOTE]

Your tip helped. I am now good to go for mpg or mpeg file extensions. However, I still can't play avi, mov, rm or wmv video files. Is there anything else I need to do to insure I can play ALL video formats?

---

### Post by Segovia on 2005-10-18
[QUOTE=nixhead]Your tip helped. I am now good to go for mpg or mpeg file extensions. However, I still can't play avi, mov, rm or wmv video files. Is there anything else I need to do to insure I can play ALL video formats?[/QUOTE]
Hmm.  You should definately be able to play .wmv and .avi.  I don't even have the win32codecs installed right now and I can play .wmv with kaffeine/xine.  I can also play  DivX XviD and any other .avi's I have.  I don't have anything in .rm or or .mov, (and I rarely encounter that format in the places I get my movies), so I don't know.

I do recall from Windows that stuff in Real format (.rm/.ram) can be a pain in the ass to get working without actually installing RealPlayer.  Even "Real Alternative" wont play certain .rm's.  Same goes for QuickTime.  That's part of the reason I have always avoided them.

Where did you get the win32codecs package, by the way? Marillat debian repositories? Or did you install them yourself from the MPlayer site?

Also, have a look at these places, maybe you'll discover something that you've missed:

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")
[http://kudos.berlios.de/]("http://kudos.berlios.de/")
[http://ubuntuguide.org/]("http://ubuntuguide.org/")

---

### Post by ColinG on 2005-10-19
I thought .mov was a quicktime derivative so you may need the quicktime library (libquicktime, I think).

---

### Post by Pumpino on 2005-10-19
I just got Kaffeine playing mpegs by following the above instructions, but everything is purple!  All the colours are screwed.  What's that all about?!?!

---

