---
title: "CD/DVD Drive Oddities"
date: 2009-01-05
forum: General Help
---

### Post by MikeRivers on 2009-01-05
I'm a brand new Ubuntu user. I have a passing knowledge of Unix (know a few command line commands and applications) but I'm not intimately familar with the names of all the configuration files and scripts that abound. I'm comfortable with editing files. But if you're inclined to tell me "You have ot add the CD drive to the .frammitzhowser file," at least tell me where that file is located and what the syntax is. 

I have the Ubuntu Studio distribution because someone (I'm gonna strangle him!) told me that this was a turnkey approach to playing with Ardour and other audio applications. I was curious to see if there was anything yet in Linux that I could recommend to someone wanting to do the sort of work that we've been doing in Windows and MacOS for many years now. 

So here's my problem, or problems:

The computer is an old Dell Optiplex G-110, dating back to around 1999. Pentium 3, 800 MHz, 512 MB RAM, latest (though that ain't so new now) BIOS version. There are two optical drives in it, an LG CDRW drive a few years old and a Samsung DVDRW drive that I got last year. Since the distribution ISO file was larger than a CD, I loaded it to a DVD, and set up the computer so that the DVD drive is the master and the CD drive is the slave. It booted the installation DVD and everything installed smoothly. I'm typing on that computer right now. I installed Ubuntu on a fresh hard drive. I didn't mess around with dual boot, and I wanted to retain the original Windows drive.

In case this means anything to anyone, the BIOS identifies the drives as follows:

IDE Drive 0 - TSSTcorp CDDVDW SH-5202N
IDE Drive 1 - HL-DT-ST CD-RW GCE-8240B

When I put a disk containing data files into either drive, after some time with the disk spinning, I get a pop-up message saying that the drive could not be mounted.  "DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken."

The disk, however, appears to be completely accessable. I can list the files on it using the file browser, I can open files (for instance, .doc files with the Open Office word processor) and there's even an "unmount volume" menu choice when right-clicking on the DISK in "Places", and an "eject" icon, which works. So apparently it is actually mounted regardless of what the warning message says. 

Both drives behave the same way. 

I haven't tried writing on a CD or DVD yet. I want to get rid of the suspicious stuff first, or at least know with reasonable confidence that it doesn't mean what it says. 

The other problem is what happens when I insert an audio CD. It's recognized as an Audio Disk. Initially a warning message came up saying that it couldn't find sound-juicer. Well, neither could I. Nor, when I checked the Preference|Media, was that the default application to open an audio CD. It was a CD burner (why would you open a CD burner, unless it's also a player - I didn't try it - when you want to listen to a CD?). So I set that preference to Movie Player, and now when I put in a disk, Movie Player opens. 

However, that comes up with an error message "Could not open location. You may not have permission to open file" (but it doesn't say what file or location). If I try to beat it into submission by telling the Movie Player to Open the Audio CD, it lists all the track files. When I click on one and tell it to play, it says "Playing" for a couple of seconds (but there's no audio) and then it drops back to "Pausing." Just in case this was an audio issue, I started JACK before opening the Movie Player. 

Behavior with Audacious, another player program that came with the kit, is essentially the same - no music. I know the CD is good. It plays in a real CD player (it's a commercial one, not home made) and it plays in other computers. It even plays in this computer, on either of these drives, when I plug in the Windows hard drive and use any number of Windows media players on it. 

Using the file bowser, I can see files on the CD. I can drag a file to Audacity and it will play. 

I'm wondering if, due to the age of the drives and the age of the computer, the CDROM driver in the Ubuntu installation isn't fully compatible with my drives. Are there alternate drivers that I can try? 

Tell me where to look and what to look for and I'll provide details on what I have. 

Or maybe all of this is just normal?

---

### Post by xscd on 2009-01-10
This dbus error is happening to my brother also. He upgraded from Hardy Heron to Intrepid Ibex and this dbus error began to happen when he inserts a CD or DVD data disk (iso9660 disk).

The problem also seems to be happening with other people on the forum, although finding the particular messages is difficult because of subject lines and not knowing what terms to search for.

The kernel is seeing the CD or DVD drive (sr0 --> scd0), but after a delay of perhaps a minute, the dbus error message is displayed:

[INDENT]DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken. (OK)[/INDENT]

After the error message, the data CD or DVD can be browsed in Nautilus, although on another friend's computer running Intrepid, the data CD or DVd is not even recognized though it is an iso9660 filesystem burned with K3B or Brasero (he tried both).

---

### Post by MikeRivers on 2009-01-10
> **xscd said:**
> The problem also seems to be happening with other people on the forum, although finding the particular messages is difficult because of subject lines and not knowing what terms to search for.

The kernel is seeing the CD or DVD drive (sr0 --> scd0), but after a delay of perhaps a minute, the dbus error message is displayed

After the error message, the data CD or DVD can be browsed in Nautilus

I'm not following all the details of your reply, but it sounds like 
(a) This isn't unique to my system
and 
(b) As long as it works, don't worry about the error message

I'm about to put this system on the shelf and maybe try again in a few months. Maybe the bug fixers will have it sorted out by then.

---

