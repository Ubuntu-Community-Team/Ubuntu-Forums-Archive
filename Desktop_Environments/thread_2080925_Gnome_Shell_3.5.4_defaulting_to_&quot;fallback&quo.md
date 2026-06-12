---
title: "Gnome Shell 3.5.4 defaulting to &quot;fallback&quot; on Ubuntu 12.04"
date: 2012-11-05
forum: Desktop Environments
---

### Post by Arnethius on 2012-11-05
Hi, I'm starting to get frustrated with Unity, so I'd like to give Gnome Shell 3 a try on my 64-bit Ubuntu 12.04 installation. However, I have so far been unable to get anything other than the "fallback" Gnome desktop to work. So when I log into Gnome (not Classic or no effects), the desktop looks like gnome 2.

I have Gnome Shell 3.5.4 (supposedly) installed along with the gnome-tweak tool. My graphics card drivers are definitely installed and working correctly (although it is the NVIDIA CUDA developer driver version 304.54).

Otherwise, the set-up consists of two monitors (Xinerama).

Any ideas? My apologies if I have left out any vital information - please let me know and I'll get back to you with it. Thanks in advance,

Arnethius

---

### Post by markbl on 2012-11-05
Well gnome-shell 3.5.4 is miles away from the version in the 12.04 repos so it may help to explain how you installed that?!

I'm guessing you added the ricotz ppa. You should purge it off unless you are an expert who wants to continue to battle an unstable system. Unfortunately that ppa is bandied about these forums to newbies but using it is very inadvisable for most users. Just add the gnome 3 team ppa and then install the default 12.04 gnome-shell.

---

### Post by Arnethius on 2012-11-05
Hi Mark,

Thanks for replying. Yes, that is pretty much how 3.5.4 will have come to be installed (yes I added ricotz ppa, but had forgotten). I added that because the version of gnome shell that I installed from the Ubuntu repositories has the problem that I described above. Installing 3.5.4 has made absolutely no difference though - presumably because the instabilities you mention don't reside in fallback.
 
Anyway, I've heeded your advice and taken it back to the Ubuntu repository version - again with no change. 

Any other ideas please?

---

### Post by markbl on 2012-11-05
Does Unity work ok?

---

