---
title: "firefox and wav files"
date: 2005-11-22
forum: Desktop Environments
---

### Post by rgrig on 2005-11-22
It seems that after upgrading to 5.10 (from 5.04) and updating the packages firefox refuses to play wav files (e.g. [http://m-w.com/cgi-bin/audio.pl?test0001.wav=test](http://m-w.com/cgi-bin/audio.pl?test0001.wav=test)). I noticed that mplayer stops with this error: "Win32 LoadLibrary failed to load: AVIFIL32.dll". I don't know what firefox uses to play wav files.

The versions are:
firefox 1.0.7
mplayer dev-CVS--4.0.2

What would you do next?

---

### Post by dcstar on 2005-11-22
[QUOTE=rgrig]It seems that after upgrading to 5.10 (from 5.04) and updating the packages firefox refuses to play wav files (e.g. [http://m-w.com/cgi-bin/audio.pl?test0001.wav=test](http://m-w.com/cgi-bin/audio.pl?test0001.wav=test)). I noticed that mplayer stops with this error: "Win32 LoadLibrary failed to load: AVIFIL32.dll". I don't know what firefox uses to play wav files.

The versions are:
firefox 1.0.7
mplayer dev-CVS--4.0.2

What would you do next?[/QUOTE]
Do you have **mozplugger** and **mozilla-mplayer** installed?

You may also want to install the **mplayer** packages from Synaptic.

---

### Post by rgrig on 2005-11-25
The package mozplugger interferes badly with mozilla-acroread and does not fix the situation. The others are installed, of course. This is most likely a mplayer problem. See for example:

  [https://www.redhat.com/archives/fedora-list/2005-November/msg01374.html](https://www.redhat.com/archives/fedora-list/2005-November/msg01374.html)

Before writing my original question (and before finding the link above) I actually tried that but the solution seems to be dependent on where you get those dll's from.

In short, the last version of the mplayer package contains a broken mplayer.

---

