---
title: "Removing LXDE/Lubuntu programs from Ubuntu?"
date: 2010-04-07
forum: Desktop Environments
---

### Post by happysadhu on 2010-04-07
Hi,
I installed the Lubuntu desktop on Ubuntu 10.04 to try it out, through the Synaptic Manager. I was able to login to Lubuntu, but now when I return to Ubuntu desktop I have all the Lubuntu programs duplicated in the Ubuntu menus. For example, now I have two "appearances" and two "screen savers" under the system > preferences menu in the Ubuntu Desktop.

I tried getting rid of these duplicates, by uninstalling Lubuntu, but they are still there?

How would I remove these etra LXDE/Lubuntu programs I no longer want? 

Thanks,
Sam

---

### Post by happysadhu on 2010-04-11
I was able to get rid of most of the LXDE programs by searching for "lxde" in the synaptic manager and removing the relevant programs. I then had to look through "applications" again and then find additional programs like "leafpad" and uninstall them as well through synaptic.

It would be much better if these programs would auto-uninstall when one removes lubuntu from their desktop or if there was a script that could be run.

Thanks,
Sam

---

### Post by fishkid257936 on 2010-07-26
Is there a better/quicker way to do this?

---

### Post by fishkid257936 on 2010-07-28
bump

---

### Post by JedMeister on 2010-08-08
I am not aware of a better way sorry :(

Perhaps you could have a look in /var/apt/cache for the lxde .deb metapackage, crack it open with some archive app and see what it installs.
Using that info you could uninstall them all a command like this:
```
apt-get --purge remove lxde lxde-common lxsession pcmanfm <and so on listing all packages>
```
You could then post it here for others! :)

---

