---
title: "Installation Size and File Management"
date: 2009-03-20
forum: General Help
---

### Post by bigbencg on 2009-03-20
I am using a 4GB ramdrive to run kubuntu, as this drive is small I need to conserve every bit space that I can.  Initially the installation was 2.6GB, leaving 1.5GB free.  I browsed adept and removed some packages I did not need, accessibility stuff, bluetooth, and some other applications.  This freed 100MB, leaving me 1.6GB free space.  I let the system update, 301MB of updates were downloaded and installed which left me with 600MB free.  I used the apt-get autoremove command to clean up what I am assuming are the downloaded packages.  Which gave me 1.1GB of free space.  I manually deleted the files in / initrd.img.old and vmlinuz.old.  

What does the autoremove actually do, and when a file is upgraded does it create an .old version of the original file.  I did search for files with .old which only returned 9 files.  I worry that as updates are released my drive space will slowly diminish.  

After installing Nvidia drivers and customizing my installations to my needs, I currently have 993MB free.  I would like to at least maintain that value.

Also, what is the file kroot?

---

### Post by kanikilu on 2009-03-20
```
sudo apt-get clean
``` will remove downloaded packages. Autoremove just removes packages that are no longer used. Check out the apt-get man page for full descriptions of all the options.

---

### Post by bigbencg on 2009-03-20
Score!  Another 13MB reclaimed!  Actually I made a mistake in my original post, it wasn't autoremove it was autoclean.  I initially tried the clean command which prompted me to use autoclean.  But this did help, as I have made package changes since the original command.

Thank you kanikiklu!

---

### Post by kanikilu on 2009-03-20
No problem, I'm in the same situation with my netbook (ASUS 4GB), so have to keep a tab on my disk usage.

Check out this guide for more tips if you want to try to reclaim even more space:

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

...some of the steps require installing a new package or two, which seems counter-intuitive at first, but I think it helps in the end...

---

### Post by bigbencg on 2009-03-20
That was a good article and found it's way into my bookmarks!

---

### Post by oldos2er on 2009-03-20
Install and run localepurge.

---

### Post by bigbencg on 2009-03-20
I did that as well, per the article kanikilu posted a link for.  That scored me 0.1MB!  Thanks for the reply

---

