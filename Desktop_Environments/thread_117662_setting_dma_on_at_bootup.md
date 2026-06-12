---
title: "setting dma on at bootup"
date: 2006-01-15
forum: Desktop Environments
---

### Post by robkenbat on 2006-01-15
Sorted turning dma on for video, but have to run the dma command line in terminal every time I boot up, if I want to watch video.
have tried to set it at bootup through hdparn.conf script,  "sudo gedit /etc/hdparm.conf  /dev/hdc { dma = on } "but no joy.  Am I missing something?

---

### Post by Perfect Storm on 2006-01-15
Read this, scroll down to troubleshooting and see if it helps: [http://doc.gwos.org/index.php/DMA](http://doc.gwos.org/index.php/DMA)

---

### Post by ptmurphy on 2006-01-15
[QUOTE=robkenbat]Sorted turning dma on for video, but have to run the dma command line in terminal every time I boot up, if I want to watch video.
have tried to set it at bootup through hdparn.conf script,  "sudo gedit /etc/hdparm.conf  /dev/hdc { dma = on } "but no joy.  Am I missing something?[/QUOTE]

This is what I put into my hdparm.conf file to get both my optical drives to have DMA enabled.

/dev/hdc {
	dma = on
}

/dev/hdd {
	dma = on
}

---

