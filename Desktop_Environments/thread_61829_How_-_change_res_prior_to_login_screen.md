---
title: "How - change res prior to login screen"
date: 2005-09-02
forum: Desktop Environments
---

### Post by Optiker on 2005-09-02
In another thread, I asked about my desktop being shifted right about a third of its width so that the right third was off-screen. I got that resolved by reducing the KDE res from 1600x1200 to 1280x1024 (I think that's what it is now).

However, it still opens the login screen at 1600x1200, so like previously, the right 1/3 is cut off. It's just annoying, not functionally a problem since the login is not cut off, but I'd like to fix it. It seems like it's after X...(whatever it's called) starts since the login screen is a GUI. Right? Wrong?

It seems obvious that someplace there is a line in a config file that sets that res. In Mandrake, there are neat GUI methods for that kind of stuff, but if there is in Kubuntu, I haven't found it. I am starting to be less nervous about editing config files, so am willing to do it that way if I know what line to edit in what file and where to find it.

I see in another post about res, a reference to xorg.conf. Is that the file where this is found, and if so, where do I find it? If not, what file and where?

Finally, is there a way to completely skip the login? I don't think I need to control access, so as in my Mandrake installations, I'd like to be able to boot into Kubuntu without manual login.

Thanks!
Optiker

---

### Post by incinerator on 2005-09-02
you will have to edit your /etc/X11/xorg.conf

In that file you will see something similiar to this
>  Section "Screen"
 Identifier "Default Screen"
 Device  "NVIDIA Corporation NV43 [GeForce 6600 GT]"
 Monitor  "Standardbildschirm"
 DefaultDepth 24
 SubSection "Display"
  Depth  1
  Modes  "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  4
  Modes  "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  8
  Modes  "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  15
  Modes  "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  16
  Modes  "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
 SubSection "Display"
  Depth  24
  Modes  "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
 EndSubSection
EndSection 
Do you see these lines that start with **Modes**? The first mode in the line is the one used as default mode for that particular colour depth. Re-arrange as you see fit. Log out of kde, log into the console and do
sudo /etc/init.d/kdm restart

---

### Post by Optiker on 2005-09-06
incin....OK - that worked. At least, it is now flush with the left edge of the screen. The splash image looks to be much larger (1600 wide?) as it is cut off at the right through the word "kubuntu". Perhaps it is independently sized to 1600 x 1200? If so, is there a way to scale it to fit the mode?

Thanks!
Optiker

---

