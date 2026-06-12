---
title: "Screwed up Nautilus"
date: 2010-01-08
forum: Desktop Environments
---

### Post by gjtoth on 2010-01-08
In my infinite wisdom, I installed a Nautilus extension called, "Nautilus-Sound-Converter".  This seems to have toasted things mightily as I have no desktop icons, can't right-click to pull up a menu, and when I attempt to run Nautilus, it fizzles.  I tried calling it from a terminal and the response I get is:

```
(nautilus:3486): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-sound-converter extension
Could not initialize GStreamer: Error re-scanning registry , child terminated by signal

```

Any ideas how I can restore things or remove this extension?

---

### Post by fibercode on 2010-01-08
Well... just remove the extension if you know what the package name is.

I did an aptitude search on a nautilus package that does sound conversion:

```
aptitude show nautilus?
```

It came back with:

```
Package: nautilus-script-audio-convert
New: yes
State: not installed
Version: 0.3.1.1-0ubuntu4
Priority: optional
Section: universe/sound
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 102k
Depends: file, gawk | mawk, nautilus-script-manager, zenity
Suggests: faac, faad, flac, lame, mplayer | mplayer-nogui, vorbis-tools
Description: A nautilus audio converter script
 audio convert is a script that converts between WAV, Ogg, MP3, MPC, FLAC, APE,
 AAC, and WMA files. It has an easy-to-use interface that makes it possible to
 fill in the tags for a few formats, copy the tags from input files into the new
 files, and choose the quality of compression.
```

Check if that is the package in question by running:

```
dpkg --get-selections | grep nautil-script-audio-convert
```

If it comes up that means that it is installed.

I would remove it:

```
sudo apt-get purge nautilus-script-audio-convert
```

Edit: Restart you computer or do Right Alt + PrintScreen + K to restart X.

If the problem persists, I would remove nautilus and all dependencies and reinstallit:

```
sudo apt-get remove nautilus
sudo apt-get autoremove
```

And then reinstall it again:

```
sudo apt-get install nautilus
```

---

### Post by gjtoth on 2010-01-08
Thanks for your help.

I chose the final option and attempted a removal and reinstall of nautilus.  I get the same thing.  I currently doing a search for anything nautilus-audio-converter with catfish.  Any other suggestions would be welcomed.  BTW, I have contacted the author and asked for advice.  And, curiously, I now have no sound devices showing.

---

