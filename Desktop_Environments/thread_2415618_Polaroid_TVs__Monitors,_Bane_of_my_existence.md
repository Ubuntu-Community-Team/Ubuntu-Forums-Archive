---
title: "Polaroid TVs / Monitors, Bane of my existence"
date: 2019-03-28
forum: Desktop Environments
---

### Post by thatsmyboy on 2019-03-28
I still have my trusty Zotac box puttering around on the interwebs. I still occasionally have reason to plug it into a Polaroid monitor (this time a TLX-02311B 23" ) and I still have the crazy flickering error-spawning behavior when I do ([as described here]("https://ubuntuforums.org/showthread.php?t=2236871")). At this point I'm just griping, because it likely won't get fixed, but I would like to know how a monitor and computer communicate to get display settings configured on the fly. If I knew what to look for, I might be able to crack this nut before it makes ME go nuts. Happy computing everybody!

the box specifications are as follows:
Zotac ZBOXSD-ID12-PLUS Barebone Mini-PC
Intel Atom D525 1.8GHz processor
1GB DDR3 Ram
500GB Toshiba Hybrid Drive
Intel GMA 3150 Graphics, HDMI,
WiFi

---

### Post by Autodave on 2019-03-29
The first thing that I would do is try another cable.  What kind of cable are you using: VGA, DVI, HDMI, ?  Cables do fail.  The monitor tells the PC, via the cable, what its resolution and refresh rate is. If the cable is cheap or failed, that info doesn't get relayed.

---

### Post by thatsmyboy on 2019-03-30
Thanks for the reply, I have used both an HDMI cable and a VGA cable. The VGA I have used with another computer on this monitor successfully, the HDMI is relatively new and also cheap. So you do bring up a good point. Can you point to any resources that point to the technical details of the handshake?

---

### Post by Autodave on 2019-03-30
[https://en.wikipedia.org/wiki/Extended_Display_Identification_Data](https://en.wikipedia.org/wiki/Extended_Display_Identification_Data)

That site explains it rather well.

---

