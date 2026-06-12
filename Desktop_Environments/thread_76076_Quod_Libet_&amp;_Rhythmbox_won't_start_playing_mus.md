---
title: "Quod Libet &amp; Rhythmbox won't start playing music anymore"
date: 2005-10-14
forum: Desktop Environments
---

### Post by feelgoodlost on 2005-10-14
I could fix all the small issues occuring with the upgrade but Quod Libet doesn't work anymore.

I can start it but it just won't start playing the music. 

Error message in terminal:
```
Unterstützte Formate: flac, mp3, oggvorbis
Audiobibliothek geladen
Öffne Audiogerät
/usr/lib/quodlibet/quodlibet.zip/qltk.py:110: DeprecationWarning: Class SongWatcher is already GObject-registered; Please note that classes containing any of the attributes __gtype_name__, __gproperties__, or __gsignals__ are now automatically registered.
/usr/lib/quodlibet/quodlibet.zip/qltk.py:715: DeprecationWarning: Class TreeViewHints is already GObject-registered; Please note that classes containing any of the attributes __gtype_name__, __gproperties__, or __gsignals__ are now automatically registered.
/usr/lib/quodlibet/quodlibet.zip/properties.py:1733: DeprecationWarning: Class SongProperties is already GObject-registered; Please note that classes containing any of the attributes __gtype_name__, __gproperties__, or __gsignals__ are now automatically registered.
/usr/lib/quodlibet/quodlibet.zip/browsers/albums.py:551: DeprecationWarning: Class AlbumList is already GObject-registered; Please note that classes containing any of the attributes __gtype_name__, __gproperties__, or __gsignals__ are now automatically registered.
/usr/lib/quodlibet/quodlibet.zip/efwidgets.py:248: DeprecationWarning: Class FileSelector is already GObject-registered; Please note that classes containing any of the attributes __gtype_name__, __gproperties__, or __gsignals__ are now automatically registered.
/usr/lib/quodlibet/quodlibet.zip/efwidgets.py:388: DeprecationWarning: Class ExFalsoWindow is already GObject-registered; Please note that classes containing any of the attributes __gtype_name__, __gproperties__, or __gsignals__ are now automatically registered.
/usr/lib/quodlibet/quodlibet.zip/browsers/filesystem.py:115: DeprecationWarning: Class FileSystem is already GObject-registered; Please note that classes containing any of the attributes __gtype_name__, __gproperties__, or __gsignals__ are now automatically registered.
/usr/lib/quodlibet/quodlibet.zip/browsers/paned.py:252: DeprecationWarning: Class PanedBrowser is already GObject-registered; Please note that classes containing any of the attributes __gtype_name__, __gproperties__, or __gsignals__ are now automatically registered.
/usr/lib/quodlibet/quodlibet.zip/browsers/playlists.py:93: DeprecationWarning: Class PlaylistBar is already GObject-registered; Please note that classes containing any of the attributes __gtype_name__, __gproperties__, or __gsignals__ are now automatically registered.
/usr/lib/quodlibet/quodlibet.zip/browsers/search.py:72: DeprecationWarning: Class EmptyBar is already GObject-registered; Please note that classes containing any of the attributes __gtype_name__, __gproperties__, or __gsignals__ are now automatically registered.
/usr/lib/quodlibet/quodlibet.zip/browsers/albums.py:493: GtkWarning: gtk_tree_view_get_cell_area: assertion `GTK_WIDGET_REALIZED (tree_view)' failed
/usr/lib/quodlibet/quodlibet.zip/browsers/albums.py:493: GtkWarning: gtk_tree_view_scroll_to_point: assertion `GTK_WIDGET_REALIZED (tree_view)' failed

```

Do I have to install an additional package? I couldn't find what's missing.
Recompiling didn't solve the problem.

I've got the same problem with Rhythmbox after the upgrade (songs can't get started anymore), but it doesn't log anything in the terminal.

Xmms, Vlc or Mplayer work like a charm.

Any suggestions?

---

### Post by Stormy Eyes on 2005-10-14
Please go into "System -> Preferences -> Multimedia Systems Selector". Are the audio input/output set for ALSA or for ESD? if they're set to ESD, change them to ALSA and see if that works.

---

### Post by feelgoodlost on 2005-10-14
Both, input and output, are set to ALSA.

---

### Post by Stormy Eyes on 2005-10-14
[QUOTE=feelgoodlost]Both, input and output, are set to ALSA.[/QUOTE]

OK, that's strange. Please open a terminal, run **ps aux | grep esd**, and post the results. I've found that if the sound is misbehaving in Ubuntu, it's usually because of ESD. Killing it off and using pure ALSA usually solves the problem.

---

### Post by feelgoodlost on 2005-10-14
OK. That's the result: 

```
 ps aux | grep esd
feelgoodlost    7439  0.0  0.2   5328   756 ?        S    17:43   0:00 /usr/bin/esd -nobeeps
feelgoodlost   16991  0.0  0.1   1620   380 pts/2    D+   21:44   0:00 grep esd
```

---

### Post by Stormy Eyes on 2005-10-14
[QUOTE=feelgoodlost]OK. That's the result: 

```
 ps aux | grep esd
feelgoodlost    7439  0.0  0.2   5328   756 ?        S    17:43   0:00 /usr/bin/esd -nobeeps
feelgoodlost   16991  0.0  0.1   1620   380 pts/2    D+   21:44   0:00 grep esd
```[/QUOTE]

I knew it: ESD is hogging your sound card and blocking Quod Libet. You can issue a **killall -9 esd** command to shut it down, and then Quod Libet should play for you.

---

### Post by feelgoodlost on 2005-10-14
Thanks so much Stormy Eyes. Unfortunately, this must have been an additional problem. I've still got the same issue with Rhythmbox and Quod Libet.

---

### Post by Stormy Eyes on 2005-10-14
[QUOTE=feelgoodlost]Thanks so much Stormy Eyes. Unfortunately, this must have been an additional problem. I've still got the same issue with Rhythmbox and Quod Libet.[/QUOTE]

So, have you got your music playing? I remember ESD being a problem back in Warty, and certainly was a problem with Hoary.

---

### Post by feelgoodlost on 2005-10-14
No, they still don't play my music like they used to do with the same settings in Hoary.

---

### Post by Stormy Eyes on 2005-10-14
[QUOTE=feelgoodlost]No, they still don't play my music like they used to do with the same settings in Hoary.[/QUOTE]

Hmm. You tried closing your music player and restarting it, right?

---

### Post by feelgoodlost on 2005-10-14
Yes, I did. Several times, including system restarts. Didn't solve anything.

---

### Post by Stormy Eyes on 2005-10-14
[QUOTE=feelgoodlost]Yes, I did. Several times, including system restarts. Didn't solve anything.[/QUOTE]

Sorry, but I'm all out of ideas then. In your position, I'd probably snarl, do a data backup, burn a Breezy disc, and install from scratch.

---

### Post by joanverde on 2005-10-15
How should I interpret this?;

ps aux | grep esd
john     26005  0.0  0.0   3060   756 pts/0    S+   00:15   0:00 grep esd
john@tapovanarama:~$ killall -9 esd
esd: no process killed

---

### Post by feelgoodlost on 2005-10-15
[QUOTE=Stormy Eyes]Sorry, but I'm all out of ideas then. In your position, I'd probably snarl, do a data backup, burn a Breezy disc, and install from scratch.[/QUOTE]

I've installed Breezy from scratch now, but there is still exactly the same problem. :???: :???: 

Anyone?

---

### Post by theh0g on 2005-12-26
If this still happens to anyone, here is what I did, after 2 hours of trying to find a sollution:
```
vi ~/.quodlibet/config
```
and set
```
pipeline = alsa
```

in **[settings]** section. No idea if this is some general sollution, but it worked on my machine.

---

### Post by jerrykenny on 2006-01-10
Thanks Stormy eyes, switching to Alsa fixed my rythmbox straight away.  :p

---

