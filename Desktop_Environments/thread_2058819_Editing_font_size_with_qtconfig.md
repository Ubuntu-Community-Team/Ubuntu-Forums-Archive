---
title: "Editing font size with qtconfig"
date: 2012-09-16
forum: Desktop Environments
---

### Post by slippyjim on 2012-09-16
Hiya,

I have a Acer Revo 3620 running Lubuntu 11.10 & qbittorrent v3.0.2 hooked up to my 40" Sont TV via HDMI.
I  couldnt get the DPI to adjust properly to make the text readable so  have adjusted the text size in Customize look and feel so I can actually  read it now. The only text I cant seem to make bigger is the text on  the taskbar and the text within qbittorrent.

I have been told that "qBittorent on Linux should use the qtconfig settings. Have you tried adjusting your fonts there?"
I have googled it and seen something about installing some qt3 or qt4 packages and then I got lost.

But I do not know how to do that as I am a complete noob to linux so any help is appreciated. 

Thanks

---

### Post by marinara on 2012-09-16
for taskbar text, there an icon size ooption on the bottom taskbar settings

---

### Post by slippyjim on 2012-09-17
Ive managed to change the icon size but the text stayed tiny. I'm not that bothered about that anyway, it is the text in qbittorrrent that is most important

---

### Post by slippyjim on 2012-09-19
I figured it out myself

sudo apt-get install qt4-qtconfig

Then system preferences -> qt4 config
select Font tab and increase size, simples

It didnt affect text on taskbar but Im not bothered about that

---

