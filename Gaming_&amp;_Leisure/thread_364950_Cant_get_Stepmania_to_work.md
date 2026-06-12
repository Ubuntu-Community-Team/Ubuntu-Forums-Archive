---
title: "Cant get Stepmania to work"
date: 2007-02-18
forum: Gaming &amp; Leisure
---

### Post by Zyren on 2007-02-18
I downloaded the Binary to Stepmania and cant get it to work. After the songs hash the game tries to load and then it just crashes and goes back to desktop in a split second.I also tried to ./configure && make from source, and then did "sudo make install" and im pretty sure it worked. I get a Stepmania file in usr/local/bin but its just one file and when i open it in terminal i get this:

//////////////////////////////////////////////////////
Exception: Couldn't find "Songs"
//////////////////////////////////////////////////////

Error: Couldn't find "Songs"

Im very new to linux (only been using ubuntu 6.06 a week) and any help or detailed explanations would be very appreciated.

---

### Post by Zyren on 2007-02-19
ok, when i tried running the binary through the terminal i got this error:

Error: There was an error while initializing your video card.

   PLEASE DO NOT FILE THIS ERROR AS A BUG!

Video Driver: OpenGL

Initializing OpenGL...
Your system is reporting that direct rendering is not available.  Please obtain an updated driver from your video card manufacturer.


how do i enable direct rendering on my 3d card? i have an nvidia geforce 6800 and i am amost positive i have the latest drivers since i only updated them a few days ago.

---

### Post by EdThaSlayer on 2007-02-19
Check if you have direct rendering enabled by typing "glxinfo", I use an ATI and it tells me if direct rendering is enabled.

---

### Post by Zyren on 2007-02-19
I found out that my direct rendering is turned "off" because of XGL. How do i create a session in login that starts gnome without XGL?

---

