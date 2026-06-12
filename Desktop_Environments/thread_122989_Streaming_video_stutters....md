---
title: "Streaming video stutters..."
date: 2006-01-28
forum: Desktop Environments
---

### Post by schnabea on 2006-01-28
Hi I used automatix to install the mplayer plugin for firefox. When I try to view streaming video such as movie trailers from apple.com, the video buffers and starts to play but it stutters. You can hear everything and watch everything but there are slight pauses every half second or so. Anyone have any ideas on how to remedy this?

---

### Post by kverde on 2006-01-28
Not that this helps you, but I have the same issue.  Thanks for posting this, maybe someone can help us!

---

### Post by Greg T. on 2006-01-29
I'm seeing the same thing, but only on certain files, WMV files in particular. It's exactly the same problem, though. The videos are jerky & stutter, as if pausing briefly every half second or so. I installed the plugin using Automatix, just yesterday.

The problem appears to be limited to the plugin, not mplayer itself. I tested one file by downloading to my desktop and running it locally using mplayer; it worked fine. I then cobbled a web page that linked to the file on my desktop; when I loaded the page, the plugin kicked in and playback began stuttering again. 

Automatix installs the latest version of the plugin (3.17). I'm trying to downgrade to an earlier version (3.11-1) that I had better luck with on my last computer. We'll see....

---

### Post by Greg T. on 2006-01-29
Downgrading didn't work. I switched to ESD in the mplayer plugin configuration and that took care of the stuttering, but now the sound is out of sync with the video.

---

### Post by Greg T. on 2006-01-30
[http://www.ubuntuforums.org/showthread.php?p=691671#post691671](http://www.ubuntuforums.org/showthread.php?p=691671#post691671)

---

### Post by schnabea on 2006-01-31
Thanks much, changing those conf files took care of everything.

---

