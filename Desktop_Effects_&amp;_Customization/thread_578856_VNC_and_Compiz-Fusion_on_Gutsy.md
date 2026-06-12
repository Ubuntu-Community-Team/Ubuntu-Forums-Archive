---
title: "VNC and Compiz-Fusion on Gutsy"
date: 2007-10-17
forum: Desktop Effects &amp; Customization
---

### Post by Prometheus7 on 2007-10-17
Upgraded to Gutsy last night and was surprised to find out that all of the desktop effects work in a VNC client window on another machine! This for whatever reason did not work for me in Feisty (maybe it was the version of compiz fusion that I had installed). I thought that this wasn't previously possible though? Anyone know why this works now?

---

### Post by diablo75 on 2007-10-27
I can't say I've had the same experience, though this might have something to do with the way I'm starting the connection.

I have a friend with a shortcut I made on his desktop that invokes the following command: 

```
x11vnc -connect myhost.dyndns.org:5500
```

The video feed from his computer to mine locks up shortly after connecting, unless compiz effects are disabled.

Should I be using something other than x11vnc at the command line?  Will vncviewer -connect work?

---

### Post by krunge on 2007-10-28
Try adding "-noxdamage" to the x11vnc command line.  More info: [http://www.karlrunge.com/x11vnc/#faq-beryl]("http://www.karlrunge.com/x11vnc/#faq-beryl")

---

