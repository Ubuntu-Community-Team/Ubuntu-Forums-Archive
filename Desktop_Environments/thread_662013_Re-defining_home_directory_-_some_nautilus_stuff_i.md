---
title: "Re-defining home directory - some nautilus stuff is lost"
date: 2008-01-08
forum: Desktop Environments
---

### Post by Saubazi on 2008-01-08
I am using couple of different distros on my machine and for this reason I want to use different home directories for each distro (they are locate in same partition) - so for example for gentoo I have /home/user_gentoo and for gutsy I have /home/user_gutsy

I modified this stuff after the installation on /etc/passwd however, I have some small inconvenient things amiss. For example my when double clicking on trash bin nautilus opens /boot director.
Deleting files will move the files still correctly to /home/user_gutsy/.Trash 

Also I recall having under "Places" menu locations like Documents and Music and so on - but not so anymore.

Is there somewhere a gdm configuration somewhere where there would be additional definitions so that I could fix the probs?

---

### Post by Saubazi on 2008-01-14
Ok, in a file called .gtk-bookmarks there were some bits that needed adjustment and at least now my "Places" menu looks better. Deleted Items still point at /boot though !!$)=!$?=&!§"$!

---

