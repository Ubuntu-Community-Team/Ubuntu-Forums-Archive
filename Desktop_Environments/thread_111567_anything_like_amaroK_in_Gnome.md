---
title: "anything like amaroK in Gnome?"
date: 2006-01-02
forum: Desktop Environments
---

### Post by tjfitz on 2006-01-02
Hello, I have recently moved off of KDE in favor of Gnome. I find the gnome interface and themes much cleaner and uncluttered than KDE. There is only ONE thing (ok, maybe two if I include k3b) that I really miss from KDE: amaroK. What I love about amarok is that I can assemble playlists from id3 tag genres, and that it displays information about the currently playing track (i.e. lyrics, album, the if-you-like-this-song-you-should-listen-to-*[title of similar song*]-type recommendations (I think this came from audioscrobbler) (did I lose anybody there???). The only other linux music player I know of that can assemble playlists in that way, using genres, is Rhythmbox. But, rhythmbox doesn't have any of the other functionalities I listed (or I haven't found them yet). Dynamic genre-based playlists are a must for me, but I also like to at least see lyrics. I don't want to encumber my system with loads of kde libraries just so I can use amarok (and possibly break my installation). Is there a way to show lyrics in rhythmbox? Or another player that fits these specs? FYI, my music library is strictly mp3, with strictly id3v2 tags.

ps: in a similar vein, how do I store lyrics in my tags? I could do it under windows, but easytag doesn't have a "lyrics" field. I don't have any lyrics stored yet as such, but this would eliminate the need to dl lyrics every time a song plays.

---

### Post by newuser111 on 2006-01-02
[http://zinf.org/](http://zinf.org/) or perhaps

[http://snackamp.sourceforge.net/](http://snackamp.sourceforge.net/)

of course you do realize that you can install and run amarok or other kde apps with gnome as well?

---

### Post by Omnios on 2006-01-02
I have both KDE and Gnome and can run most of those in gnome. Gnome also has Sreamtuner wich accesses live 365 and shoutcast as well as a few other if your into that. Its kind of funny because I cant burn cds with the gnome burners but the KDE burner works wright from its install

 EDIT: there is also a theme engine in to better render kde apps into gnome

---

### Post by tjfitz on 2006-01-02
I installed zinf, but it wouldn't start, so I ran it in console, and I got this:

```
tjfitz@mightymouse:~$ zinf

(<unknown>:18043): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(<unknown>:18043): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(<unknown>:18043): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(<unknown>:18043): Gdk-CRITICAL **: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
The program '<unknown>' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 325 error_code 8 request_code 62 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
tjfitz@mightymouse:~$
``` 
The description on snackamp suggests it's tuned more toward ppl who DON'T want to organize music by tag, so that doesn't look like a good candidate. (Mine is organized ~/Audio/*artist_name*/[I]music_file).

[/I]That leaves KDE again.  Well, what the heck, if I break something, I'll just post again.  Thanks!

EDIT: My roommate just told me that amarok worked fine under gnome for him, his problem was with mplayer!

---

### Post by tjfitz on 2006-01-02
It looks like amarok is working fine.  Thanks all!

---

### Post by banjobacon on 2006-01-02
Quod Libet has a lyrics plugin and half-way decent library functionality.

[http://www.sacredchao.net/quodlibet](http://www.sacredchao.net/quodlibet)

---

### Post by rubengs on 2006-01-03
I have gnome too and I run K3b and amaroK without problems ;) .

---

### Post by todavies on 2006-01-07
just do a search in synaptic for kdebase and install that.
should get amarok running in gnome just like kde.

---

### Post by Spie on 2006-01-08
[Banshee]("http://www.banshee-project.org") is on its way to become the best music player for GNOME.

---

### Post by charlieg on 2006-01-09
[QUOTE=Spie][Banshee]("http://www.banshee-project.org") is on its way to become the best music player for GNOME.[/QUOTE]
As much as I like Banshee, it has a long way to go to catch up with amaroK and amaroK is being more actively developed (not that Banshee development isn't active).  As such, I just use amaroK whilst keeping an eye on each Banshee release to see where it is.

I wish somebody would do a Gnome/Gtk port of amaroK.  Sadly such things are as likely as they are trivial.

---

### Post by charlieg on 2006-01-23
[QUOTE=banjobacon]Quod Libet has a lyrics plugin and half-way decent library functionality.

[http://www.sacredchao.net/quodlibet](http://www.sacredchao.net/quodlibet)[/QUOTE]
Woah, Quod Libet is awesome!  I think I found my "amaroK for Gnome"!

---

### Post by exchequer598 on 2007-10-25
Nobody thought of Exaile?

---

### Post by TeaSwigger on 2007-10-26
tjfitz, have you tried Exhaile or gmusicbrowser?

[http://squentin.free.fr/gmusicbrowser/gmusicbrowser.html](http://squentin.free.fr/gmusicbrowser/gmusicbrowser.html)

---

### Post by Callius on 2007-10-26
I have Amarok installed in Gnome and haven't really noticed any substantial issues.

The biggest thing is that when I disconnect my iPod it ejects the CD tray instead.  Nothing too big, and I'm sure there's a work around, but it's been frustrating me.

---

