---
title: "Limit bandwidth SSH forward uses"
date: 2009-03-11
forum: General Help
---

### Post by XCan on 2009-03-11
Recently, I have been working a lot through ssh -X to a remote workstation at the same network. However, today I noticed, when monitoring the network traffic, that ssh caused a huge amount of traffic. This traffic of course arises when the forwarded screen was being updated (in this case calculations that updated a log windows continuously), and was going steadily at 100 MBit/s constantly. It feels like this is a bit extreme, and I'm wondering if anyone could give a few pointers as of how to limit the traffic caused by this.

Also, on a side note, I'm not really sure about the difference between ssh -X and ssh -Y, besides something according to the man being "trusted X11 forwarding, which I don't really know what it is. It would be great if someone could elaborate this. :)

---

### Post by LegendofTom on 2009-03-11
As far as the difference between ssh -X and ssh -Y, did you check the man pages?

---

### Post by XCan on 2009-03-12
Yah, but as I mentioned in the original post, I don't really know what it implies in more detail.

---

