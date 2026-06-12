---
title: "Changing resolution, with no physical monitor connected"
date: 2014-06-17
forum: Desktop Environments
---

### Post by askeuhd on 2014-06-17
I have a server running Lubuntu 14.04, which I control remotely using TeamViewer, with no physical monitor connected. 

Connected using teamviewer, a resolution of 1024x768 is automatically applied. It can't be changed using TeamViewer's resolution tool.

Running xrandr, I'm getting the following output:

```

xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 32767 x 32767
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```

Unsupringsly it states that no monitors are connected, but it does indicate that a resolution of 1024x768 is applied to "Screen 0"

Is there anyway to change this resolution? Ideally permanently, but a fix that requires me to change it on each connection/reboot is fine. Something like 1920x1080 would be ideal, since it matches the resolution on my guest machine.

---

### Post by rahul4557 on 2014-06-17
See if this helps..

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by askeuhd on 2014-06-17
Thank you for that suggestion. It seems as though the only solution really is to edit the xorg.conf, and it seems I won't be able to do so, without a physical monitor connected. I will update this thread when I have located one, and tried editing xorg.conf. (I used my TV to install Lubuntu on the server, but overscan issues makes it unusable for much else)

---

### Post by Ola_Billinger on 2014-10-10
Hi!

> **askeuhd said:**
> Thank you for that suggestion. It seems as though the only solution really is to edit the xorg.conf, and it seems I won't be able to do so, without a physical monitor connected. I will update this thread when I have located one, and tried editing xorg.conf. (I used my TV to install Lubuntu on the server, but overscan issues makes it unusable for much else)

How did this go for you, did you find a good resolution? I have exactly the same problem. 

Thx,
Ola

---

