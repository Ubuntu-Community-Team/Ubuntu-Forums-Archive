---
title: "Desktop inaccessible and can't mount drive"
date: 2009-11-23
forum: Desktop Environments
---

### Post by amalgamis on 2009-11-23
After booting up, my desktop shows the appropriate folders and files on it. Hovering the mouse over them gives the slightest visual cue that they're clickable, except nothing is. A first click (right or left) on any file, folder, or the desktop freezes the entire desktop. I'm still able to access all functionality from the OS toolbar, but as these windows open over desktop icons the icons disappear. 

Places->Desktop won't load, and when I try to mount my DATA partition I get the prompt for the password, and then nothing happens. Attempts at this temporarily shows the 'Opening _DATA' icon in the toolbar, but then it vanishes. 

Finally, when rebooting or shutting down I get a prompt indicating that the file manager is not responding (haha, really?). 

Any advice would be greatly appreciated.

UPDATE: I just discovered that I can access the files on the desktop (that are vanishing) using software (I just opened an .svg through inkscape). I have also run system updates, to no avail.

---

### Post by fancypiper on 2009-11-23
I would first try removing and re-installing nautilus:

sudo apt-get remove nautilus
sudo apt-get install nautilus

---

### Post by amalgamis on 2009-11-23
> **fancypiper said:**
> I would first try removing and re-installing nautilus:

sudo apt-get remove nautilus
sudo apt-get install nautilus

I tried this, and now the OS is just booting to terminal. I also tried running ```
sudo apt-get install ubuntu-desktop
``` and ```
sudo dpkg --configure -a
``` but keep getting the error 'unable to fetch some archives.'

---

### Post by amalgamis on 2009-11-23
top.

---

### Post by nitstorm on 2009-11-23
[http://ubuntuforums.org/showthread.php?t=1324475&page=2](http://ubuntuforums.org/showthread.php?t=1324475&page=2) 

i had a similar problem but my screen jus kept going black and ubuntu jus froze if i clicked something. it was a prob with compiz so uninstalled it completely, check out comment #15 that was the code i typed in to remove it completely

hope this helps

---

### Post by amalgamis on 2009-11-23
> **nitstorm said:**
> [http://ubuntuforums.org/showthread.php?t=1324475&page=2](http://ubuntuforums.org/showthread.php?t=1324475&page=2) 

i had a similar problem but my screen jus kept going black and ubuntu jus froze if i clicked something. it was a prob with compiz so uninstalled it completely, check out comment #15 that was the code i typed in to remove it completely

hope this helps

No dice... thanks for replying though. I'm finally able to get back to the desktop, but it's still unusable. If anything I just need to grab some files off of here and then I can reinstall the OS no problem.

---

### Post by BooSolo on 2010-01-30
I'm having a very similar issue, there was a double power outage in my neighbourhood a few days ago and after the second surge when my computer was started up again I couldn't open any of my folders. I click on the folder it starts up, says opening "home folder" for example, the little circle thing spins then it just stops. Nothing opens. 
I can get online no problem and all of the games and applications run but I have no access to any of the folders in Places, I'm very new to Ubuntu and don't understand most of the technical language in a lot of the forums that may be relevant to fixing this... Any help at all would be greatly appreciated

---

