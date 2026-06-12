---
title: "MP3 conundrum"
date: 2006-08-28
forum: Desktop Environments
---

### Post by dont42panic on 2006-08-28
Ubuntu Friends,

I recently picked up an MP3 player. A Sandisk Sansa M240. Nice little player. Issues though. With Windows, I can browse the file system and freely add and remove MP3, but, alas, with Linux I cannot,

Running Dapper and fully updated with all necesary codecs and apps.

If a modern Linux kernel doesn't see the file system, then there has most certainly been a concerted effort to thwart us non standard OS types.

Would a kind soul please inform me briefly why this is happening, and more importantly how I can circumvent this inconveniance?

Thanks in advance,

James

---

### Post by orb9220 on 2006-08-28
My sansa m230 shows up in /media/sansa m230 when I plug it in. It is a usb device and shows thier fine I can use nautilus to drag and drop mp3's thier or use amarok 1.4.1 and add device thier then connect to my library and presto chango add songs from my library.

Did you actually look in your /media folder to see it thier when you plug it in? It does do popups like windows does.

---

### Post by dont42panic on 2006-08-30
OK. Let me clarify and reiterate.

Rereading my post, it would seem that I jumped to some conclusions and mislead.

I can browse the file system using Nautilus. It shows the correct amount of disk space used and avaible. It doesnt however list my MP3s. The MP3s were added using a Windows machine. 

Havnt tried yet to add/remove on my linux box. In fact, I wont be home for a bit.

So, will do a test with the Ubuntu machine and if all goes well, then will just slave the windows HDD to the Ubuntu machine and transfer the whole audio collection.

Will post back. 

Thanks

---

### Post by tmckellar on 2006-09-01
Here's the issue you're having. When you plug your mp3 player into a windows box I'm assuming Windows Media Player opens up. If so you need to go into the settings and under usb change it from autodetect to MSC. In autodetect it will show up as an mp3 player in windows and simply flash storage in Ubuntu. Changing it to MSC will make it so in both Ubuntu and windows (and possibly Mac) your player will show up as a flash drive. I discovered this when I first got my m230. For whatever reason it won't let you see the files in Ubuntu you put on it in windows in autodetect mode.

And out of curiousity have you tried putting an entire album on your player yet in windows? And if so have the tracks played in order on the player? I also had that problems transferring files from windows. Strangely enough that issue is non-existent transferring files from Ubuntu. Which is great cause I don't like windows anywho.

---

