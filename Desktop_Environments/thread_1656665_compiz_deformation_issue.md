---
title: "compiz deformation issue??"
date: 2010-12-31
forum: Desktop Environments
---

### Post by gmenfan83 on 2010-12-31
ok i have searched and seen this thread numerous times /watched you tube videos on it and still cant figure this out ....first my deformation /sphere settings to be specific would not take place ...so i searched and enabled wallpapers and found a methoud using g-conf editor as well......and for some reason my cube by default was actually the cylinder and using the gconf method by tick enable desktop actually properly turns it into a cube but i still cant change to sphere???

update:i have looked in the faq section and ran the check-compiz script and this is the output...it says my graphics chip is blacklisted and im not sure whether or not to select yes and proceed?



update 2:i have just read about the blacklist and if i proceed it may cause media and video playback issues.....would it really cause many problems???

Gathering information about your system...

 Distribution:          Ubuntu 10.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [WARN]

Something potential problematic has been detected with your setup:
 Warning: PCI ID 8086:2a02 detected. 

Would you like to know more? (Y/n) Y

 Your particular graphics chip may be blacklisted on certain distributions.
 However that does not necessarily mean you will not be able to run Compiz.

 You can skip this blacklist -- but keep in mind that you did so.
 Do not complain if you encounter any problems with Compiz afterwards. 

Do you want to skip blacklist checks by Compiz? (y/N)

---

### Post by Frogs Hair on 2010-12-31
Go to cube reflection deformation setting and click on the setting icon. When the settings open select the deformation tab . From the drop down menu you can choose cylinder or sphere .

I use the cube mainly for a workspace switcher , so I am no expert when it comes fine tuning the cube settings. I don't know anything about blacklisting and have no recommendations.

There is a ppa for Compiz plugins that are not included in the with the plugins-extra and accounts for some of the effects you see in videos . Nixie Pixel mentions  them in her cube videos.

---

### Post by Frogs Hair on 2010-12-31
Load 3 times

---

### Post by Frogs Hair on 2010-12-31
Load 3 times

---

### Post by gmenfan83 on 2010-12-31
> **Frogs Hair said:**
> Load 3 times
whats load 3 times?
also i have done the sphere /settings you suggested to no avail ...i also tried to add nixies script for the unsupported add ons in her video and it wont install

---

### Post by Frogs Hair on 2010-12-31
> **gmenfan83 said:**
> whats load 3 times?
also i have done the sphere /settings you suggested to no avail ...i also tried to add nixies script for the unsupported add ons in her video and it wont install

My post appeared three times after I submitted it resulting in a triple post . The add on  script must be out dated. I will look for the current ppa. The black list issue may be causing the problem. If you choose to continue make backups.

---

### Post by Frogs Hair on 2010-12-31
Compiz experimental plugins. [http://www.webupd8.org/2010/11/install-compiz-experimental-plugins-in.html](http://www.webupd8.org/2010/11/install-compiz-experimental-plugins-in.html)

---

### Post by gmenfan83 on 2010-12-31
> **Frogs Hair said:**
> Compiz experimental plugins. [http://www.webupd8.org/2010/11/install-compiz-experimental-plugins-in.html](http://www.webupd8.org/2010/11/install-compiz-experimental-plugins-in.html)
thanks i installed the plugin but i am not going to use them until i see if i should proceed through the blaclist since most of the extra animations wont work while my card is blacklisted i believe

---

