---
title: "Looking for audio player......"
date: 2009-06-23
forum: General Help
---

### Post by del_diablo on 2009-06-23
Hi, i am looking for a light music/audio player application that works. It needs systray support, in some form.

I have tried following
MPD and its infinetiv amounts of frontends:
*Requires server
Amarok, Rythmbox, etc:
*Too bloat
*Too heavy
Minirok:
*Cannot start in tray
*Too heavy
*No volume control
Several others:
*No systray(potamus)
*No tray support
*The documentation on using it, is bad..........

_Solved_

---

### Post by vikkikanhaua on 2009-06-23
who told you that mpd requires a server coz i'm using mpd on my desk with no server apps installed.
just give default port as "6600" & address as "localhost" in gmpc{mpd client} & ur music will start.
hope that helps......

---

### Post by Closed_Port on 2009-06-23
First off, learn some manners.
Second, try audacious and enable the status icon plugin.
Third, you don't need an extra server to run mpd.

---

### Post by del_diablo on 2009-06-23
> **vikkikanhaua said:**
> just give default port as "6600" & address as "localhost" in gmpc{mpd client} & ur music will start.
hope that helps......

[ATTACH]118710[/ATTACH]
There is a reason i am not hearing music <.< I just got noe clue on what the problem is.

---

### Post by whitethorn on 2009-06-23
Hi, I found this on another thread, where another person had troubles getting mpd to work.  

> 
I see issues with this thread: recommendations for a system-wide install (edit /etc/mpd.conf) are mixed with actions for per user install. Here follows the most simple procedure you can have to get mpd/sonata running on Ubuntu. It will be a system-wide install: i.e. all users will see the same music, playlists etc. I actually did this on the fly on my old desktop while writing these steps, so it should work.

1) Install mpd and sonata
Code:
sudo apt-get update ; sudo apt-get install mpd sonata
2) Point mpd to your music directory. We do this by replacing the default mpd music directory by a symbolic link to your actual collection.
My collection resides under the Music directory in my home, i.e. /home/vanadium/music (or ~/Music when I am logged in). Substitute your correct path instead of ~/Music in the second command:
Code:
sudo rmdir /var/lib/mpd/music
sudo ln -s ~/Music /var/lib/mpd/music
3) Create the music database
Code:
sudo mpd --create-db
4) Reboot the computer (safest but not fastest approach for it to work!)
5) Start Sonata (Applications - Sound & Video - Sonata). On the Library tab, you should see your collection. Right-click and Add adds an item (or a whole directory tree) to the playlist. With items in the playlist, pressing the Play button should ... (hold your breath)
__________________


I got it from this thread, where I also tried to help. 
[http://ubuntuforums.org/showthread.php?t=916715](http://ubuntuforums.org/showthread.php?t=916715)

The only other thing you might need to do adjust the /etc/mpd.conf   Depends on if you're using alsa, or pulse audio as your output.  Hope this helps a bit.  You first need to get mpd to work before you can connect to it with gmpc.  

If you want to see if mpd is starting properly, you can try

```

sudo /etc/init.d/mpd restart

```

---

### Post by vikkikanhaua on 2009-06-23
sorry i didn't got you in the last post
everything seems fine to me though

---

### Post by del_diablo on 2009-06-23
The /etc/mpd.conf that is gotten in by the package manager got a faulty config file.
Basicaly changing "/var/mpd/*" to "~/.mpd", did the trick for the folders.

This is mine working mpd.conf at the moment.
```
playlist_directory	"~/.mpd/playlists"
db_file			"~/.mpd/tag_cache"
log_file		"~/.mpd/mpd.log"
error_file		"~/.mpd/errors.log"
pid_file		"~/.mpd/pid"
state_file		"~/.mpd/state"
user                            "delly"
mixer_type                      "alsa"
filesystem_charset              "UTF-8"
id3v1_encoding                  "UTF-8"
gapless_mp3_playback             "yes"
```

PS: Got /var and a few other dirs mounted directly into my ram.

---

### Post by SuperSonic4 on 2009-06-23
Exaile?

---

### Post by del_diablo on 2009-06-23
> **SuperSonic4 said:**
> Exaile?

Bloatware?
And the tread is already solved, MPD + Sonata.

---

