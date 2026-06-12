---
title: "Rhythmbox Shuts Down"
date: 2006-08-30
forum: Desktop Environments
---

### Post by Erik Pritzl on 2006-08-30
I am having a problem with Rhythmbox shutting down by itself.  I am using a shared folder (through Samba) and my music library is stored on another desktop using Windows XP.  The folder shows up as mounted on my desktop.  Everything was working fine until about 2 weeks ago.  Now when I start up Rhythmbox, it grabs the music library from the shared folder and populates the playlists.  I can start playing a song, but it will shut down about a minute into a song.  

I also have an issue with Rhythmbox playing AAC files and music that has been downloaded from iTunes.  That doesn't suprise me too much as the files downloaded from iTunes are protected.  I have tried adding support for other file formats (faac, faad.)  I'm not sure if something I did there caused the other problem.  There are some files that never seem to make it into Rhythmbox even though it is set to check for new files.   

I have tried using other music players, but couldn't get them to work with a music library on a server.  They seem to like libraries that are actually on the hard drive.  

I really, really like Ubuntu.  I started using Linux about 6 months ago with Xandros.  I had too many problems and switched to Ubuntu.  I won't go back.  I have an older laptop (HP Omnibook xe3) and this has been working fine.  The hardware detection has been perfect and the whole distro is easy to use.   

Any help is much appreciated!

---

### Post by Rhubarb on 2006-08-30
I've heard a few people on this forum have the same problem with rhythmbox playing music with samba.  Sadly I can't remember if there was a solution to the problem.  Perhaps the next version of rhythmbox or samba will fix it all up.

One way you could try, is to ditch filesharing on your winxp box, and install filezilla server (do a search for it on sourceforge.net).
Filezilla server is an FTP server, you can set up an account with a username and password.  Then on your Ubuntu box you can connect to the FTP server.
Hopefully this would work out to be more stable for you.

Filezilla server can be set to start on computer start up.  So you won't need to do anything once it's all set up.

I wouldn't bother about trying to get iTunes music to play, they're all DRM'd up to make life more annoying for us all.  In future buy your music online from someone that offers ogg / flac / or mp3 DRM free music.

Not sure why Rhythmbox for you refuses to update some files to its playlist.

... If all else fails, you could always liberate your xp box :D

---

### Post by xtknight on 2006-08-30
My Rhythmbox always froze up (compiz subsequently dimmed it) when I had any samba share, regardless if I added music from the samba share or not.  Check **dmesg**.

---

