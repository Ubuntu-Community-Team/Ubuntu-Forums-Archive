---
title: "How to update Cave Story to version 1.2"
date: 2013-05-13
forum: Gaming &amp; Leisure
---

### Post by A-DavRoyShi-X on 2013-05-13
I already know how to install the original version, but don't know what to do with the files of 1.2 update. It cannot be executed, opened as an archive, it's just unknown.


I've tried replacing the main executable and bin file, but that breaks the game. Searching online via Google didn't help either. Please help.

---

### Post by oldrocker99 on 2013-05-14
How did you get the game? If it was with the Humble Bundle, you may be able to download the game through the Ubuntu Software center; the Humble Bundle has allowed both Steam keys and Ubuntu Software Center for SOME games. If so, it adds a PPA repository for Cave Story, and it'll be updated like every other program through the Update Manager, Synaptic, or sudo apt-get install update && sudo apt-get upgrade.

---

### Post by A-DavRoyShi-X on 2013-05-14
From the official site: [http://www.cavestory.org/downloads_game.php](http://www.cavestory.org/downloads_game.php)
This link may help, but I don't understand the technical details: [https://aur.archlinux.org/packages/doukutsu/](https://aur.archlinux.org/packages/doukutsu/)
May try this version if nothing else works: [http://www.portablelinuxgames.org/?title=Cave+Story](http://www.portablelinuxgames.org/?title=Cave+Story)

---

### Post by A-DavRoyShi-X on 2013-05-15
I found the answer! Replace doukutsu.bin with doukutsu_32bits,** and** make it executable. It was MediaInfo that lead me to the right direction strangely enough (was just trying for the heck of it), it detected both files as the same container (ELF).

Only quirk is, the game displays the same version as the previous one (1.0.0.4), which is shared with the .run 1.2 version.

---

