---
title: "XMMS Playlist not working"
date: 2006-10-29
forum: Desktop Environments
---

### Post by polt on 2006-10-29
Hello All!

I saved a *.pls playlist file in XMMS and I cannot get it to play.  Basically, my music files are on an external drive mounted under /media/usbdisk.  When I open the playlist, it scrolls through all of the songs without playing them, because it can't figure out where any of them are.  

When I look at my playlist file, the entries are as follows:
> File5=/media/usbdisk/Chuck Berry - Deep Feeling.mp3
Then, when I look at the file info in XMMS to see what XMMS is looking for, it says this:
> /home/polt/Desktop/File5=/media/usbdisk/Chuck Berry - Deep Feeling.mp3

Ah, poor XMMS, you are looking in the wrong place!

Does anyone know of any way to remedy this situation?  I would greatly appreciate any help!  Thank you everyone!

---

### Post by polt on 2006-10-30
I'm actually kind of wondering if anyone else has been able to get playlists to work in XMMS?  I might need to put the playlist in the same directory as the music or some such.

---

### Post by EvergreyNY on 2006-10-30
I think it's just that XMMS doesn't read *.pls files very well. I got the same error but then created a playlist as *.m3u and there was no issue.

---

### Post by polt on 2006-10-31
Okay, I tried that and it seemed to work!  Thank you!  What is the deal with *.pls files anyway?  Are they supposed to be non-affiliated with any particular program, or some such thing?

---

