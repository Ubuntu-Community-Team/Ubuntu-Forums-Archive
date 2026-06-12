---
title: "tvtime - no /dev/video0"
date: 2005-03-24
forum: Desktop Environments
---

### Post by rotorwash on 2005-03-24
I have an ATI AIW 9800 and installed tvtime from the ubuntu distribution to watch tv. When I start tvtime is says that there is no /dev/video0. I ran MAKEDEV video and it exits but there is still no /dev/video link. Can someone give me some pointers on how to troubleshoot this?

---

### Post by emperor on 2005-03-24
The AIW interface is NOT v4l compatible (tvtime only supports v4l cards) and thus requires another driver. ATI does not support the video interface under Linux but the Gatos project does. Gatos are in the process of trying to merging their code into xorg, but they are lagging behind a bit. 

The bad news is that Gatos does not release binaries very often and you have to build the driver yourself from CVS code. In order to do this you have to have the whole Xorg tree installed as well. 

Here's the link to the project on sourceforge:
[http://sourceforge.net/projects/gatos/]("http://sourceforge.net/projects/gatos/")

Their "latest" binary is for Xorg 6.7 :cry:

Also see: [http://gatos.sourceforge.net/ati.2.php]("http://gatos.sourceforge.net/ati.2.php")

I was a steady AIW user for years, but when I installed FC2, I got tired of waiting for Gatos to support Xorg and got rid of my AIW. I swore at the time that I would never buy another one. So, I replaced my AIW7500 with a Generic 9600PRO and an Asus TV card that cost about $40. The Asus tvcard has a saa7133 chipset and is fully v4linux compatible via the saa7134 driver which is shipped with every kernel release. So the tv support just works, even with live linux Distros.

---

### Post by Pablo928 on 2005-03-24
My tvtime program starts fine in terminal,but I get an error message that it can't retrieve station list----will create one---access denied. I/O error. Can anyone tell a new Ubuntu (and Linux) user how to create a station list?

---

### Post by rotorwash on 2005-03-25
Thanks, Emperor. Unfortunately, I cannot change cards... no room in the SFF box. I've heard that folks can get it to run since it can use the bttv drivers but I haven't found any specifics on how they did it yet. I am running xfree86 and using the proprietary ATI drivers if that matters. Guess I will have to study v4l when I get time. I was hoping the software was plug and play.

---

### Post by emperor on 2005-03-25
If you are running Warty and using xfree86, you can you the Gatos ati4.3 binaries. Installation is simple too. Just don't upgrade to Hoary until  Gatos gets an Xorg 6.8 driver out  of cvs. The info on the Gatos 4.3 binaries is in the link I gave you last night.

---

### Post by rotorwash on 2005-03-26
Thanks, I will give it a try and report back.

---

