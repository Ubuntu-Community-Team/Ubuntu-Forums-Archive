---
title: "What program is like iTunes that will keep playing songs?"
date: 2009-02-11
forum: General Help
---

### Post by PsychedelicWonders on 2009-02-11
Every type of player I have right now only seems to play one song at a time.

I want a program like iTunes that I can scroll my entire library with just the songs, not all of the BS folders they are in.

I also want the player to keep playing song after song in the list once I hit the play button.

Does that make sense?

Basically I dont want to have to keep manaully playing new songs and I just dont want play lists, but all of my media at a quick glance.

---

### Post by Regnulify on 2009-02-11
so far songbird, rythmbox and banshee will all do what you're asking. There are many more too.  On songbird you will have to download the ipod support. Make sure in songbird to tell it to ignore errors on files it can't play (i.e. drm'd files).

Check out this article: [http://www.linuxjournal.com/article/9266](http://www.linuxjournal.com/article/9266)

---

### Post by brianmrowe on 2009-02-11
I tried songbird and rythmbox, but I like rythmbox better.
It was easier to import the CD I wanted to listen to. It has a lastfm plugin that was great and radio.  It dealt with podcasts well too.

---

### Post by PsychedelicWonders on 2009-02-11
> **Regnulify said:**
> so far songbird, rythmbox and banshee will all do what you're asking. There are many more too.  On songbird you will have to download the ipod support. Make sure in songbird to tell it to ignore errors on files it can't play (i.e. drm'd files).

Check out this article: [http://www.linuxjournal.com/article/9266](http://www.linuxjournal.com/article/9266)

What exactly is the iPod support that song bird offers?

I have a dual boot system and still have windows and generally just use iTunes to calibrate my iPhone...  I just dont want the iPhone to have any issues trying to force it to work in linux if i just boot to windows.

But why would there be files with errors on them as you mentioned? drm'd etc

How can I find these files with errors and remove them from my computer completely?

---

### Post by silentknyght on 2009-02-11
> **PsychedelicWonders said:**
> What exactly is the iPod support that song bird offers?

I have a dual boot system and still have windows and generally just use iTunes to calibrate my iPhone...  I just dont want the iPhone to have any issues trying to force it to work in linux if i just boot to windows.

But why would there be files with errors on them as you mentioned? drm'd etc

How can I find these files with errors and remove them from my computer completely?

I'm guessing the poster meant DRM aka AAC formats downloaded from iTunes before it offered DRM-free songs.  Therefore, I bet you can find which files are likely to be protected by searching for AAC files and testing those.

---

### Post by PsychedelicWonders on 2009-02-11
> **silentknyght said:**
> I'm guessing the poster meant DRM aka AAC formats downloaded from iTunes before it offered DRM-free songs.  Therefore, I bet you can find which files are likely to be protected by searching for AAC files and testing those.


hmm.  how can I tell if I have drm free songs?

I've never downloaded songs from itunes, just ripped cds really.

---

### Post by mb_webguy on 2009-02-11
> **PsychedelicWonders said:**
> hmm.  how can I tell if I have drm free songs?

I've never downloaded songs from itunes, just ripped cds really.

Basically, if have all of the extra codecs and Medibuntu niceties installed and you can't play certain files with a file extension of mp4, m4p, m4a, m4v, mov, wma, or wmv, then it may be due to some sort of DRM on those files.  Otherwise, you're fine.  And if you ripped music from CDs, especially if you ripped them to mp3, then you don't have to worry about DRM on those files.

---

### Post by PsychedelicWonders on 2009-02-11
songbird, rythmbox and banshee 

Alright, so which one is better out of those 3 and why?

---

### Post by anjilslaire on 2009-02-11
AmaroK

---

### Post by jrusso2 on 2009-02-11
> **PsychedelicWonders said:**
> Every type of player I have right now only seems to play one song at a time.

I want a program like iTunes that I can scroll my entire library with just the songs, not all of the BS folders they are in.

I also want the player to keep playing song after song in the list once I hit the play button.

Does that make sense?

Basically I dont want to have to keep manaully playing new songs and I just dont want play lists, but all of my media at a quick glance.

Amarok does this and it very stable I use it every day just hoping they do a Windows port one day.

---

### Post by PsychedelicWonders on 2009-02-11
why is amarok better than the other 3?

I think I have that one installed, not sure.

What would I need a windows port for?

---

### Post by Regnulify on 2009-02-11
Songbird had the most itunes like interface. I have not had an issue with any of these only playing one song at a time. If I start a song in the middle of a set of songs they all just keep playing.

Right now I am using banshee but only because it was installed by default on eeebuntu. It works fine and the ipod support was ready without additional installs. My only gripe with it is no shortcut to toggle shuffle. You have to use the mouse to do it.

I have updated my ipod with banshee but I have tried it with my iphone.

---

### Post by jrusso2 on 2009-02-11
> **PsychedelicWonders said:**
> why is amarok better than the other 3?

I think I have that one installed, not sure.

What would I need a windows port for?

I only have used songbird and found that unstable.  I want the windows port which they said they were working on to use at work.

Amarok has been stable for a long time and can be used with sqlite or mysql database if you have a lot of music its best.

---

### Post by powerplayground on 2009-02-11
Songbird lacks in alot of places (features, stability, etc) Amarok also uses a database, so going through and organizing 10000+ songs doesnt take forever. It's a bit technical and it requires some tweaking to get it to work correctly.

---

### Post by PsychedelicWonders on 2009-02-12
Alright i will try out Amarok...

I think I have it installed, if not, what should I type in the terminal?

---

### Post by mb_webguy on 2009-02-12
"sudo apt-get install amarok", or install it through Synaptic or Add/Remove Applications.

If you're using Ubuntu (and therefore Gnome) and have a laptop with media keys on the front, you'll probably want to download and install [Gnome Multimedia Keys]("http://www.kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910").  This is an Amarok script, which you'd add using the Script Manager under the Amarok Tools menu.

---

### Post by PsychedelicWonders on 2009-02-13
> **mb_webguy said:**
> "sudo apt-get install amarok", or install it through Synaptic or Add/Remove Applications.

If you're using Ubuntu (and therefore Gnome) and have a laptop with media keys on the front, you'll probably want to download and install [Gnome Multimedia Keys]("http://www.kde-apps.org/content/show.php/Gnome+Multimedia+Keys?content=60910").  This is an Amarok script, which you'd add using the Script Manager under the Amarok Tools menu.


I dont have a laptop, but do have a wireless microsoft ergonomic keyboard I have been trying to get my media keys to work properly with...

would this help?

---

### Post by mb_webguy on 2009-02-13
> **PsychedelicWonders said:**
> I dont have a laptop, but do have a wireless microsoft ergonomic keyboard I have been trying to get my media keys to work properly with...

would this help?

For Amarok (since it is a script specific to Amarok) I would think so, yes.  For Gnome apps, you should just be able to go to System->Preferences->Keyboard Shortcuts and set those keys to what you want.

---

