---
title: "Very Big Fonts"
date: 2012-01-18
forum: Desktop Environments
---

### Post by cajimene on 2012-01-18
Hello and sorry for my english,

I just installed lubuntu 11.10, from livecd all fonts are perfects, but now are giants.

I have an Acer Aspire Revo, with nVidia ION, TV 37' 1080p (connected with hdmi).

I changed size from obconf, and ubuntu tweak, but don't work.

Any idea?

Thanks in advance

---

### Post by cajimene on 2012-01-21
Hi all,

The problem are the nvidia driver, i follow instructions from this link [http://forums.bodhilinux.com/index.php?/topic/204-solved-nvidia-drivers-and-fonts-size/](http://forums.bodhilinux.com/index.php?/topic/204-solved-nvidia-drivers-and-fonts-size/)

Thanks all

---

### Post by Anthon on 2012-11-02
It took me some trying out using the info in the provided link as an
Unquote entry would hang my X.

What worked for me is to add under 'Section "Monitor"' in /etc/X11/xorg.conf the following lines only:

Option "UseEdidDpi" "FALSE"
Option "DPI" "96 x 96"

before the EndSection.

Then logout/login 
If you screw up lightdm will not start, press Ctrl+Alt-F1 and login as root then edit the xorg.conf file and restart X with 
  restart lightdm

---

