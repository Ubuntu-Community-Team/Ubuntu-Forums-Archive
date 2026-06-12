---
title: "problem installing wolfenstein enemy territory"
date: 2008-05-31
forum: Gaming &amp; Leisure
---

### Post by CrinkElite on 2008-05-31
Hi folks, I've been trying to install True Combat Elite on Ubuntu gutsy for a while now, I have been unable to install wolfenstien enemy territory which is required to install the mod.
 every time i try to run the et-linux-2.55.x86.run file I am presented with this, 

***@***-desktop:~/Desktop$ sudo ./et-linux-2.55.x86.run
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.55...........................................................................................................................................................................................................................................................................................................
/home/***/.setup7578: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
The setup program seems to have failed on x86/glibc-2.1

See [http://zerowing.idsoftware.com/linux/](http://zerowing.idsoftware.com/linux/) for troubleshooting
***@***-desktop:~/Desktop$ 


I'm not so hot at installing stuff without the synaptic or the apt-get install command, I understand that my system does not have the requird dependancies but I have no Idea of how to go about getting them. 
I have followed the link supplied by the error output and I've done a few google searches but I'm still none the wiser, anyone got any ideas?

thanks for reading

---

### Post by CrinkElite on 2008-05-31
Ok got it sorted, I had to download some toolkit for gimp, don't really understand how i figured that out but its working now.

---

### Post by glenmo on 2008-06-11
WHICH toolkit?  it would be helpful to have this on record for posterity

---

### Post by Perfect Storm on 2008-06-12
It's libgtk1.2 he installed. It's ancient ;), but some older games still requires it.

---

### Post by glenmo on 2008-12-26
sorry if this is a faux-pas but could you take a look at this problem:

i don't understand why it doesn't work...

[http://ubuntuforums.org/showthread.php?t=828968](http://ubuntuforums.org/showthread.php?t=828968)

---

