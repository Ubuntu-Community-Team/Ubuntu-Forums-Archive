---
title: "KDM theme manager not working (kubuntu gutsy)"
date: 2007-10-24
forum: Desktop Environments
---

### Post by keesercc on 2007-10-24
Hello and thanks for the help.

I upgraded from kubuntu feisty to gutsy (10/21/07).  The upgrade seemed to go fine (although I dont have compiz... but thats another problem) but the upgrade has changed my login screen to a (imo) very ugly login screen with an XP-esque user list.  I went to return my KDM Theme to its original style, but changing the theme in KDM manger has absolutely no effect.  Small problem I know, but annoying none the less.  Anyone know of a fix?

---

### Post by vonderer on 2007-10-25
Same problem here.

Is there any solution?

---

### Post by infinitezero on 2007-10-26
Just installed Gusty and KDM theme manager does not work. It will not except new themes or even apply the default themes that come with it. Does anyone have a work around for this?


Thanks,
iz

---

### Post by infinitezero on 2007-10-26
found the answer:
[https://bugs.launchpad.net/ubuntu/+source/kde-systemsettings/+bug/148706](https://bugs.launchpad.net/ubuntu/+source/kde-systemsettings/+bug/148706)

I went into the file /etc/kde3/kdm/kdmrc

Added the following line:
UseTheme=True

Then you need to change the following line:
Theme=@@@ToBeReplacedByDesktopBase@@@

For example I changed mine to:
Theme=/usr/share/apps/kdm/themes/true-nature

Save the changes then restart your system.

If KDM theme manager will not install a new theme you can add it manually. Untar it in the themes directory /usr/share/apps/kdm/themes/ and then change the line Theme=/usr/share/apps/kdm/themes/**true-nature** to the new theme folder name.

iz

---

### Post by keesercc on 2007-10-26
Ultimately thats exactly what I had to do to get my theme back.  However, I am disappointed that this feature no longer functions in kcontrol or the kubuntu settings manager.  Thanks for your input.

---

### Post by infinitezero on 2007-10-27
There are always some bumps in the road to success.

iz

---

### Post by oobuntoo on 2007-10-27
I think this has something to do with how Gutsy deals with profile/settings. Before Kubuntu Gutsy, settings that were applied to programs running as sudo/root are different from the one used by programs running as a normal user. In Gutsy, when you run an app as sudo/root, your normal user settings/profile are being applied to this app as well. This gives a consistent look and feel; icons, fonts, and color scheme are the same for both apps that run as root and normal users. I think they have introduced bugs when they tried to achieved this consistency.

---

### Post by prince_niceguy on 2008-02-25
It is pain to restart the computer to take the new theme into effect. shouldn't the kdm thing take it up directly when the change is done.

---

### Post by Whiffle on 2008-02-25
Shouldn't have to restart the computer, 

sudo /etc/init.d/kdm restart 

should do it, but save your work first as it will restart X and kill all the programs you ahve running.

---

### Post by prince_niceguy on 2008-02-25
yup.. never realised that could be done.

---

