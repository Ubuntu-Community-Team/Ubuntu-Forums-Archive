---
title: "Amarok Skipping thro' playlist-no sound"
date: 2006-06-10
forum: Desktop Environments
---

### Post by bodkin on 2006-06-10
Have followed many similar  threads but they end without  a result  .                                                                                                                                
Amarok skipps thro the play list with no sound.Have installed requirements  of the wiki
and other Ubuntu Dapper help sites(this forum also) They do not provide me
with an answer.Rhythmbox works ok,but i prefer Amarok.I have it working great on a Debian Etch beta 2 install. It must have passed me by but i cannot see what i have missed.
The dapper install was fresh,Gnome is improving all the time.
Many thanks in advance.

---

### Post by Jucato on 2006-06-10
What audio format are you trying to play? If you are trying to play MP3s, etc., you need the libxine-extracodecs package from multiverse.

For reference, read this: [https://wiki.kubuntu.org/RestrictedFormats](https://wiki.kubuntu.org/RestrictedFormats)

Btw, GNOME and KDE now have different methods to get these codecs installed, because GNOME is using GStreamer, while KDE is using Xine currently (because GStreamer is broken in KDE).

---

### Post by bodkin on 2006-06-11
Many thanks Fenyx- I had been over this Multiverse route many times
but as it was highlighted in the Installation Media, i did not notice 
the  Button was Not  activated.
Problem solved ,again many thanks

---

### Post by Shonkin57 on 2006-06-11
Thank you so much! This solution worked for me as well, after I'd just about despaired of seeing Amarok work. I'm loving Dapper otherwise, and now have my Amarok working as well. I'm still baffled as to some of the wierd quirks re having to install odd files like this and so forth, but hey, Linux isn't just an OS... it's an adventure!

Again, Thanks!

---

### Post by onlybui on 2006-06-11
adding libxine-extracodecs worked for me as well...

---

