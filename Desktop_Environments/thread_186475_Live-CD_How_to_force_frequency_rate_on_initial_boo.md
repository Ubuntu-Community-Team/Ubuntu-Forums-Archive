---
title: "Live-CD: How to force frequency rate on initial boot screen to 60 Hz"
date: 2006-06-02
forum: Desktop Environments
---

### Post by lptr on 2006-06-02
Target: Only booting into Live-CD with X...

Having dapper-desktop-i386.iso here - booting fine screen resolution changes up to 1600x1200x32 ... until X starts. Monitor frequency changes to 70 Hz leaving me a black screen without anything. I having just TFT monitor here. It does just 60 Hz and runs out of sync in higher modes :( 

Alt-F1 Switching to term works ok.

How to force frequency rate on initial boot screen to 60 Hz? Howto activate GRUB cmd line on boot screen and what entries need to be set that there is something visible when X starts?

---

### Post by lptr on 2006-06-02
[update] I successfully tried following form console:
(switching into it with Strg-Alt-F1)

# sudo dpkg-reconfigure xserver-xorg 
and selected vesa as driver, keyboard, deselected option glx (had some trouble with it in the past) all other defaulting etc. etc. 

then the important part for me (very late during cfg) there one can decide between refresh rate config low, middle and advanced. Selected middle there and choosed 1600x1200@60Hz 

Need finding process id of kdm (gdm would be valid for gnome)
# ps -e | grep kdm
# sudo kill 6101 
(6101 would be the first number got from ps for kdm)

then:
# startx

Well and Live-CD was there with KDE / X-Windows.

Again I having still trouble with my stupid KVM switch. Mouse is completely unusable because of that (stupid kernel timing bug?) - I expect if I restart X another time with mouse and another keyboard all works expectedly.

---

