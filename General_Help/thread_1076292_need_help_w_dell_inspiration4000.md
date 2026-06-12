---
title: "need help w dell inspiration4000"
date: 2009-02-21
forum: General Help
---

### Post by panda11 on 2009-02-21
i have an old dell inspiration 4000 (256ram). it ran ok with xp on it. i wanted to give it a go to ubuntu. i downloaded ubuntu 8.10,  burn the iso, and installed it on my dell. i have a problem with the video card. my screen is split in 3 and it is pretty horrible.  so here are my questions.

1. how can i fix the screen resolution
2. is ubuntu 8.10 appropriate for my dell or do i need a different version

thank you for the help

adrian

---

### Post by kestrel1 on 2009-02-21
You may need to enable the propriatary graphics driver.
Go to Sysstem -> Addministration -> Hardware Drivers & check to see if the driver need to be enabled.
Have you updated your system?

---

### Post by panda11 on 2009-02-21
nope. i just installed it last night. i have not updated my system. i can't even go to the system/administration. it is right at the overlap of the split screen and i have no idea how far down i need to go on that menu to get to the hardware and drives

---

### Post by kestrel1 on 2009-02-21
Can you open a terminal & try this command: ```
sudo dpkg-reconfigure xserver-xorg

```
If you are unable to open a terminal press CTRL, ALT & F1 together & type the command.

---

### Post by panda11 on 2009-02-21
did open the terminal and typed it in. i have a blue screen for package configuration

---

### Post by kestrel1 on 2009-02-21
You need to go through the steps to reconfigure xserver

---

### Post by panda11 on 2009-02-21
I downloaded and installed xubuntu. it works fain now. thank you. we can close this thread.

---

