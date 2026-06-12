---
title: "Adding lyrics search to Spotify Unity Launcher"
date: 2011-04-22
forum: Desktop Environments
---

### Post by Hirs on 2011-04-22
I was excited about the quicklists feature of Unity launcher:
[https://wiki.ubuntu.com/Unity/LauncherAPI](https://wiki.ubuntu.com/Unity/LauncherAPI)

You can search for lyrics of the playing song with one command (not very good looking but it works):
```
gnome-open "http://www.songlyrics.com/index.php?section=search&searchW=$(dbus-send --print-reply --dest=org.mpris.MediaPlayer2.spotify /org/mpris/MediaPlayer2 org.freedesktop.DBus.Properties.Get string:'org.mpris.MediaPlayer2.Player' string:'Metadata'|egrep -A 1 "(artist|title)"|egrep -v "(artist|title)" |cut -b 44-|cut -d '"' -f 1|egrep -v ^$|tr  '\n' ' '|sed 's/ /+/g')"
```

Adding a quicklist to spotify is easy:
```
sudo vi /usr/share/applications/spotify.desktop
```

Add this after the last line:
```
X-Ayatana-Desktop-Shortcuts=Lyrics

[Lyrics Shortcut Group]
Name=Show lyrics
Exec=/home/carlos/bin/spotyLyric.sh
TargetEnvironment=Unity

```

And create the file /home/carlos/bin/spotyLyric.sh (or whatever you choose to place it) with this:
```
#!/bin/sh
gnome-open "http://www.songlyrics.com/index.php?section=search&searchW=$(dbus-send --print-reply --dest=org.mpris.MediaPlayer2.spotify /org/mpris/MediaPlayer2 org.freedesktop.DBus.Properties.Get string:'org.mpris.MediaPlayer2.Player' string:'Metadata'|egrep -A 1 "(artist|title)"|egrep -v "(artist|title)" |cut -b 44-|cut -d '"' -f 1|egrep -v ^$|tr  '\n' ' '|sed 's/ /+/g')"
```


I would like to be able to execute this command from the desktop file, but It never gets executed, that is why I created a script. I have read the doc here: 
[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html)
but escaping characters doesn't work, probably I've done something wrong.

How could I do this without the script?

---

