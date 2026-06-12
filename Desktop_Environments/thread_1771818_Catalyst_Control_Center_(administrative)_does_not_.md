---
title: "Catalyst Control Center (administrative) does not open."
date: 2011-05-30
forum: Desktop Environments
---

### Post by [compactwelve] on 2011-05-30
Hello there!

I am currently using Xubuntu version 11.04 and I am working with a Radeon HD 4850 graphics card. I am using the proprietary FGLRX drivers from AMD.

I have a small problem. I have two monitors, and in order to tell the computer to use the extra monitor for extra desk space, I have to get into the Administrative CCC. However, when I click on the administrative CCC, nothing happens. It's strange considering that the regular CCC works just fine.

Any ideas?

thank you!

---

### Post by Toz on 2011-05-30
It looks like the desktop file to run the application is using a command that isn't working properly. To fix it, open up a terminal window and type in:```
sudo mousepad /usr/share/fglrx/amdccclesu.desktop
```

Change the line```
Exec=amdxdg-su -c amdcccle
```
to read:```
Exec=gksudo amdcccle
```and save the file.

I had to logout and back in for the change to take effect in the menus (not sure why though). But it should work for you then.

---

### Post by jcer93705 on 2012-05-24
> **Toz said:**
> It looks like the desktop file to run the application is using a command that isn't working properly. To fix it, open up a terminal window and type in:```
sudo mousepad /usr/share/fglrx/amdccclesu.desktop
```

Change the line```
Exec=amdxdg-su -c amdcccle
```
to read:```
Exec=gksudo amdcccle
```and save the file.

I had to logout and back in for the change to take effect in the menus (not sure why though). But it should work for you then.

This didn't work for me. My games in linux is running  great. I have installed is 12.4 and in Xubuntu 12.04. I did a full wipe and even before I could never open up catalyst control center administrator only the other one. Any ideas.

---

### Post by Toz on 2012-05-24
What didn't work? The original instructions were for 11.04, but they should work for 12.04 (I don't have an ati card anymore, but just had a look at the contents of the package) provided you installed fglrx-amdcccle from the ubuntu respositories (using the additional drivers application). 

How did you install the properietary drivers?

---

### Post by stooeygee on 2012-05-25
Here is what I did ( complete noob so bear with me!)

Right click on your Applications menu, click properties then edit menu.
Locate where the AMD Cat Control Center ( Administrative ) is, highlight it and click properties.
Type gksudo amdcccle in the command section,  then save it and close down your Applications Menu. Now try opening the amdcccle admin again and it should work.
This maybe a long way winded way of doing it but it worked for me!

---

### Post by Toz on 2012-05-25
Open a terminal window and execute the command there:
```
gksudo amdcccle
```
...and post back any error messages.

---

### Post by Bucky Ball on 2013-05-19
***Thread closed ...***

... as it is a year old and has been inactive for that long. Please post a new thread with any further issues.

Incidentally, post #5 worked perfectly for me. ;)

---

