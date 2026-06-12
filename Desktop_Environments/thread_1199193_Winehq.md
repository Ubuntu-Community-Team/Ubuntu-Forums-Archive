---
title: "Winehq"
date: 2009-06-28
forum: Desktop Environments
---

### Post by SNOOPY817 on 2009-06-28
okay well i installed winehq and all but theres something wrong i cant see the letters.... check it out


[IMG]http://i42.tinypic.com/2uoo2vs.png[/IMG]

anyone know what the problem is?
do i need to install something else or do 
i have something missing idk plz helkp

---

### Post by dunkar70 on 2009-06-28
Did you install from a .deb file or from source? I would start by checking that you have the dependencies, including the MS true type fonts. I prefer to install from the repositories as outlined below. The first line will add the key to your ring. The second line will create a new file with the winehq repository. The last two lines will install the latest version of wine. Each time you update your system, wine will be updated with it.

> wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -
sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list](http://wine.budgetdedicated.com/apt/sources.list.d/jaunty.list) -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get install cabextract msttcorefonts wine

---

### Post by SNOOPY817 on 2009-06-28
all of them worked except the third one i got this error

>  sudo wget [http://wine.budgetdedicated.com/apt/....d/jaunty.list](http://wine.budgetdedicated.com/apt/....d/jaunty.list) -O /etc/apt/sources.list.d/winehq.list
--2009-06-28 19:09:57--  [http://wine.budgetdedicated.com/apt/....d/jaunty.list](http://wine.budgetdedicated.com/apt/....d/jaunty.list)
Resolving wine.budgetdedicated.com... 81.171.111.184
Connecting to wine.budgetdedicated.com|81.171.111.184|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2009-06-28 19:09:57 ERROR 404: Not Found.


---

### Post by flugh on 2009-06-28
Did you put exactly this?
sudo wget _[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)**[COLOR="Blue"]/....d/[/COLOR]**jaunty.lis_t -O /etc/apt/sources.list.d/winehq.list

It should be:
sudo wget _[http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt)**[COLOR="Blue"]/sources.list.d/[/COLOR]**jaunty.list_ -O /etc/apt/sources.list.d/winehq.list

I just tested the full URL there and it works fine. The "..." stuff is just the poster's system doing some 'helpful' formating (a 'feature' that I don't personally care for because of this exact situation).

---

### Post by flugh on 2009-06-28
Also, I have used the packages from that repository myself, and had no problems. My guess would be a font problem. Check your X startup log and see if there's a bunch of FontPath errors, maybe the fonts aren't readable (permission problem)? Something along those lines.

---

### Post by SNOOPY817 on 2009-06-29
well i put the code in it worked, but still the fonts dont work
or the color w.e idk what the problem is /=

---

### Post by dunkar70 on 2009-06-29
Sorry about the ellipse... I guess I didn't proof read closely enough. 

Based on your intial post, it apears you have just installed Wine and do not have any applications installed yet. If this is the case, try removing the ~/.wine directory then log out. When you log back into the GUI, it will create a new directory with the default configuration.

---

### Post by SNOOPY817 on 2009-07-01
oh okay wheres the ~./wine?

---

### Post by dunkar70 on 2009-07-02
Open a terminal and type this:
> cd ~
rm -R .wine

The ~ represents your home folder and will usually be /home/yourUserName.

---

### Post by SNOOPY817 on 2009-07-04
Okay, well i did it but i still got the same problem /=

---

### Post by txcrackers on 2009-07-04
Try installing msftcorefonts... ;)

---

### Post by SNOOPY817 on 2009-07-04
Eh, how do i do that? xD

---

### Post by dunkar70 on 2009-07-04
try...

> sudo apt-get install msttcorefonts cabextract

---

### Post by SNOOPY817 on 2009-07-04
damn,,, didn't work either, i think i should just unistall is and reinstall it back, what do you think? The thing is idk how to unistall it :confused: so if you can tell me how. i would
REALLY REALLY APPRECIATE IT

---

