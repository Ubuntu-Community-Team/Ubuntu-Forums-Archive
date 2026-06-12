---
title: "virtualbox share persistence"
date: 2009-03-27
forum: General Help
---

### Post by tacoma50 on 2009-03-27
Running Virtualbox on x86
 Host = vista
 virtualmachine = ubuntu 8.10

I Created a folder called myVBshareFOLDER on my Vista desktop. 
Then I shared it in VirtualBox like this:
 Machine - Settings - Shared folders - Add new shared folder. 
   I gave the share name of: myVBshare

Then on ubunto I created this directory: 
  sudo mkdir /mnt/myshareFolder
Then I mount the share:
 sudo mount -t vboxsf  myVBshare /mnt/myshareFolder


Everything works, but when I restart ubunto I must run the mount command again.

How can I make the mount persistent?

---

### Post by Jgonick on 2009-03-27
Add it to fstab file

Try...  [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by coffeecat on 2009-03-27
If you're new to the joys of /etc/fstab, you'll need this line (modified from mine):

```
myVBshare    /mnt/myshareFolder    vboxsf    uid=1000,gid=100    0 0
```But check your UID (User ID) and GID (Group ID) in Users and Groups first. If yours is the first created account, then the uid and gid will be 1000 and 100. But if not, you'll have to change the values.

---

