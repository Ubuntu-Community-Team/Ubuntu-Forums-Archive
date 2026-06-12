---
title: "GStreamer encountered a general supporting library error."
date: 2009-06-19
forum: General Help
---

### Post by metricspace on 2009-06-19
Hi, 

When I tried to play a swf file Totem asked me to install GStreamer-FFmpeg-Plug-in, which i did. 

however after installing the required plugged in, Totem thrown the msg. "GStreamer encountered a general supporting library error."

does anyone has any idea as to why this msg. is thrown and soln. to fix this.

Thanks & Regards,
metric

---

### Post by pendelton on 2009-08-01
I have exactly the same problem with no solutions as yet. Clean install of 9.04. I tried to view a video online but it just came up blank. I downloaded the link and opened it with Movie Player and when I press play I get the message:

> An Error Occured
GStreamer alternative encountered a general supporting library error.
I've checked for updates but nothing. I've even tried uninstalled GStreamer via Synaptic, rebooted. I then opened the video via Movie Player again which informed me that I didn't have what I needed to play the movie and would I like to install the required updates (can't remember exact message). I said yes, it installed GStreamer and all other required libs etc. but it still failed with the same error.

Any solutions or workarounds anyone?

---

### Post by pendelton on 2009-08-02
I now have streaming media working in Firefox at least. If you follow the steps at [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) they worked for me on 9.04. However, although I have an AMD Athlon 64 I did have to install the 32-bit version. The 64-bit steps returned a missing library error but the 32-bit steps worked fine.

---

### Post by donkhan on 2010-03-26
I found that installing "gnome-codec-install" worked for me.

---

### Post by kneedragon on 2010-05-26
> **donkhan said:**
> I found that installing "gnome-codec-install" worked for me.

Got that one. The problem remains.

---

### Post by agentbuzz on 2011-07-13
I also had the error, "GStreamer alternative encountered a general supporting library error.", and I adapted pendleton's remedy at [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) for my use. I still had the problem, so I went in to the NoScript preferences and checked "Temporarily allow top-level sites by default" and then Shockwave movies on this one particular site ran with no problem.

---

### Post by lawrencejohny on 2011-07-27
> **agentbuzz said:**
> I still had the problem, so I went in to the NoScript preferences and checked "Temporarily allow top-level sites by default" and then Shockwave movies on this one particular site ran with no problem.

Can you specify what you did here?

---

