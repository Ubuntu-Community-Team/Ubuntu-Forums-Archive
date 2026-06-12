---
title: "My hard search for an Audio Player"
date: 2006-08-06
forum: Desktop Environments
---

### Post by mahavishnu on 2006-08-06
I couldn't realize how difficult it is to find a player 
that can play AudioCDs, MP3 and have a scrobbler plugin that works properly.

XMMS doesn't submit AudioCD tracks to lastfm, even it has scrobbler plugin enabled.Beep Media the same. XMMS crashes all time, also.

Amarock doen't play AudioCDs (Play Audio CD is grayed out). 

Rhytmbox doen't play audio CDs, either. Listen, the same.

Kaffeine plays AudioCDs but doesn't have scrobbler plugin.

Banshee plays and scrobbles AudioCDs bug has a bug (I think) that doen't recognize the time of tracks correctly and doen't play it till the end.

I'm still looking for a player that plays CDs, MP3 and have a scrobbler plugin, all in one ...

---

### Post by jISh on 2006-08-06
I don't like any of those players, except Listen and Amarok. I don't use Listen because it still has far too many bugs, and I don't want to install half of KDE onto my GNOME desktop to run Amarok.

My solution? Quod Libet. Does everything you are wanting. Small player, great library management, EXTREMELY powerful tagging, system tray integration, loads of plugins including scrobbler...you get the picture :O

Edit: It's in the repositories, also.

---

### Post by Dubbayoo on 2006-08-06
Rhythmbox does play audio CDs.

---

### Post by mahavishnu on 2006-08-06
> **jISh said:**
> My solution? Quod Libet. Does everything you are wanting. Small player, great library management, EXTREMELY powerful tagging, system tray integration, loads of plugins including scrobbler...you get the picture 
[B]
are you sure, Quod Libet plays AudioCDs ?
Here doesn't.[/B]


> **Dubbayoo said:**
> Rhythmbox does play audio CDs.

**Here Rhytmbox only plays the first track of Audio CDs, the other there's an error "Not negotiated".**

---

### Post by Lord Illidan on 2006-08-06
Amarok does play audio cds, at least on my pc..

Have you got the latest version?

---

### Post by mahavishnu on 2006-08-06
> **Lord Illidan said:**
> Amarok does play audio cds, at least on my pc..
Have you got the latest version?

The current in Synaptic.
I think it isn't the latest ...

---

### Post by dolby on 2006-08-06
[http://audacious-media-player.org/Main_Page](http://audacious-media-player.org/Main_Page)

the best player on linux atm

---

### Post by mahavishnu on 2006-08-06
> **dolby said:**
> [http://audacious-media-player.org/Main_Page](http://audacious-media-player.org/Main_Page)
the best player on linux atm

no scrobbler plugion for 1.1.0 version . ..   ](*,)

by the end of the day I have two more players (quodlibet and audacious) and still can't play cds, mp3 and scrobbler all in one ...:(

---

### Post by kno712 on 2006-08-06
From the Amarok help file

[FONT="System"]The Play Audio CD feature uses the audiocd:/ protocol and is not compatible with all of the available engines[/FONT]

In my ubuntu installation, Rhythmbox plays Audio CDs, Amarok doesn't. I think I will have a look to that quod.

---

### Post by mahavishnu on 2006-08-07
> **kno712 said:**
> [FONT="System"]The Play Audio CD feature uses the audiocd:/ protocol and is not compatible with all of the available engines[/FONT].

oddly Gxine plays AudioCds here.
Amarok using xine engine, **doesn't** ...

---

### Post by indytim on 2006-08-07
I've got 1.3.9 Amarok and it plays CDAs on my PC with no problems.

IndyTim

---

### Post by kno712 on 2006-08-09
What about 'Listen' [http://listengnome.free.fr/]("http://listengnome.free.fr/"); have any of you try it?

---

### Post by mojoman on 2006-08-10
I too have been looking for a mediplayer and reading this thread I looked up quod libet and it looked good so I thought I'd give it a try. However, apt-get install quodlibet gave the following output:

```
The following packages have unmet dependencies:
  quodlibet: Depends: exfalso (= 0.18-3ubuntu1) but it is not going to be installed
             Depends: python-gst0.10 but it is not going to be installed
  rhythmbox: Depends: libgpod0 but it is not going to be installed
             Depends: libnautilus-burn3 but it is not going to be installed
             Depends: libnotify1 but it is not going to be installed
             Depends: libsexy2 but it is not going to be installed
             Depends: libsoup2.2-8 (>= 2.2.92) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Ok, so naturally i did try apt-get -f install quodlibet and ... the exact damned thing happened again! :---)  Does anyone know what is going on? Does this mediaplayer require *another* mediaplayer (i.e. rythmbox) to work?

Any ideas?
/Mojoman

---

### Post by dolby on 2006-08-11
have u tried installing all these first?
  Depends: exfalso (= 0.18-3ubuntu1) but it is not going to be installed
  Depends: python-gst0.10 but it is not going to be installed
  Depends: libgpod0 but it is not going to be installed
  Depends: libnautilus-burn3 but it is not going to be installed
  Depends: libnotify1 but it is not going to be installed
  Depends: libsexy2 but it is not going to be installed
  Depends: libsoup2.2-8 (>= 2.2.92) but it is not going to be installed

have u tried [audacious](http://ubuntuforums.org/showthread.php?t=195867&highlight=audacious)?

---

### Post by hugmenot on 2006-08-11
> **mojoman said:**
> I too have been looking for a mediplayer and reading this thread I looked up quod libet and it looked good so I thought I'd give it a try. However, apt-get install quodlibet gave the following output:

```
The following packages have unmet dependencies:
  quodlibet: Depends: exfalso (= 0.18-3ubuntu1) but it is not going to be installed
             Depends: python-gst0.10 but it is not going to be installed
  rhythmbox: Depends: libgpod0 but it is not going to be installed
             Depends: libnautilus-burn3 but it is not going to be installed
             Depends: libnotify1 but it is not going to be installed
             Depends: libsexy2 but it is not going to be installed
             Depends: libsoup2.2-8 (>= 2.2.92) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Ok, so naturally i did try apt-get -f install quodlibet and ... the exact damned thing happened again! :---)  Does anyone know what is going on? Does this mediaplayer require *another* mediaplayer (i.e. rythmbox) to work?

Any ideas?
/Mojoman

You could get it from **mlind**&#8217;s own repository, which contains recent packages of all packages you need for Quod Libet. It&#8217;s something like elisanet.fi.

---

