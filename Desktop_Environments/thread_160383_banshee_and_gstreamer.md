---
title: "banshee and gstreamer"
date: 2006-04-14
forum: Desktop Environments
---

### Post by Hairy_Palms on 2006-04-14
, i was just wondering, is it possible to allow banshee music player to use something other than gstreamer because its so damn slow. and gstreamer jumps all the time.

---

### Post by croak77 on 2006-04-15
I pretty sure there are options to configure helix/real player or vlc as a backend. I think Mandriva cooker has rpms for them.

---

### Post by Hairy_Palms on 2006-04-15
hmm i psoted wrong forum, meant to put this in dapper :/ no options for real/vlc as backend anyway i have both installed

---

### Post by croak77 on 2006-04-15
Well you would have to compile banshee by source and enable the options. From the website:

"--enable-vlc: Disabled by default, Banshee also supports the VLC ([http://videolan.org/](http://videolan.org/)) media engine. However, you must build your own libvlc.so from Jon Lech Johansen's snd123 ([http://nanocrew.net/2005/09/20/snd123/)](http://nanocrew.net/2005/09/20/snd123/)). Once you build snd123, copy the resulting libvlc.so library to mediaengines/vlc in your Banshee source tree, before running make install."

[http://banshee-project.org/Banshee_Source](http://banshee-project.org/Banshee_Source)

---

