---
title: "Getting Banshee keyboard shortcuts in Xubuntu (How-to)"
date: 2007-07-02
forum: Desktop Environments
---

### Post by ugm6hr on 2007-07-02
I couldn't get Rhythmbox to work on Xubuntu7.04 on my Acer Aspire 5050, so I installed Banshee instead.  I really like it, but decided it would be nice to get my Fn keyboard shortcuts to work with it to allow me to run it happily in the background (which I gather it does as default in GNOME).

Just in case someone else is struggling with this, I thought I'd post my solution:

1. I installed KeyTouch and KeyTouch Editor from Synaptic Package Manager.

2. I set up my keyboard Fn keys with KeyTouch Editor (Volume Up / Down, Mute, Play, Stop, Previous / Next Track), and saved the file.  While I was there, I set up a few other keys (program launchers etc)

3. Opened KeyTouch and load the keyboard file that I saved.  Then set up the key actions as below:
Play: *banshee --toggle-playing*
Stop: *banshee --shutdown*
Prev Track: *banshee --previous*
Next Track: *banshee --next*
Launch: *banshee --play-enqueued --hide --enqueue *

I also set the Volume Up / Down / Mute (as Amixer Up / Down / Mute).

This launches Banshee (by pressing Launch shortcut) in the system tray (although starts paused), and controls the tracks with the appropriate controls (with stop closing down Banshee).  Obviously, you can chose whatever controls you want, according to personal preference.

This was useful:
[http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys#Banshee_player](http://gentoo-wiki.com/HOWTO_Use_Multimedia_Keys#Banshee_player)
or in Terminal: *banshee --help*

---

### Post by ugm6hr on 2007-07-10
I realised that Keytouch is unnecessary.  XFCE has a "Keyboard Settings" page in the Settings Menu.

Just go into the Shortcuts tab, Add a Theme (e.g. Volume), then add commands as necessary.  I've given my examples (for my laptop).

Theme: Volume
Vol up: amixer set Surround 5%+
Vol down: amixer set Surround 5%-
Mute/Unmute: amixer set Surround toggle

Theme: Media
Play/Pause (also launches): banshee --toggle-playing
Stop (hides in system tray): banshee --hide
Next: banshee --next
Prev: banshee --previous

Haven't bothered with any of the other keys, since I have found I don't use them anyway.  Realised that this laptop doesn't allow PCM sound source to be muted/unmuted, so decided to use Surround, which only controls main speakers, not the heaphone socket.

---

### Post by jolla on 2007-08-08
> **ugm6hr said:**
> 
Theme: Media
Play/Pause (also launches): banshee --toggle-playing
Stop (hides in system tray): banshee --hide
Next: banshee --next
Prev: banshee --previous
.

If you want to control more than banshee try out [ReMoot]("http://www.kde-apps.org/content/show.php/ReMoot?content=63140"), it can handle most linux players (18 players). Instead of "banshee --next" you would write "remoot next" and that command will control "next" in banshee, Amarok, xmms, vlc, Rythmbox etc. :-)

---

### Post by revolutio on 2008-05-07
A bit of necromancy but it is still relevant.

I'm unsure whether this issue is related to Hardy or my own troubles with my keyboard and Xubuntu, but whenever I use these commands they open a new instance of Banshee even if one is already open.  Any ideas?

---

### Post by ugm6hr on 2008-05-07
Honestly, I can't help.

I have moved to Ubuntu from Xubuntu since Gutsy, and use the Rhythmbox default rather than Banshee.

---

