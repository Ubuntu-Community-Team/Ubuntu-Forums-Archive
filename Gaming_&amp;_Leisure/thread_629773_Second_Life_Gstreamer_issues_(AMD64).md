---
title: "Second Life Gstreamer issues (AMD64)"
date: 2007-12-02
forum: Gaming &amp; Leisure
---

### Post by Menthol on 2007-12-02
I've recently installed Second Life on Gusty Gibbon 64bit. Everything runs smoothly apart from I cant get it to play streaming video inside the client.
I've installed virtually every gstreamer plugin under the sun all to no avail.
I'm still getting this message from the client : 

 grab_gst_syms: Couldn't load DSO: libgstreamer-0.10.so.0

and

 init: Couldn't find suitable GStreamer 0.10 support on this system - video playback disabled.

The gstreamer files are installed, I've done a file search for them and they are there, I've even copied them into the lib directory of second life and it still wont work.

Anyone have any ideas or is anyone having similar problems ?

---

### Post by matthewcraig on 2007-12-02
Doesn't second life say they only support 32-bit ?  I saw they recommend installing the 32-bit binaries if you want to use their software.  Surprised that no one has helped them make their code 64-bit compatible, with them opening the codebase and all.

I bet once they make it compatible with both architectures, we would likely see the client as a managed Debian+Ubuntu package in Synaptic.

---

### Post by werewolfzx8 on 2007-12-02
I use the 32-bit version of Ubuntu (thinking about going 64), but I still have issues with streaming video, and sometimes music. It's still Alpha, so it's to be expected though...

---

### Post by Menthol on 2007-12-03
It runs really well on 64bit and the getdeb site had 32bit and 64bit versions, however once I installed it I then found that the package was out of date and I downloaded the upgrade, which I'm not sure is a 64bit version. Anyhow it runs just fine, apart from the streaming video.

I went to the Ubuntu pyramid in Second Life and went and asked a few people, none had issues with streaming video, but none I spoke too used 64bit.

If it is a 64bit issue I'll just live with it until it gets fixed, but would be nice to know one way or the other. If its not a 64bit issue I'll continue to find a fix.

---

