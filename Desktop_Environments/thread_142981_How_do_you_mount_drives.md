---
title: "How do you mount drives??"
date: 2006-03-11
forum: Desktop Environments
---

### Post by MrDan on 2006-03-11
I broke my breezy install while playing with dapper.  now dapper runs great (kinda) but now breazy won't load and I can't get at my files from the breazy. on hda1.  I can find hda1 in the dev directory but can't seem to get at it.  I can get into breazy only at command prompt but can not startx.  I thought about simply copying "cp" the files from there to /dev/sdb (smart card reader) and then transfer over.  I am supremely inept with linux command line stuff.  How do I mount drives and copy to drives both command line and in dapper.   


Help!!!:cry:

---

### Post by taurus on 2006-03-11
Open a terminal and do

```

sudo mkdir /mnt/hda1 /mnt/memstick
sudo mount -t vfat /dev/sdb /mnt/memstick
sudo mount -t ext3 /dev/hda1 /mnt/hda1

```

---

### Post by MrDan on 2006-03-11
That worked great and I think I get the whole mdir in the mnt dir, then mount into said dir.\\:D/ 

Now this doesn't make theloss of breazy too bad.  but I still want to try to repair the damage to it.:-k

---

### Post by taurus on 2006-03-11
How did you "break" Breezy?  Did you try to upgrade it to Dapper?

---

### Post by MrDan on 2006-03-11
yep!  then when it tries to boot, it has a nuber of fails then I get the blue screen saying:

 "failed to start X server (your graphical interface). It is likely that it is not set up correctly."

Some of the lines in the log:

(EE) Failed to load module "kbd" (module does not exist, 0)
(EE) Failed to load module "mouse" (module does not exist, 0)
(EE) I810(0): No valid modes.
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

---

### Post by atoponce on 2006-03-11
From the terminal, try: ```
sudo dpkg-reconfigure xserver-xorg
``` to reconfigure your xorg installation.

---

### Post by MrDan on 2006-03-11
then it dumps me onto the login screen. and I can do stuff in the command line.  I tried to do 
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver.xorg
(went through the reconfigureing )
sudo /etc/init.d/gdm restart

to no avail

---

### Post by taurus on 2006-03-11
Not sure whether it's a typo but it should have been
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by MrDan on 2006-03-11
[QUOTE=taurus]Not sure whether it's a typo but it should have been
```

sudo dpkg-reconfigure xserver-xorg

```[/QUOTE]
yah, sorry.#-o typo

---

### Post by MrDan on 2006-03-11
I guess now that I have my files, It isn't that big of a deal anymore.  I do kinda like the new dapper.  I think I'll keep it till it bites me in the butt.  (althogh the stable version will be nice):grin:

---

### Post by taurus on 2006-03-11
Dapper will officially be out on April 20th!!!

---

### Post by atoponce on 2006-03-12
[quote=taurus]Dapper will officially be out on April 20th!!![/quote] Isn't it going to be delayed for 6 weeks?

---

### Post by taurus on 2006-03-12
[QUOTE=atoponce]Isn't it going to be delayed for 6 weeks?[/QUOTE]
Well, it still says April 2006, according to this link!!!
[http://www.ubuntu.com/ubuntu/releases](http://www.ubuntu.com/ubuntu/releases)

---

