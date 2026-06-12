---
title: "Lost my applications icon and menu"
date: 2009-08-05
forum: Desktop Environments
---

### Post by wpsmithii on 2009-08-05
I'm setting up my mother with Xubuntu 6.06 lts and I tried to do an automatic  install of hplip-3.9.6b which was needed to run her new HP Officejet 6310 all-in-one. When I ran the script and rebooted. The applications menu and icon were gone. Everything else seems to work fine except for that. The blue ball for Firefox just moved over, further to the left. The only thing I noticed during install was that "Python dbas" was not installed and now the boot up notice says HP imaging and scanning failed. I'm in Tucson AZ trying to do this. Any help would be appreciated. Thanks in advance Bill Smith

---

### Post by doas777 on 2009-08-05
I would start by trying to remove the hp app.

if your going to put more than a couple hours into this, you might want to consider reinstalling and upgrading to 8.04 or even jaunty. 6.06 is pretty dated at this point.

---

### Post by wpsmithii on 2009-08-06
I'm working with very limited computer resources, ie AMD 1100 and 384 megs of ram. Thats why I chose the OS. The OS and Firefox actually runs faster than my quad core at home. How do I remove the app? The downloaded file and compiled app reside on the desktop. I can delete them but will that do it? I'm new at this.

---

### Post by appier on 2009-08-06
Personally, for your particular configuration, I would recommend Xubuntu Hardy 8.04 -- stable as a rock and light on the resources.

---

### Post by wpsmithii on 2009-08-07
OK, I upgraded to Jaunty, and took care of the original problem, but the second hard drive didn't get formatted. The OS sees it as "lost and found" with no access at all? Also I'm supposed to run "hp-setup" to configure the printer. When I enter that command in a Terminal window, it says that its supposed to run in a graphical environment. I would assume CUPS, how do I access that? Thanks Bill

---

### Post by doas777 on 2009-08-07
what are the permissions and owner on your drives? you can find out with 'ls -l'. 

as for your hp command; is it a script or an executable? if it's an executable, just hit alt + F2 and enter 
```
gksu hp_setup
```
if it's a script, open a terminal, navigate to the script directory, and enter:
```
gksu ./hp_setup
```

---

### Post by wpsmithii on 2009-08-07
OK, I got the printer fixed, I had to download an app from HP that loads an icon in the upper right corner between the network icon and the mixer icon, and thru that I can access all the features. It's called HPLIP in the add/remove list. Now, the drive, I typed: 'ls-l', ls-l, 1s-1, '1s-1' then sudo and all 4 again and I got command not found for all 8 of them? I'm logged on as the root, mom, and there are no other users. The "lost and found" folder ,which appears to be the drive in question, in the file system, has a big X on it like the root folder does. "Mom" has superuser rights and permissions. Thanks again Bill I have pulled the hd in question for another  use.

---

