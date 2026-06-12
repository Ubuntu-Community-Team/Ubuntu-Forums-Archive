---
title: "Starting compiz makes system unusable"
date: 2010-05-29
forum: Desktop Environments
---

### Post by elizium23 on 2010-05-29
> rearl@aten:~/src$ sh compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 10.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation C73 [GeForce 7150 / nForce 630i] (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


I am using the "current" nVidia hardware driver.

When I start compiz (either manually or by enabling Desktop Effects) several undesirable things happen. My terminal windows resize themselves to about 56x15. Then the screen "wipes" from top to bottom with a totally black screen. The screen quickly becomes visible again, but all visual updates are incredibly slow and accompanied by the black "wipe" within the window (for example, I was watching a DVD and could see about 4 frames per minute.)

This doesn't happen every time. Testing it now I was able to enable compiz. It may or may not have something to do with Emerald. I would prefer to run Emerald but I am having another issue that may force me to revert.

---

### Post by WinRiddance on 2010-05-29
Emerald and Compiz together might just be too much for your setup? If you have 3D working at all be happy. Anything beyond "standard" 3D is an extra. Have you tried looking for updated hardware drivers?
start ----> system ----> administration ----> hardware drivers?

Keep in mind that compiz and emerald are definitely extras with which you can push your systems graphic capabilities to its limit, just like with any hardcore 3D game engine.

---

### Post by elizium23 on 2010-05-29
Reverting to version 173 of the nvidia hardware driver seems to have fixed the problem.

---

