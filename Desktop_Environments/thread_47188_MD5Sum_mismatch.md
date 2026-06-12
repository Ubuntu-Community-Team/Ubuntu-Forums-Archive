---
title: "MD5Sum mismatch"
date: 2005-07-07
forum: Desktop Environments
---

### Post by adamb10 on 2005-07-07
> 
root@ubuntu:/home/adam # apt-get dist-upgrade --fix-missing
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  firefox firefox-gnome-support libcairo1
The following packages will be upgraded:
  mozilla-firefox mozilla-firefox-gnome-support
2 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 121kB/8829kB of archives.
After unpacking 676kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  firefox-gnome-support mozilla-firefox-gnome-support mozilla-firefox firefox
Install these packages without verification [y/N]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main libcairo1 0.3.0-1 [121kB]
Fetched 121kB in 0s (180kB/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb)  MD5Sum mismatch


I tried apt-get update but that didn't work.

---

### Post by MikeyXX on 2005-07-07
[QUOTE=adamb10]I tried apt-get update but that didn't work.[/QUOTE]
 Damn, I didn't see your post when I posted the same!

---

### Post by torena on 2005-07-07
This has been the bane of my existence since last night.  I've been trying to install evolution and then I wanted to install firefox, and I'm hanging at [http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomecanvas/libgnomecanvas2-0_2.10.0-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libg/libgnomecanvas/libgnomecanvas2-0_2.10.0-0ubuntu1_i386.deb) and last night I was hanging on something else while trying to install gaim.  Just as I was finding another source for the file, the error went away.  This time, however, it is not.  ](*,)

---

### Post by torena on 2005-07-07
[http://de2.vlsm.org/dists/stable/de2ui/binary-i386/](http://de2.vlsm.org/dists/stable/de2ui/binary-i386/)

Okay, here's what I did.  Might be a little complicated but try it anyway.  :)  Copy and paste that missing package into a google search.  Find a site that has that file, and download it.  Open up a konsole window and locate the file.  Then, dpkg -i <filename>.

Now, that *should* work.  However, you might get an error about dependencies and it'll tell you to 'apt-get -f install' to fix.  I did that, and it fixed my dependencies.  Then I was able to apt-get install evolution and mozilla-firefox. 

Hope this helps.

---

### Post by Strider on 2005-07-08
Found the solution in another thread:

[http://ubuntuforums.org/showthread.php?t=47203&highlight=md5sum+mismatch](http://ubuntuforums.org/showthread.php?t=47203&highlight=md5sum+mismatch)

Tried the solution posted and it works.

Good luck!

-S

---

