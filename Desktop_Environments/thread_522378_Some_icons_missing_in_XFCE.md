---
title: "Some icons missing in XFCE"
date: 2007-08-10
forum: Desktop Environments
---

### Post by zamia on 2007-08-10
my xubuntu has some icons missing as the attachment shows, some menu or button also has this problem. I don't know how it happened? anyone could give me some advice? i'm a newbie in xubuntu.
btw, ignore the chinese in the screenshot :)

solved by:
apt-get install xfce* --reinstall

seems like it is because some package was not installed

---

### Post by merlinus on 2007-08-10
Are you allowing xfce to manage your desktop?

Applications/Settings/Desktop Manager

-merlin

---

### Post by zamia on 2007-08-10
yes~any idea?

---

### Post by tjmakin on 2007-09-12
I'm having the same problem, haven't been able to fix it. Running Ubuntu 7.04 install on which I've installed xubuntu-desktop and other XFCE goodies.

Here's a pic that shows the icons missing.

[http://img62.imageshack.us/my.php?image=screenshot1by6.png](http://img62.imageshack.us/my.php?image=screenshot1by6.png)


-

Have tried sudo apt-get install xubuntu-desktop --reinstall cause it was suggested in some other thread that I found. No success.


All help appreciated.

---

### Post by the yawner on 2007-09-12
Hi guys. Please check the following:

- Is there an icon for each of the program on your menu on the icon theme you're using?
- Is there a .desktop file for the program/s? Look in /usr/share/applications.
- If there is a .desktop file, open it with mousepad and look for the word *Icon*. The value should match the name of the icon on your icon theme. If it does not match, do not change the value on the file, just rename the icon to match that on the file. Or to be safe, create a copy of the icon on the same folder and rename the copy.

Please note that the .desktop file will appear with the corresponding icon if the icon names match.

---

### Post by tjmakin on 2007-09-12
> **the yawner said:**
> Hi guys. Please check the following:

- Is there an icon for each of the program on your menu on the icon theme you're using?
- Is there a .desktop file for the program/s? Look in /usr/share/applications.
- If there is a .desktop file, open it with mousepad and look for the word *Icon*. The value should match the name of the icon on your icon theme. If it does not match, do not change the value on the file, just rename the icon to match that on the file. Or to be safe, create a copy of the icon on the same folder and rename the copy.

Please note that the .desktop file will appear with the corresponding icon if the icon names match.

Ok, will try that after I get out of school. Will post results.

---

### Post by tjmakin on 2007-09-12
Ok, tried it, there were icons missing (at least I think so) .desktop files were all there but no icons anywhere. 

Anyways, I **solved** the problem by installing the newer XFCE 4.4.1 and it works good and all the icons are where they're supposed to be.

---

