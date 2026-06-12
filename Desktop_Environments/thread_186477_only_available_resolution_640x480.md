---
title: "only available resolution 640x480?"
date: 2006-06-02
forum: Desktop Environments
---

### Post by boxubi on 2006-06-02
I was having an issue earlier where I could not get over 640x480 screen resolution.

I was using the DVI port on my video card and when I switched to the standard video port I fixed the problem. Now I can use all my monitor's resolutions.

This should help some other people who have been having the same problem.

One note: I was using an adapter to plug up to the DVI port because my monitor doesn't have a DVI connection.
](*,)

---

### Post by frodon on 2006-06-02
In most of the cases this problem come from the xorg configuration. Could your post there your xorg.conf file : ```
sudo gedit /etc/X11/xorg.conf
```Always backup this file before doing anything.
Then your will surely just need to add the **HorizSync** and **VertRefresh** parameters of your screen and restart Xserver (Ctrl+Alt+Backspace), the doc is there : [http://doc.gwos.org/index.php/ChangeResolution#How_to_edit_or_add_HorizSync_and_VertRefresh_lines](http://doc.gwos.org/index.php/ChangeResolution#How_to_edit_or_add_HorizSync_and_VertRefresh_lines)

---

