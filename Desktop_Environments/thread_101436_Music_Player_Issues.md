---
title: "Music Player Issues"
date: 2005-12-09
forum: Desktop Environments
---

### Post by dystrust on 2005-12-09
When I try to open an MP3 file in Music Player, I get the error, "The file is not an audio stream."  Any ideas on how to fix this?  I can play mp3s in Audacity, so I don't think it's an mp3 decoder issue.

---

### Post by abou on 2005-12-09
It probably is, actually.  Do you have w32codecs?

---

### Post by dcast on 2005-12-09
unfortunately it is a decoder issue you will need gstreamer0.8-mad to play mp3s in musicplayer

---

### Post by dystrust on 2005-12-09
My bad...  I must have forgotten to restart Music Player after installing the plugins.  Works fine now, thanks.

---

### Post by Kasanax on 2005-12-17
Hi - I'm a newbie (as in, started using Linux for the first time last week...), and I've been having the same problem. Would someone be able to show me how to find and install the required plugins/codecs?

Thanks!

---

### Post by Hairy_Palms on 2005-12-17
open synaptic from the menu and search for gstreamer0.8-plugins then install it and you can play mp3s in music player

---

### Post by Kasanax on 2005-12-17
Yep, that worked! Thanks for the help.

---

