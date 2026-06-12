---
title: "Gnome-Commander &amp; Midnight Commander"
date: 2006-09-15
forum: Desktop Environments
---

### Post by freiubtheit on 2006-09-15
Has anyone installed the above-mentioned applicatoins?

---

### Post by moore.bryan on 2006-09-15
*gnome-commander is great visually and helpful as a two-pane.  i found midnight-commander sloppy.  a great VERY LOW CPU USAGE two-pane is xfe... it's frickin' fast.*

---

### Post by andiii on 2006-09-15
I liked it, but one bug scared me too much to use it...

When movin a folder and destination disk was full, the source folder still got removed, even if not sll files could fit on the destination..

---

### Post by moore.bryan on 2006-09-15
*i've never had the pleasure of that bug... did you report it?*

---

### Post by keithb on 2006-09-15
I have been using Midnight Commander for quite a while. I think that is has a good reputation as a file manager. I like it. It takes a little while to get used to it but it has some good features. I try to keep my files synchronised with an external usb drive. Midnight Commander has a command to compare the contents of folders. It will highlight the files that are newer.

---

### Post by andiii on 2006-09-16
> **moore.bryan said:**
> *i've never had the pleasure of that bug... did you report it?*

Yes I just did. Should have done it right away. 

Ok, I just found out that it's not as bad. The file that should have been moved just disappears from the display. Refreshing the view brings it back.

---

### Post by freiubtheit on 2006-09-18
Thanks for sharing.

Where can I download the binary or RPM?

---

### Post by moore.bryan on 2006-09-18
[I]for g-c or m-c?
g-c's in the repos, if it's not default installed.  try ```
gnome-commander
``` in term.  for m-c, i think you have to compile from source.  i think i have the wget coding right, if not just go the site, download it and run from there.
```
wget http://www.ibiblio.org/pub/Linux/utils/file/managers/mc/mc-4.6.1.tar.gz
tar xvzf mc-4.6.1.tar.gz
cd mc-4.6.1
./configure
make
sudo make install
```
[/I]

---

### Post by freiubtheit on 2006-09-19
Thanks for the pointer.

I have successfully download, compiled and installed mc-4.6.1.

However, no luck with the make command with Gnome-Commamder-1.2.0 downloaded. And the error message is as follows:

"make: *** No targets specified and no makefile found.  Stop."

Kindly enlighten.

---

### Post by moore.bryan on 2006-09-19
*freiu... g-c may already be installed; look through the menus or type gnome-commander into a terminal.  if it's not, i'm almost positive it's in the repos.  try ```
sudo aptitude install gnome-commander
```*

---

### Post by freiubtheit on 2006-09-30
With the recent system update, I can install gnome-commander using synaptic at ease.

Cheers!!

---

