---
title: "amarok 1.3.7 wont update new albums automatically"
date: 2006-01-26
forum: Desktop Environments
---

### Post by pillypoon on 2006-01-26
I recently just switched from ubuntu to kubuntu with a fresh install. I had amarok working perfectly under ubuntu for a long time.  

So far Kubuntu has been awesome expect for a few little bugs i need to work out.  :KS 

I just installed Amarok 1.3.7 using adept and it seemed like it installed fine. The only problem I am having is that when I add new albums to my collection it wont automatically update itself like it should.. I have the scan folders recursively and watch folders for changes options checked.  in order for me to see the new albums i have to rescan my entire collection.  i have been using amarok for a long time with many different distros and this is the first time I have encountered this problem. 

if anybody has any ideas please let me know.  [-o< 


thanks in advance,
pilly

---

### Post by NeoChaosX on 2006-01-26
Try upgrading to [Amarok 1.3.8](http://kubuntu.org/announcements/amarok-1.3.8.php).

---

### Post by pillypoon on 2006-01-31
[QUOTE=NeoChaosX]Try upgrading to [Amarok 1.3.8](http://kubuntu.org/announcements/amarok-1.3.8.php).[/QUOTE]

I updated to 1.3.8 and it still doesnt update new albums.. I think it has somehthing to do with sqlite. I cant figure where to go from there. Any help would be apprecited.

thank again,
pilly

---

### Post by mlomker on 2006-01-31
[I have a guide]("http://www.ubuntuforums.org/showthread.php?t=80492") for installing the latest SVN if you want to give that a whirl.  I'd recommend hitting them up on their [IRC channel]("http://w5.cs.uni-sb.de/~gogo/homepage/amarok-stats/")--I've heard that they offer great support on there.

---

### Post by pillypoon on 2006-02-01
[QUOTE=mlomker][I have a guide]("http://www.ubuntuforums.org/showthread.php?t=80492") for installing the latest SVN if you want to give that a whirl.  I'd recommend hitting them up on their [IRC channel]("http://w5.cs.uni-sb.de/~gogo/homepage/amarok-stats/")--I've heard that they offer great support on there.[/QUOTE]


I followed your guide and got the following error as it was running the script:

grep: /lib/libattr.la: No such file or directory
/bin/sed: can't read /lib/libattr.la: No such file or directory
libtool: link: `/lib/libattr.la' is not a valid libtool archive
Error creating ./amarok/src/libamarok.la. Exit status 1.

ERROR: Compilation wasn't successful. amaroK was NOT installed/upgraded.

any ideas?

Thanks,
Pilly

EDIT:  i installed the libattr-dev package from synaptec and now it installs perfectly and my albums are updated automatically.

---

