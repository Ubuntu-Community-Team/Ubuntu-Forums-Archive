---
title: "Can I play wmplayer stream video?"
date: 2005-10-15
forum: Desktop Environments
---

### Post by MikeyXX on 2005-10-15
I have a site that I go to with WMPlayer. It's streaming video. I go into Open URL and type my [http://domain:port](http://domain:port) and I can watch the video (it's internal). This works flawlessly on XP. Slightlyl hiccupy with my PPC but I can't figure out how to do it on UBUNTU. Any suggestions?

---

### Post by MikeyXX on 2005-10-15
Ok, found that if I run mplayer mms://domain:port It'll play. really chunky, but it'll play. How do I smooth that puppy out?

---

### Post by kaput on 2005-10-16
Maybe this isn't what your looking for, but...

For most streaming video that is located at a "mms://" address, I usually use mimms, which rips the stream to disk so I can watch it later without worrying about buffering issues.

You should be able to install it via a simple "sudo apt-get install mimms".

---

### Post by MikeyXX on 2005-10-16
Good call. Will it allow me to view it live as well by chance?

---

### Post by kaput on 2005-10-16
Well, yes, in a way. When you invoke mimms, it will begin to download the file into your present working directory. Once the file is created and begins downloading, you should be able to click on it and watch it (what's been downloaded so far, anyway), so long as the file is downloading faster then you're watching it. But then you're basically back to the issue of possibly having buffering issues. I usually start the stream rip, let it get a good way into the file, and then start watching. 

I understand that streaming media is bufffered in media players, but with mimms, I can let half of a 35 megabyte file be "buffered" to my disk before I start watching rather than an insufficient 512k buffer by streaming directly into a media player .

I basically do the same thing with wget with other media types, but mms:// locations require mimms to download the file.

---

