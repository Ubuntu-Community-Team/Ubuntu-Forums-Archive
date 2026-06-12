---
title: "Cheese Photobooth Webcam Problem"
date: 2008-12-10
forum: General Help
---

### Post by Prominence on 2008-12-10
[FONT="Arial"]Cheese Photobooth isn't working all of a sudden, and I have no idea why. Every other Webcam app works, what's up with this? How do I fix it? The area where the webcam vid thing should be is not there, just nothing.[/FONT]

---

### Post by Prominence on 2008-12-11
anyone?

---

### Post by soro2005 on 2008-12-11
Cheese uses the settings from gstreamer. Try hitting <alt>+<f2> and enter "gstreamer-properties" in the box that opens (without the quote). On the "Video" tab, play with the Input settings.

Having said that, there's currently a major shake up in the way Ubuntu handles webcams. You may have to look for a solution for your specific model.

---

### Post by Prominence on 2008-12-11
Any idea when it will be fixed?

---

### Post by soro2005 on 2008-12-11
I think that most people have had problems with camorama, rather than cheese. Talking about Intrepid, anyway. Yours might be a different problem, but if it's related to the new libv4l library, then it depends on your webcam when it's going to be fixed/adapted, I guess.

There's an [entry in the sticky on known problems in Intrepid](http://ubuntuforums.org/showthread.php?t=966436). Perhaps that helps, or else you could provide info on your webcam.

---

