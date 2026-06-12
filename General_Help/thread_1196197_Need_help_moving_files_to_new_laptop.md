---
title: "Need help moving files to new laptop"
date: 2009-06-24
forum: General Help
---

### Post by dellsguy67 on 2009-06-24
I am an SNES goober and i have several games in progress on my current laptop. I am getting a different one soon and i want to transfer my saved game data to the new one to play

how do i do this so when i load zsnes on the new laptop, i can load a game and have it be where i left off last time?

thanks

---

### Post by s3MA00RRNY on 2009-06-24
To backup a Ubuntu system, go to System > Administration > Synaptic > File > Save Markings. Save the markings to your home folder. Also save /etc/apt/sources.list to your home folder. Back up the ENTIRE /home directory (make sure you have root privs). If all your apps were installed from repositories, you are done. If they were not, make sure you have your debs. EVERYTHING is saved in your home folder because it is the only place on the system owned by you, so once you've backed that up, you're done. Once you get to the new computer, drop in the old /home, sources.list, and read markings in Synaptic. Click apply and it will reinstall all your software.

---

### Post by s3MA00RRNY on 2009-06-24
From what I remember ZSNES saves the states in the directory with the ROM.

---

