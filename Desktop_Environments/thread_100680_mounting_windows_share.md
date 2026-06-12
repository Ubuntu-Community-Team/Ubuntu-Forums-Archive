---
title: "mounting windows share"
date: 2005-12-08
forum: Desktop Environments
---

### Post by Balakrishnan on 2005-12-08
I am new to Ubuntu.

I have installed Ubuntu 4.10 in my hard disk.

I have another machine running Windows XP with a "read only" share. It is accessible to all in Intranet.

I am able to mount this share in Knoppix and many distributions using the following command (as root or sudo)

  mount -t smbfs -o username="windows_domain\username" //ip_no_of_winXP/sharename /mnt

However, it is not working in Ubuntu and some more distributions. Ubuntu 4.10 gives the following error :

wrong fs type or bad option or bad superblock or too many monted file system

Please guide me.

---

### Post by HighPlainsDrifter on 2005-12-08
```
sudo apt-get install smbfs
```

Try that. Also, the version of Ubuntu you are running is the oldest of the two (er, three, technically)

---

### Post by Balakrishnan on 2005-12-08
I do not have access to "ftp". My firewall does not allow "ftp". So, upgrading a package through apt-get from Internet is not possible.

If someone can confirm that mounting of windows share in XP is possible in Ubuntu (the latest version), I can download the latest version.

Or alternatively, if there is some problem in the command line, please correct me - so that it works in Ubuntu 4.10 itself.

---

### Post by kori.mendocino on 2005-12-08
the smbfs and smbclient packages should be located somewhere on your ubuntu install cd, but i'm not too sure, and issuing an apt-get of smbfs (with your cd repository uncommented in the sources.list) is the best way to test this.

---

### Post by GoldBuggie on 2005-12-08
ftp??? Why not go here [http://archive.ubuntu.com/ubuntu/pool/main/s/samba/](http://archive.ubuntu.com/ubuntu/pool/main/s/samba/) and download it http.
Then install it using ```
sudo dpkg -i [smbfs_3.0.20b-2ubuntu1_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/s/samba/smbfs_3.0.20b-2ubuntu1_i386.deb")
```[]("http://archive.ubuntu.com/ubuntu/pool/main/s/samba/smbfs_3.0.20b-2ubuntu1_i386.deb")

---

### Post by jferrando on 2005-12-08
Why using ftp with repositories... use http. You need to modify [COLOR="Red"]/etc/apt/sources.list[/COLOR] like this:

deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

in al the lines replace ftp with http.

---

