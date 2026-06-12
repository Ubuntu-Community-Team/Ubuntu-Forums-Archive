---
title: "No Screenshot at Lubuntu 13.04 with Acer Aspire 3610"
date: 2013-10-10
forum: Desktop Environments
---

### Post by AstroPhysik on 2013-10-10
Hello,

The "print" button from the keyboard is not working. It does not save screenshots to the RAM. So pasting the screenshot with strg+v into writer or gimp is not possible. 
How can i fix this?

Laptop: Acer Aspire 3610
Lubuntu 13.04, Kernel 3.8.0.-31-generic #46-Ubuntu i686 GNU Linux, with LXDE.
regards AP

---

### Post by vasa1 on 2013-10-10
Lubuntu is a "lightweight" distro and that implies that the software that comes with Lubuntu may not be as full-featured as one may expect.

In the case of "print" not saving to clipboard, that's because the program involved is "scrot", one of the lighter screen grabbers around. If you want to save to the clipboard, install "xfce4-screenshooter". That will do what you want.

---

### Post by Dennis N on 2013-10-10
Your Print Screen button probably is not broken; screenshots are being saved in the background, probably to your home folder. From there, just copy and paste into another application.

---

### Post by vasa1 on 2013-10-10
OP wants to "... save screenshots to the **RAM**."

---

### Post by Dennis N on 2013-10-10
> **vasa1 said:**
> OP wants to "... save screenshots to the **RAM**."

Hi Vasa1,

I understand that. I am just making clear that they are actually being done, since no dialog appears, and how to work around this.

---

### Post by walterorlin on 2013-10-10
Yes scrot saves to the disk by defualt.

---

### Post by vasa1 on 2013-10-10
The reason I mentioned "xfce4-screenshooter" is that you get the option to "save to clipboard" which is somewhat close to saving to "RAM" and xfce4-screenshooter is also relatively light.

Just to be clear, I'm quite content with scrot and have the following keyboard shortcuts in lubuntu-rc.xml:
```
Print = scrot -b -d 5 -q 33 ~/Desktop/%H-%M-%S.png
W-Print = scrot -u -b ~/Desktop/%H-%M-%S.png
Alt-Print = scrot -u -b -d 5 -q 33 ~/Desktop/%H-%M-%S.png

```
All the switches are explained in **man scrot**.

---

