---
title: "I am new to linux and need help at installing a game (TA3D)"
date: 2008-06-16
forum: Gaming &amp; Leisure
---

### Post by dinbrca on 2008-06-16
I downloaded Total Annilation 3D from:
[http://ta3d.darkstars.co.uk/linuxdl-en.php](http://ta3d.darkstars.co.uk/linuxdl-en.php)
and i don't know what i need to do to install it..

---

### Post by cogadh on 2008-06-16
That's source code for the game, you need to compile it first. All you should need to do is install the required libraries and tools, then follow the instructions on that page to compile and install it...

Hmmm, unfortunately, it looks like you will also need to compile the Allegro library for it, since only 4.2 is available in the repositories and the game recommends 4.3. 

I don't usually like to do this, but if you are really new to Linux, you might not want to take this on right now. If you are looking for a challenge, by all means, this is a worthy project and I or one of the other people here would be more than willing to help you with it.

EDIT - I take some of that back (now that I've actually downloaded it). It looks like this has an installer, but it requires you to have an original TA cd. All you need to do to run it is extract the files from the tarball, make sure you have the cd in the drive, open a terminal and change directories to wherever you extracted the files, then run "sh install-sh".

---

### Post by Vadi on 2008-06-16
Try Spring RTS ([click]("http://spring.clan-sy.com/wiki/Ubuntu_install#Graphical_Interface")) instead. It's similar, and easier to setup.

---

### Post by dinbrca on 2008-06-17
ok so ta3d is actually an addon for ta the original? cause i uses the files of it? if yes the i have the original + its all addons..
what is tarball?

---

### Post by cogadh on 2008-06-17
"Tarball" is a Linux geek term for the .tar.bz2 compressed file you downloaded for the game. Its like a zip file in Windows.

Since I don't have the original game, I'm not sure what this is. All I know is when I downloaded, extracted and ran the installer from the TA3D website, it asked for the original CD and I could not proceed any further.

---

### Post by MaximB on 2008-06-17
> **Vadi said:**
> Try Spring RTS ([click]("http://spring.clan-sy.com/wiki/Ubuntu_install#Graphical_Interface")) instead. It's similar, and easier to setup.

I fully agree.
Try Spring as TA3D will demand the original files from the game CD.
Spring runs without those files.

Plus IMO Spring is more developed then TA3D and it has a much larger community and network game via lobbies.
And Spring has more mods and maps. (although I think you can also use them at TA3D, but I never tried).

---

