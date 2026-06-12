---
title: "Nautilus; tiedoston oletussovelluksen vaihtaminen"
date: 2006-08-17
forum: Desktop Environments
---

### Post by Markus Valkeapaa on 2006-08-17
Hi all!

Nautilus keeps associating ASCII text files with extension .dat to MPEG video files. I have tried to change this with 'right mouse button - Properties - Open with' function. I wonder if there is a "lower level" way to assign file extensions to certain applications? 

-Markus

---

### Post by philippe_carlo on 2006-08-17
Take a look at /etc/mime.types, maybe the dat extension is in there. Any idea why the open-with won't work? I seem to have successfully changed it that way.

---

### Post by Markus Valkeapaa on 2006-08-17
> **philippe_carlo said:**
> Take a look at /etc/mime.types, maybe the dat extension is in there. Any idea why the open-with won't work? I seem to have successfully changed it that way.

Yes, /etc/mime.types has 'dat' listed, alltough not for a video application. Taking it away did not solve the problem though. I don't understand howcome open-with does not work.

-Markus

PS. Sorry for the Thread name. Could not edit it. Originally forgot I was posting in "english" forum.

---

