---
title: "MTP Music Device Recognition"
date: 2009-05-30
forum: General Help
---

### Post by dsfitzpat on 2009-05-30
Hi, I'm wondering if anyone can help me to configure the automount behaviour for my mp3 player - it's a Philips Gogear 1630.
There was some related discussion on this thread: [http://ubuntuforums.org/showthread.php?t=1119627](http://ubuntuforums.org/showthread.php?t=1119627) but it's since been closed.

Anyway, here are the details: I can manage the device OK using libmtp and Gnomad (Amarok 1.4 did a much better job but is no longer available!) or using mtpfs.  The trouble is that automount support was added for mp3 devices in Jaunty, but my player is not detected correctly: Ubuntu now recognises it as Philips Gogear HDD14XX (rather than 16XX) and therefore thinks that it has 1 GB capacity, instead of the 6 GB capacity it actually has.  This means that I can't transfer files when it automounts (I can't even transfer the first 1 GB - I tried and the files were all corrupted).

The reason this is annoying is that this player doesn't function all that well with Linux to begin with, and the mounting process can take 5-10 minutes, and until it finishes, and I unmount it, I can't manage it using libmtp.  I'd like to be able to plug in, transfer files, and go.  This means I need to either
   (a) Stop it from mounting altogether
   (b) Get Ubuntu to recognise it correctly

Any ideas?

(In hindsight I should have gone with a Creative Zen player but the $30 price tag on the Philips player was hard to pass up!)

---

### Post by nereid on 2009-06-12
The Zen player isn't that much better ;) The automount feature from Jaunty always freezes my Zen player and I have to reset it via the pinhole reset button.

So I would also be interested on how to stop the automounting issue or get it working, without crashing my jukebox.

---

### Post by dsfitzpat on 2009-07-04
Is there anyone out there who has this feature running smoothly for them?  If so, with what mp3 player?  I had heard that the Zen players run smoothly with libmtp but if the automount is still getting in the way, that makes it less ideal.

On a related note, it would be nice to find a program that can replace Amarok 1.4 as a device manager.  Exaile has an mtp device manager, but it crashes all the time for me and I haven't found it that user-friendly.  Gnomad2 works smoothly but only does one track/folder at a time (i.e. there's no queue feature, so you can't build the list and then go do something else while the tracks load).

Best-case scenario for me: 1. Connect to the device using libmtp.  2. Let me browse my music library using a tree view (eg. artist-album) 3. Let me build a transfer queue from the files in my library. 4. Display the amount of disk space remaining on the player vs the size of the queue.

I could do all of these in Amarok 1.4 but I haven't found anything that supports queuing or tells me how much disk space I have!

---

### Post by dsfitzpat on 2009-07-04
I should add that I had been using a newer version of libmtp (the one in the Ubunuto repos is something like a year out of date - they have 0.3.0 and it's up to 0.3.6).  Just in case that was the problem, I downgraded to the Ubuntu version, and the problem persists.  The trouble with the older version is that it doesn't detect my player properly - I have to edit a file in the source code (music-players.h) before installing.

Maybe my problem is that whatever is doing the mtp automount is using the out-of-date version of libmtp.  It's a bit confusing because Philips 14XX is not even on the list of players supported by libmtp, and that's what the computer is detecting my player as - so maybe it's not even using libmtp?

Anyway, if someone knows how to stop the automounting, or configure it, or something, I'd really appreciate it!  This is verging on making my mp3 player unusable with Ubuntu - and it had been working fine (if slowly) before.

---

