---
title: "Rhythmbox won't play streaming audio"
date: 2005-02-04
forum: Desktop Environments
---

### Post by dandeguire on 2005-02-04
I recently installed ubuntu, and I'm trying to listen to a radio staion over the web.
They use an ASF stream.  I've tried using rhythmbox, but it just sits there buffering forever.  Is there something I missed?
I've also tried Totem, but it wouldn't even open the stream.

Thanks for any help.
Dan

---

### Post by valadil on 2005-02-04
I haven't had much luck streaming with rhythmbox.  xmms did the job pretty well though.

---

### Post by dandeguire on 2005-02-04
I install xmms, but it looks like it only takes files.  How do I get it to take a stream from the web?

---

### Post by valadil on 2005-02-04
When you're getting the stream from the web I assume you're clicking on a link somewhere.  When firefox asks what to do with the link try having xmms open it.

---

### Post by Xian on 2005-02-04
[QUOTE=dandeguire]I install xmms, but it looks like it only takes files.  How do I get it to take a stream from the web?[/QUOTE]
Read "Enable MP3 support in Rhythmbox" on the [FAQ](http://www.ubuntuforums.org/showthread.php?t=3713) thread.

---

### Post by DougInKY on 2005-02-04
Get XMMS with apt-get. Then go to the streaming site you want to listen to and when Firefox asks you what you want to do with the pls file, tell it to open it with /usr/xmms
You can also get most streams to tell you what the piece and artist is by selecting Options/Preferences/MPEG Layer 1/2/3 layer and then click Configure and then select the Streaming folder and at the bottom it will have Shoutcast/ICEcast select buttons. Select both and you are set.

Doug

---

