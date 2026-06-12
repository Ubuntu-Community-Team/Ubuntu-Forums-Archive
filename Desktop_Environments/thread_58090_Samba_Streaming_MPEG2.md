---
title: "Samba Streaming MPEG2"
date: 2005-08-18
forum: Desktop Environments
---

### Post by crazydahveed on 2005-08-18
I am having someproblems streaming mpeg2 files to my Ubuntu box.  I have a windows XP box that I am currently sharing out files that I record off my TV tuner.  On the XP/2k boxes, everything works fine.  However, I also have 2 Ubuntu boxes.  I have installed win32 codecs, MPlayer, samba, and many other things (lost track) trying to get the videos to stream onto the Ubuntu machines.  I have mounted the shared drive (through the GUI) and I still have the following problem.  The files are opening in Totem and they will play 2-3 seconds, then buffer for about 1 second, then play 2-3 seconds.  It goes on like this as long as you can tolerate it.  I tried opening the samba shares in mplayer, but I was not able to determine how I could actually open them in mplayer (does it not have samba support?).

Am I doing something wrong or missing something terribly obvious?  I have searched the Ubuntu forums, google, etc.  I can not seem to find anything on this.  Perhaps I am using the wrong search terms, or am attributing the problem to something that is not causing it.  Any help would be *greatly* appreciated.

Thanks,
David

---

### Post by nad on 2005-08-19
Have you modified this section of the smb.conf file?

############ Misc ############
(snip)
# Most people will find that this option gives better performance.
# See smb.conf(5) and /usr/share/doc/samba-doc/htmldocs/speed.html
# for details
# You may want to add the following on a Linux system:
         SO_RCVBUF=8192 SO_SNDBUF=8192
   socket options = TCP_NODELAY

---

### Post by crazydahveed on 2005-08-20
Ok, after reading your post, I did a little research and started playing with the packet sizes.  However, they did not seem to affect the performance much.  I increased the packet size all the way up to 16384 on both the send and receive, to no avail.  In each case, the problem persists.  The machine I am doing my testing on is directly connected via a crossover cable, and the other machine having the problem is going through a home wireless router.  The machine hosting the files in on a wireless connected, however, the other MS boxes can access the files without problem.  It is a 2GB file that lasts 1 hour.  So it does not have to maintain a very high speed to stream the data.  All MS boxes are XP.  Does the XP factor play in some how?

This is just confusing me.  I want terribly to move away from the MS world, But if I cant get the streaming to work correctly, my dear brothers are going to make me turn their box back into an MS box.  Really dont want to do that...so any ideas?

David

---

### Post by nad on 2005-08-20
How about the Totem Network preferences or [http://xinehq.de/index.php/hackersguide](http://xinehq.de/index.php/hackersguide) .

I don't see a way to adjust xine's buffer sizes without recompiling.

---

### Post by crazydahveed on 2005-08-20
Totem prefs are set to Internet/LAN and the xine looks a little harder than what I think I would be capable of.  Is this uncommon?  It seems like since it is happening to two different machines it shouldnt be.

---

### Post by crazydahveed on 2005-08-22
Is this a common problem?  Is it that no one has ever had this problem before, or that no one is attempting this?  I copied over the mpeg file to my home directory and it took all of 20 minutes to do so (for an hour long/2GB video).  I am able to play video feeds off the internet without a problem.  Is this a problem with totem's buffering of the playback? (not enough buffer space on disk?)  Is there another player I can use to view mpeg files over a samba share?  If you can open samba files over MPlayer, I have not been able to do so via the GUI; I am trying the command line at the moment (creating a path with no spaces for simplicity's sake).  Any help/comments would be greatly appreciated.

---

### Post by nad on 2005-08-22
Okay. This problem has been bothering me. There is no reason for lan throughput to not support streaming media.

I've come acroos a couple of suggestions.

This may sound silly, but, get rid of all the comments (including unused directives) in your smb.conf file. Apparently, the samba daemons read the file at startup and cache it. Then reread its cached copy every 20 seconds. Make a backup copy first, of course.

Stop the daemons ( /etc/init.d/samba stop ) and restart them with a higher priority ( nice -n -10 /etc/init.d/samba start ).

You may also try the options:
socket options = IPTOS_LOWDELAY TCP_NODELAY

and play with the cache size:
write cache size = 131072 (This is conjecture, some will base this on the cache size of the hard drive.)

---

### Post by crazydahveed on 2005-08-23
Ok, I tried all the settings you suggested to no avail.  I played with the cache size; doubleing it over and over again, and trying less even.  In each case; I noticed no difference.  Now here is something interesting to throw into the mix.

The program I use to record the shows also setups a webpage, through which, you can watch the shows.  When viewing them through the web interface, there is NO problem.  Everything works perfectly.  If I then try to open the share and play the file, it fails.  Oh the inhumanity!

David

---

### Post by minio on 2005-08-23
I've got the same problem + totem refused to play subtitles from shared files, but if I mount samba shares as a regular drives (mount -t smbfs pathtoshare wheretomountit) everything works fine.

---

### Post by nad on 2005-08-23
The only other suggestions are to make certain that the MS clients file sharing features are up to date, the firewall is disabled (not just turned off), rolling back samba to a previous version and making certain that all hardware is modern and fully supported on the operating system used.

By the way I have forgotten to mention that some have increased performance by specifically setting the transfer mode to half duplex, disabling auto or full duplex mode on their nics. Seems counterintuitive (shrugs).

---

### Post by MetalMusicAddict on 2005-08-27
Ive been searching my ass off but I know I read that MPEG2 has problems streaming. Ive always had problems with unless it was on the machine itself. Ill still look for the info.

---

### Post by suoko on 2008-01-02
Nothing to say.

---

