---
title: "Dynamically mount network shares"
date: 2004-11-17
forum: Desktop Environments
---

### Post by deeler on 2004-11-17
The "network" button in the computermenu works great, I can browse all the workgroups and all pc's in the network. When I double click on, let's say a JPEG for viewing, it works. I know the path is described as smb://pc/share/file.jpeg, but how do I for instance attach that file to an email in evolution ????  I looked in /mnt/ but nothing there. Is it so that I have to manually mount the shares ??? It would be great if any file  or any shares that is browsed in the network was also auto-mounted in /mnt ... or at least a right-click option in the nautilus gui to mount it. 

Does anybody know a solution to this problem? The mount-at-boot trick in fstab is not suitable for me, as my metwork topology tends to change quite often, especially with a significant amount of laptop users.

help is welcome.

UBUNTU RULES
 =D>

---

### Post by duff on 2004-11-17
You can either drag to your dekstop first (copy it), or maybe you could just drag it straight into evolution.  Not sure if that'll work though..but it should.

---

### Post by deeler on 2004-11-18
drag and drop is not suitable, some OpenOffice documents are read/write on a network share and they need to be openen from that share instead of a desktop-copy....

---

### Post by castrojo on 2004-11-18
I usually use Nautilus' "Connect to Server" feature for my most commonly used SMB resources. This places that certain directory in the bookmarks in the file selector as well as in the computer window. Then when I click on attach in Evolution, the shortcut to that directory is already there in the file selector.

That obviously won't work if you're just browsing around and find a file you want to email, but if you have certain working directories that you visit often it might work for you.

---

### Post by inc595 on 2004-12-11
a great package is xsmbrowser. makes mounting win shares easy

---

### Post by Abhi Kalyan on 2006-11-06
> **inc595 said:**
> a great package is xsmbrowser. makes mounting win shares easy
xsmbrowser,
Thank you inc595, thats great news
Thank you once again

---

