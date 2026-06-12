---
title: "Sharing home with Ubuntu 6.10"
date: 2007-04-17
forum: Debian
---

### Post by UbuntuniX on 2007-04-17
I haven't done this before, so my method is probably bad.

On Debian 4.0, I went to Administration -> Disks, selected the Ubuntu partition, mounted it as /ubuntu and enabled.

I then set my home directory to /ubuntu/home/ubuntunix from Debian, but every time I reboot and login, I get the message that my home directory cannot be found. So then I have to login as root and go through the mounting procedure again.

I've noted that when I login as root, /ubuntu seems to show up fine.
So, I presume the problem is that the disk manager thing doesn't start until I have logged in...

Could anyone help me in a way of fixing this, or a better method?

PS: Debian Forums is a ghostland...

---

### Post by rmemm on 2007-04-17
I don't know about disk manager, but the way one normally mounts partitions at boot time is to modify /etc/fstab.  See man fstab for the format of the file -- plus there should already be entries there.  Probably good to keep a copy of the original too.

Are you trying to share all of /home or just a single user?  Also what user name?  ubuntunix?

Depending on what your doing -- there are several ways this can be done.  If I wanted to share all of /home between the two systems ideally i'd put /home on a separate partician then just mount it on each system.  If not a separate partician, I'd mount it like you did, and then symlink the /home sub directon to /home on each systems root partician (I think this works but you'd need to try it).  If a specific user -- then I'd do the same thing but just simlink the users are wanted to share.  Changing home directories in /etc/passwd should work also in the latter case.

One thing about sharing users -- your users will need to be using the same uid and gid number scheme between the two systems -- otherwise you'll have ownership problems I think.

Rob

---

### Post by UbuntuniX on 2007-04-17
> **rmemm said:**
> 
Are you trying to share all of /home or just a single user?  Also what user name?  ubuntunix?


I'm trying to share the whole partition, and change my home directory to Ubuntu's (/home/ubuntunix).

---

### Post by Ti_Uhl on 2007-04-17
You should edit your /etc/fstab file to mount the partition at boot time, check 'man fstab' for the correct options to set.

---

