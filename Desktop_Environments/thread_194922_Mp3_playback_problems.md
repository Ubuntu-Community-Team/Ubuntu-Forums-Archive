---
title: "Mp3 playback problems"
date: 2006-06-12
forum: Desktop Environments
---

### Post by Torstein_V on 2006-06-12
Hi!

Has anyone noticed any problems with the new gstream engine 0.10? I've installed three different music playback applications, and all of them result in some kind of problems:

For instance, Amarok won't play the mp3-s at all. It just skips the one, and tries to execute the other, whitout success. 

Rhytmbox and Banshee are having major problems seeking through the song, whenever I use the progress bar to wind forward, or backwards. The progress bar jumps forward and backwards, and can't quite figure out where I wanted it in the first place.  

Does anybody understand my problem? It's a bit hard to explain.

I can't seem to remember experiencing these problems under Breezy with gstreamer 0.8... :neutral:

---

### Post by Jucato on 2006-06-12
I can only answer for Amarok, since I'm only using Kubuntu. The GStreamer back-end in Kubuntu Dapper is broken, that's why all multimedia apps now use Xine only. To enable mp3 for Amarok or any KDE app, you have to install libxine-extracodecs from the multiverse repository. The good news is that this one lib will handle all restricted media formats, with the exception of MS specific ones (WMA/WMV, etc), where you still need the w32codecs.

Hope that helps.

---

### Post by Torstein_V on 2006-06-12
Thanks Fenyx! Doing following:

```
sudo apt-get install libxine-extracodecs w32codecs
```

solved the playback problem in Amarok, but didn't help Rythmbox nor Banshee. 

Using the progressbar in Amarok doesn't generate any problems at all, so thumbs up for Amarok. The only negative thing about Amarok is that it has a quite over-complex user interface, and is difficult to use. 

Is there anyway to strip the application down? Strip it so it looks more like Rythmbox/ iTunes?

---

### Post by Jucato on 2006-06-12
I'm not really sure. But Amarok 1.4 has a cleaner interface than the previous versions. In some ways it actually resembles iTunes, except that iTunes doesn't have tabs. I rarely set Amarok to run in a normal window mode, I always close it (just click the X button) and let in run in the system tray. That's why I really don't mind the user interface :D

EDIT:
Hey I just discovered something! There are only 4 main tabs in Amarok (the ones on the right): Context (which lets you browse CD covers, lyrics, artists, etc), Collection (like iTunes library), Playlists, and Files (a file browser). If you don't want some of the tabs, just right click on the tabs and you can uncheck those that you don't need. :D

I only use Collection and Playlists so now they're the only two tabs that I have.

---

### Post by Torstein_V on 2006-06-12
You do mean on the left (Files, Media Device, Playlists, Collection and Context)?

Right-clicking them doesn't activate any context menu, so is it at all possible to remove these? 

By the way, has Amarok 1.4 made to the repositories yet? O:)

---

### Post by Jucato on 2006-06-12
Amarok 1.4 didn't make into the main repositories because of the feature freeze. But a special repository was made for it (just like KDE 3.5.3). Follow this link to the Kubuntu announcement:

[http://kubuntu.org/announcements/amarok-1.4.php](http://kubuntu.org/announcements/amarok-1.4.php)

NOTE: you need to have your universe repositories enabled, as some packages needed are found there (I think somethings needed by amarok-xine?)

The Media Device tab was removed and the Context tab was reduced to just Music/Lyrics/Artist. You can now right click on those tabs to make those that you don't want disappear. But in order to stop the Context tab from showing up everytime you change tracks/mp3, go to Settings > Configure Amarok > General tab > Playlist-window options > disable "Switch to context browser on track change"

---

### Post by Torstein_V on 2006-06-12
Okay, I managed to install Amarok 1.4 successfully, thanks a lot Fenyx! :)

And here's how I did it, so the rest of you can enjoy Amarok 1.4, just like I do :)

**Gnome:**

```
sudo gedit /etc/apt/sources.list
```

**KDE:**

```
sudo kwrite /etc/apt/sources.list
```


**Both KDE and Gnome:**

copy this respository to the end of the document "sources.list"

```
deb http://kubuntu.org/packages/amarok-14 dapper main
```

Have the document look something like this (the bottom line):

```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.freecontrib.org/ubuntu/plf dapper free non-free
deb-src http://packages.freecontrib.org/ubuntu/plf dapper free non-free 

deb http://kubuntu.org/packages/amarok-14 dapper main
```

**Perform the following in SHELL/Terminal:**

```
wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg

sudo apt-key add kubuntu-packages-jriddell-key.gpg

sudo apt-get update

sudo apt-get install amarok

sudo apt-get install libxine-extracodecs

killall gnome-panel

```

Thanks again Fenyx ;)

---

