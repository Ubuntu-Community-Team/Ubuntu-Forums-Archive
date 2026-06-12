---
title: "Serpentine not handling mp3 files"
date: 2005-10-31
forum: Desktop Environments
---

### Post by raheesom on 2005-10-31
Serpentine is supposed to handle audio input using Gstreams.   I want to burn mp3 to CD and my Gstreams setup doesn't seem to handle mp3!

I installed "soundconverter" through apt-get.  It also uses Gstreams.  I see from its more obvious preferences screen that mp3 definitely is not included.

I can't see an  mp3 plugin in my apt-cache list.  How do I get mp3 enabled within Gstreams??

Tnx
Rupert

---

### Post by phanboy_iv on 2005-10-31
Use synaptics to install gstreamer0.8-mad
Also,try doing a forum/wiki search on this. MP3 support is a common issue.

---

### Post by raheesom on 2005-10-31
Thanks for your reply.  got the MAD plugin installed.  Serpentine now burns CDs for me!  Thanks.  Unfortunately the burn dlg froze on "fixating disk" but the CD seems to have burned fine, cause I can play it.  I guess I can live with that.....

---

### Post by phanboy_iv on 2005-11-02
No prob.

Hum.:???: 

Did you get any kind of terminal output?

I've used Serpentine a few times, and haven't had a problem with it.

Well, you could do some more experimentation with Serpentine to see if you can get the freeze to happen again, and file a bug report. Then, if you're lucky, you might not have to live with it when the next version hits!

---

