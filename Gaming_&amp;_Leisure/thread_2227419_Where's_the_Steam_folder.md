---
title: "Where's the Steam folder?"
date: 2014-06-01
forum: Gaming &amp; Leisure
---

### Post by bug67 on 2014-06-01
I want to play Torchlight 2 on my Xubuntu 14.04 machine, however, it is not available for the native Steam Linux client.  So, I installed Wine 1.7 via PPA from WineHQ and used WineTricks to install the Steam client.  Torchlight 2 then downloaded, installed and launched perfectly!

Then, after having shut the game down and quitting Steam, I cannot find the Steam folder in either the program or program(x86) folders on Wine's virtual c-drive.  Any ideas?  I found a few threads but they all had to do with running Steam via PlayOnLinux and didn't seam to apply.

---

### Post by Mateusz Stachowski on 2014-06-02
First of all anything related to Wine should go to the appropriate section of the Ubuntu Forum which is [Wine]("http://ubuntuforums.org/forumdisplay.php?f=313").

If I remember correctly when you install Steam with winetricks it creates a new wineprefix in ~/.local/share/wineprefixes. That is a hidden folder in your home directory Ctrl+H in Nautilus will let you see the hidden files.

---

### Post by bug67 on 2014-06-02
Thanks.

---

