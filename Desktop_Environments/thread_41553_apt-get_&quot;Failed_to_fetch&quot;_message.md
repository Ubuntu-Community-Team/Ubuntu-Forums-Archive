---
title: "apt-get &quot;Failed to fetch&quot; message"
date: 2005-06-13
forum: Desktop Environments
---

### Post by McSnickered on 2005-06-13
I'm using Kubuntu Hoary and am trying to get KDevelop working.  After working through several errors, I'm now getting the following error when trying to apt-get some Qt libs:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libj/libjpeg6b/libjpeg62-dev_6b-9_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libj/libjpeg6b/libjpeg62-dev_6b-9_i386.deb)  MD5Sum mismatch

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libpng3/libpng12-dev_1.2.8rel-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libp/libpng3/libpng12-dev_1.2.8rel-1_i386.deb)  MD5Sum mismatch


I've done an update, tried "--fix-missing", and "-f" but I get the same message.  I would greatly appreciate any help or even similar stories.

---

### Post by dare2dreamer on 2005-06-13
No idea what the error is, but I got the same errors on a server install this afternoon. I was trying to install mkisofs.

In the end, I just grabbed the files off my install disc.

Anyone know anything?

---

### Post by SGC on 2005-06-13
Try to change all refrences to "http://us.archive.ubuntu.com" into "http://archive.ubuntu.com" in apt-get sources file: 
/etc/apt/sources.list 

Then do:
sudo apt-get update

---

### Post by McSnickered on 2005-06-13
Thanks - that fixed it!

---

### Post by mrbit on 2005-07-12
what a provocative solution - why is us.archive.ubuntu broken?

---

### Post by ticklu2deth on 2005-07-12
I too had trouble with the 'us' repositories; are they indeed broken? I changed mine to point to the 'uk' repositories and had no problems, but it seems that the 'us' reps should be working for thos of us in the states.

Thanks, Jeff

---

### Post by monkster on 2005-07-13
Just to put in my 2 cents, SGC's post of a simple workaround saved the day for me, too.  This does mean something is wrong with the us. repositories, then?

---

