---
title: "This is my firts linux, and it doesn't work !!"
date: 2005-10-13
forum: Desktop Environments
---

### Post by dnshare on 2005-10-13
Hi Comiunnty:


I've decide to get mysel into the UNIX world, mots of people told me that the best distribition to start is UBuntu, so I Installed this distribution. all installation proces were good, no failures o something wrong, but.... when I start my sistem just en the moment when Ubuntu shows the login screen the system fails, it looks like a Video fail because the screen looks currup with some lines or sometimes the screen only displays de background. 
I'm workin with 5.04 version of Ubuntu, I install "linux" mode I mean desktop, I already Reinstall Ubuntu and the problem didn't solve. my video card is an Nvidia Geforce 4 MX 64MB ram DDR AGP 8X, Ive installed the grub and the other OS is win xp pro SP2. As I said this is my firts linux, I hope you can help me I really want to start with Ubuntu, If you need more information please let me know, Greetrings from Mexico !!!

---

### Post by Fade on 2005-10-13
Try moving your curser around the outer edges of the screen to see if it helps straighten things up. I've noticed some of my downloaded login themes are a bit screwy in this respect. With any luck, you will be able to login at least and then surge forward in the linux world. Of course, others with more experince may wish to offer up some help.

Cheers & Good Luck!

---

### Post by karuptdata on 2005-10-13
Have you configured your Nvidia drivers??If not go to this How To and itll walk you through it! [http://ubuntuforums.org/showthread.php?t=75074&highlight=Nvidia]("http://ubuntuforums.org/showthread.php?t=75074&highlight=Nvidia")

---

### Post by drewbie on 2005-10-13
just a thought,
but since you have an nvidia graphics card you may be needing nvidia-glx

once you have installed and at the login prompt where it all fails,
use the combination control-alt-F1 to drop to the command line,
login,
and type 

sudo apt-get install nvidia-glx

(and enter your password)
after that  type

startx 

to restart the graphical login, hopefully this should work, unless anyone else has any better advise and actually knows what the specific problem is.

---

### Post by jeffreyvergara.NET on 2005-10-13
why not try the new release of Ubuntu? Breezy Badger 5.10

---

