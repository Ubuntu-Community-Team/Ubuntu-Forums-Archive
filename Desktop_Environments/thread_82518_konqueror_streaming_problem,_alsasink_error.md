---
title: "konqueror streaming problem, alsasink error"
date: 2005-10-26
forum: Desktop Environments
---

### Post by jesse on 2005-10-26
Hi. 

I recently switched from Ubuntu (Gnome) to Kubuntu (Kde), though I still use both Gnome and KDE applications as I need all of them. 

I mostly still use firefox for internet browsing, but I would like to use konqueror too. I have gotten all of the plugins to work in Konqueror except for av streaming. Every time I try to play a real player stream, e.g. on my.yahoo or Czech TV's website, I get an error message about "alsasink" and then konqueror crashes. :confused: 

I don't have any sound problems in any other programs. 

Very annoying. 

I don't mind using firefox, but since I'm running Kde I think it would make sense for konqueror to work. 

I read about this bug already, but I was wondering if anyone knew of a work around.

---

### Post by majkmil on 2005-11-03
I have the same problem with alsasink in Konqueror, but mine also asks for xvimagesink also. I just moved over from Gnome and I am getting my feet wet. I was using MPLAYER in firefox and it worked like a charm. Please Help!

---

### Post by TomG on 2005-11-03
Same for me :( : alsasink + xvimagesink error messages = crash of all Konqueror windows...
Would be happy to find a fix.
TomG

---

### Post by majkmil on 2005-11-03
anyone?

---

### Post by TomG on 2005-11-04
alsasink comes from GStreamer plugins (gst-plugins).
On gstreamer.net the latest stable version is the 0.8.11 and it seems not have a future ("DISCONTINUED")...
The core dev version is 0.9.4. Does anyone has tested it yet ?
Is it usable for fully unstable ?

---

### Post by jesse on 2005-11-04
I found that when I installed kaffeine and the kaffeine mozilla plugin it solved the problem. I also changed the engine from gstreamer to xine. Most streams work now in konqueror, but not all. At least konqueror doesn't crash any more, and for the streams that don't work I can use firefox if needed.

---

### Post by majkmil on 2005-11-06
How do I change the engine from gstreamer to xine?  I installed every thing I could find related to plugins in Korqueror. I reinstalled Koerquerorm also.  Thanks

---

### Post by majkmil on 2005-11-06
How do I change the engine from gstreamer to xine?  I installed every thing I could find related to plugins in Korqueror. I reinstalled Koerquerorm also.  Thanks

---

### Post by Specialsauce on 2006-01-31
i know that this is a really old thread, but is there an answer to this? i cant figure out how to change the engine...

---

