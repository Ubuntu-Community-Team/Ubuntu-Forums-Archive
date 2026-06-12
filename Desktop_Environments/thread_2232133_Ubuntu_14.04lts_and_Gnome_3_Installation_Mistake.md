---
title: "Ubuntu 14.04lts and Gnome 3 Installation Mistake"
date: 2014-06-30
forum: Desktop Environments
---

### Post by nate15 on 2014-06-30
I ran both these commands, as suggested by another site, to try the gnome 3 look on my ubuntu machine.

My Specs (as far as ubuntu is aware) are:
Memory: 7.6 GiB
Intel® Core™ i5-3210M CPU @ 2.50GHz × 4 
Intel® Ivybridge Mobile 
64-bit

I ran this command in terminal:
sudo apt-get install gnome-shell ubuntu-gnome-desktop

It did work, but I was unsatisfied with gnome and wanted to go back to unity.
I then ran:
sudo apt-get remove gnome-shell - which apparently removed it and gnome-desktop; at least I can't remove either of them again (they dont exist). 

However, my machine is not at its previous state and is now lagging cosiderably, no longer has ubuntu 14.04lts on the top left, the boot manager (grub) has changed from purple to a pale blue-grey, I cant draw maquarees on the desktop, unity tweak tool doesnt work. It looks like normal unity, but the small animation on the left had icon bar are also gone.

Does anyone have any idea how I can remedy this? Furthermore, when logging in, there is no option to change to a different desktop environment (only one exists).

Thanks, I appreciate any help I can get. Let me know if you need more information about my system or anything else.

---

### Post by ajgreeny on 2014-06-30
As far as I'm aware gnome-shell and ubuntu-gnome-desktop are both just meta-packages and will have brought with them a lot of other packages, which will also need to be removed in order to get back to where you were before.

You can find all the info about the packages that were installed at the same time from the files in **/var/log/dpkg.log** and **/var/log/dpkg.log.1**
with command ```
grep -iw install /var/log/dpkg.log.1 && grep -iw install /var/log/dpkg.log
```then search for gnome-shell in the list (or use grep again on the output).

That will give you a date and time, and you will be able to see everything that was installed at the same date/time and then remove them.

You may also like to try the command ```
sudo apt-get -s autoremove
``` which will show you what would be removed  if you ran the command without the -s option, but will not actually remove anything, thus giving you a chance to look at the list before taking real action.

After all this you may want to re-install ubuntu-desktop package just in case anything has been removed inadvertently.

---

### Post by nate15 on 2014-06-30
> **ajgreeny said:**
> As far as I'm aware gnome-shell and ubuntu-gnome-desktop are both just meta-packages and will have brought with them a lot of other packages, which will also need to be removed in order to get back to where you were before.

You can find all the info about the packages that were installed at the same time from the files in **/var/log/dpkg.log** and **/var/log/dpkg.log.1**
with command ```
grep -iw install /var/log/dpkg.log.1 && grep -iw install /var/log/dpkg.log
```then search for gnome-shell in the list (or use grep again on the output).

That will give you a date and time, and you will be able to see everything that was installed at the same date/time and then remove them.

You may also like to try the command ```
sudo apt-get -s autoremove
``` which will show you what would be removed  if you ran the command without the -s option, but will not actually remove anything, thus giving you a chance to look at the list before taking real action.

After all this you may want to re-install ubuntu-desktop package just in case anything has been removed inadvertently.

Thanks, I wasn't aware that it would have installed multiple other packages. I guess this answers my question.

---

