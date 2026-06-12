---
title: "How do you read a d-bus bool?"
date: 2011-01-09
forum: Desktop Environments
---

### Post by azzid on 2011-01-09
I'm writing a script which sets the master volume of my soundcard to max at one point.
This is needed for things to work smoothly further down the script, but it is kind of a hazard to run the script if something else is playing on the soundcard at that particular moment.

My main source of music is spotify, so my plan the get the script a bit nicer was to atleast stop spotify from playing before raising the volume.

Spotify has quite a rich d-bus interface, so pausing it was no harder than:
```
dbus-send --print-reply --dest=org.mpris.MediaPlayer2.spotify /org/mpris/MediaPlayer2 org.mpris.MediaPlayer2.Player.Pause
```
A line i found floating about them internets.

Instead of blindly firing that command I'd like to read another d-bus value, namely:
```
**$ qdbus org.mpris.MediaPlayer2.spotify /org/mpris/MediaPlayer2**
[...]
property read bool org.mpris.MediaPlayer2.Player.CanPause
[...]
```
Which I guess would tell me if spotify is actually playing or not.

What evades me here is the syntax for the d-bus command. Does anyone here know how one would read such a value?

---

### Post by azzid on 2011-01-09
I figured it out.

The 'CanPause' value was not what I was looking for, but **org.mpris.MediaPlayer2.Player.PlaybackStatus** contained the information I needed.

In order to **GET** the the value I had to use the following command:
```
$ qdbus org.mpris.MediaPlayer2.spotify /org/mpris/MediaPlayer2 org.freedesktop.DBus.Properties.Get org.mpris.MediaPlayer2.Player PlaybackStatus
```

imo, the syntax is not entriely obvious, but then I have a severe lack of understanding when it comes to d-bus. ;)

---

