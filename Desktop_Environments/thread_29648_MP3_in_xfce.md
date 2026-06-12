---
title: "MP3 in xfce"
date: 2005-04-25
forum: Desktop Environments
---

### Post by Pulka on 2005-04-25
Hi!

I can't seem to play mp3 in xfce. When i try to play, it gives me this errors:

"could not open resource for writing" and then "could not pause playback"

I have sound in the system (gaim for example), it's just the mp3.
In gnome i had no problems.
Can anyone help me?

---

### Post by defkewl on 2005-04-25
[QUOTE=Pulka]Hi!

I can't seem to play mp3 in xfce. When i try to play, it gives me this errors:

"could not open resource for writing" and then "could not pause playback"

I have sound in the system (gaim for example), it's just the mp3.
In gnome i had no problems.
Can anyone help me?[/QUOTE]
 Did you install the library needed?

---

### Post by tread on 2005-04-25
Check what output plugin is being used by the mp3 player, and experiment with that.

---

### Post by eric71 on 2005-04-25
[QUOTE=Pulka]Hi!

I can't seem to play mp3 in xfce. When i try to play, it gives me this errors:

"could not open resource for writing" and then "could not pause playback"

I have sound in the system (gaim for example), it's just the mp3.
In gnome i had no problems.
Can anyone help me?[/QUOTE]

What application are you using for playing mp3s in Xfce?  It may not be the same by default as in Gnome.  Also, as tread mentioned above, it may be due to the wrong plugin being selected.  For instance if you have xmms set to use the esd plugin in Gnome, and esd is not loaded in Xfce, it won't play.  Try selecting a new default application to run mp3's as explained in the thread you started about customizing Xfce, and if that isn't the problem, try a different output plugin for the one you are using.

If you've still got Gnome installes, everything that worked in GNome should work in Xfce.  So it's probably just a matter of getting the right application to start.

---

### Post by bored2k on 2005-04-25
Open xterminal in xfce and run esd &, then retry [make sure your player is using eSound/ESD].

---

### Post by Pulka on 2005-04-25
Well, in gnome i use rhythmbox. But i'm trying with xmms and also can't play it.
In xmms i have "esound" selected, and in rhythmbox, i can't find the place to choose the plugin

---

### Post by eric71 on 2005-04-26
[QUOTE=Pulka]Well, in gnome i use rhythmbox. But i'm trying with xmms and also can't play it.
In xmms i have "esound" selected, and in rhythmbox, i can't find the place to choose the plugin[/QUOTE]

You've most likely not got esd running in Xfce, and as far as I'm concerned esd is nothing but trouble anyway.  Try selecting the Alsa or OSS plugin, and you should be able to play mp3s.

---

### Post by bored2k on 2005-04-26
[QUOTE=eric71]You've most likely not got esd running in Xfce, and as far as I'm concerned esd is nothing but trouble anyway.  Try selecting the Alsa or OSS plugin, and you should be able to play mp3s.[/QUOTE]
 I'm an ESD only user. I haven't encountered any problems with it. Not in GNOME, not in XFCE.

---

### Post by eric71 on 2005-04-26
[QUOTE=bored2k]I'm an ESD only user. I haven't encountered any problems with it. Not in GNOME, not in XFCE.[/QUOTE]
It's actually fine depending on what applications you use.  I use Skype and Audacity, both of which just don't work with ESD.  If I didn't use those, I'd probably use ESD.  As far as an Xfce user goes, it's another service to have started, which further complicates things, whereas it's pretty automatic in Gnome.

---

### Post by Pulka on 2005-04-27
just to say that i found the solution here:

[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=119958](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=119958)


In case anyone has the same problem, just to:

gconftool-2 -s /system/gstreamer/0.8/default/audiosink -t string esdsink

---

### Post by tonymoyoy on 2005-07-26
i just run esd and then it work O_o

---

