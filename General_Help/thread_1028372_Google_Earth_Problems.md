---
title: "Google Earth Problems"
date: 2009-01-02
forum: General Help
---

### Post by NoBugs! on 2009-01-02
On the latest Ubuntu 8.10, with the latest Google Earth 4.3, the program will only work when desktop effects are disabled, and the program is run as root (sudo). If it is run normally, without sudo, it will only show background stars.
Even when it does work, the letters disappear. Depending on what font I set, different letters become invisible. For example, the bottom text will say
"Im g   NASA
 urop  T chnologi s"

and the numbers at the bottom don't show up, except for 9's and sometimes 8's.

---

### Post by ithanium on 2009-01-02
sounds weird, my installation worked perfect. Try reinstalling the software :|

---

### Post by paris_alex on 2009-01-02
i got it working perfectly too. However, i noticed that when installed on a computer without a 3D card (i.e. NVIDIA), it will cause flickering problems when there's image overlays... which...i'm thinking is unavoidable...

how did u install it? i suggest using the medibuntu or google's repository to install via apt-get, so that you'll get it right for sure.

Good Luck! ;-)

---

### Post by NoBugs! on 2009-01-18
I got it from here:
[http://earth.google.com/](http://earth.google.com/)

What would be the correct way to uninstall it, and install it correctly?

---

### Post by oldos2er on 2009-01-18
Assuming you installed GE to /opt/google-earth, run the script /opt/google-earth/uninstall:

sudo /opt/google-earth/uninstall

 Then you can either reinstall GE from Medibuntu, or manually by running 

sudo ./GoogleEarthLinux.bin

 from the file downloaded from earth.google.com. If you do it manually, once the installer is finished and asks if you want to quit or run GE, choose quit.

---

### Post by superoptimo on 2009-01-19
Hi.

I have the same issue with Google Earth.

I did reinstall it with the command "sudo ./GoogleEarthLinux.bin" and the problem persist.


Solution: Edit the Gnome menu, and change the properties of the "Google Earth" entry : change the command attribute from "googleearth" to "gksudo googleearth".

No more problems since then, except that I have to enter a password each time that I want to see the earth.

---

### Post by Roasted on 2009-01-19
It's in the repos. Search in Synaptic for it. I haven't had any problems with Google Earth on both new and old machines with a mixed bundle of hardware, however each time I installed it through Synaptic. In the repos is 4.3 and 4.2. If you try 4.3 and have problems, you could try kicking it back to 4.2 and see if that runs more stable for you.

I always check Synaptic first for any software I may want or need. If I can't find it, I'll search for a .deb then.

Note - I would advise you do a full blown uninstall of it before attempting to install it again.

---

### Post by danwood76 on 2009-01-19
I used to have this problem with the old ATI proprietary drivers.

What card do you have and what drivers are you using?

---

### Post by NoBugs! on 2009-01-19
I uninstalled and switched to using medibuntu packages, now it opens and crashes. And, it looks like it didn't fix the missing letters.

---

