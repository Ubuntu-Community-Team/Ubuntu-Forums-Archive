---
title: "how do i increase resolution when using lcd tv"
date: 2009-10-27
forum: Desktop Environments
---

### Post by Gnome181 on 2009-10-27
i have upgraded from windoze to ubuntu 9.04 and am trying to using this as a multimedia unit with my sanyo lcd tv. the highest resolution i am offered is 720x400, due to the tv being an unknown device. how do i force the resolution higher? do i need to run a separate program?

i am very new to ubuntu so please be patient and give detailed instructions.

thank you.

---

### Post by Gnome181 on 2009-10-29
Problem solved. I did some research on the net and found some one who had to edit his xorg.conf to get higher resolution with a new graphics card. He had added an extra mode, so I tried this:

Section "Screen"
Identifier "DefaultScreen"
Monitor "ConfiguredMonitor"
SubSection "Display"
Mode "1024x768"
Virtual 1024 768
EndSubSection
EndSection

It worked.

---

