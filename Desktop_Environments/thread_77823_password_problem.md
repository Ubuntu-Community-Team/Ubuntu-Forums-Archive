---
title: "password problem"
date: 2005-10-17
forum: Desktop Environments
---

### Post by virka on 2005-10-17
I have kubuntu installed, but there is problem that during installation it did not prompt for a root password, but only for a username and password.

Now when i try to enter root mode, the password is unknown:
su
password: xxxxx
Authorization failed.

I can only work with my superuser account.

Anyone having similar problems? Help!

---

### Post by GrumpyBob on 2005-10-17
Did you try searching the forum?
[http://ubuntuforums.org/showthread.php?t=77502&highlight=root+password](http://ubuntuforums.org/showthread.php?t=77502&highlight=root+password)

Robert

---

### Post by virka on 2005-10-17
Thanks a lot for the reply.

In that case, im having hard times editing the /etc/apt/sources.list file, as it says i cannot overwrite.
Check access.

:)?

---

### Post by cytoplasm on 2005-10-17
virka,

Use the following command:

   sudo vim /etc/apt/sources.list

If you are not familiar with vi/vim then replace vim with your favorite editor.

---

### Post by virka on 2005-10-17
I'm following, i managed to changed that. Now, when trying to run sudo apt-get update, i get the following errror message: Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Sources Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages 404 Not Found [IP: 130.239.18.137 80] Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages 404 Not Found [IP: 130.239.18.137 80] Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Sources 404 Not Found [IP: 130.239.18.137 80] Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Sources 404 Not Found [IP: 130.239.18.137 80] Fetched 3B in 3s (1B/s) Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/) binary-i386/Packages.gz 404 Not Found [IP: 130.239.18.137 80] Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restr](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restr) icted/binary-i386/Packages.gz 404 Not Found [IP: 130.239.18.137 80] Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/) source/Sources.gz 404 Not Found [IP: 130.239.18.137 80] Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restr](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restr) icted/source/Sources.gz 404 Not Found [IP: 130.239.18.137 80] Reading package lists... Done W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backpor ts/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-b ackports_main_binary-i386_Packages) - stat (2 No such file or directory) W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backpor ts/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_br eezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or direct ory) W: You may want to run apt-get update to correct these problems E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by cytoplasm on 2005-10-17
There are no breezy-backports yet.

---

