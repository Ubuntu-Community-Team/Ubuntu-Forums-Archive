---
title: "how do I backup my user data files to web hosting service"
date: 2006-08-01
forum: Desktop Environments
---

### Post by brickbat on 2006-08-01
Hi,

I want to backup my local data files to a hosting service I have signed up with.  They offer loads of disk space and bandwidth and I figure I may as well use it for something practical.

I would like it to have the following features;
    1. files to be unencrypted locally but the remote backup to be encrypted.  

    2. Be able to download individual files from the backup as simply as possible - preferably from any pc with a browser.

    3. Sync with the backup on a daily basis but only files that have changed.

What software/setup would you recommend?

---

### Post by jordilin on 2006-08-01
Take a look at rsync or rdiff-backup

---

### Post by brickbat on 2006-08-01
Thanks for the ideas.  I looked into them but I can't see any encryption options.

---

### Post by jordilin on 2006-08-01
Yes, it seems that rdiff-backup and rsync don't provide encryption,  perhaps the best solution would be using tar and gpg. Another solution would be that the target backup directory had an encrypted filesystem, so any file written on it would be encrypted at the same moment, but this is not the case.

---

### Post by roderikk on 2007-04-03
Hello,

I am looking into something very similar. I have a hosting provider that has given me a tremendous amount of diskspace and bandwith. So I would like to have a system in which I can do incremental backup to this server but of course they would have to be encrypted.

I am using Feisty and as such it seems that Kdar is not installed, not that I think it would be of much help since according to their sourceforge site it hasn't been updated in a year.

I cannot find a sufficiently clear tutorial of dar to be able to use it. Anyone else used it successfully over ftp?

I have also looked into Duplicity (which uses rsync as its back) but first of all this also hasn't been updated in over a year and secondly it doesn't work for me at the moment.

Does anyone have a working solution for this already?

Thank you very much.

---

### Post by roderikk on 2007-04-03
Ok, what I have found so far (but didn't get to work yet) is the following:

[https://wiki.ubuntu.com/HomeUserBackup](https://wiki.ubuntu.com/HomeUserBackup) This program will be available and allows a front end for dar. I do not however right now know if it will encrypt the data.

However, as it states on the wiki page:

> Backup to a user-specified path on a filesystem. (This could cater for non local medium backup if those are mounted and visible as part of the filesystem tree.)

This got me thinking, what if I could mount an ftp drive as a local drive and just do the backups to there. So at the moment I am investigating fuseftp: [http://wiki.thiesen.org/page/Fuseftp](http://wiki.thiesen.org/page/Fuseftp)

I have now found that the following actions are at least required:
```

sudo aptitude install fuse-utils           *******not sure if this is necessary?
sudo cpan Fuse Net::FTP Cache::File Term::ReadKey

mkdir fuseftp
cd fuseftp
wget http://perl.thiesen.org/fuseftp/fuseftp-0.8.tar.gz
tar -xvf fuseftp*.tar.gz .
perl Makefile.PL
make
sudo make install
```

This should install fuseftp. However, since I am running feisty something is going wrong when using CPAN and the Fuse package doesn't seem to install properly.

Therefore I tried to download the deb package from their site:

wget [http://debian.jox.be/fuseftp_0.8-1_all.deb](http://debian.jox.be/fuseftp_0.8-1_all.deb)

But that doesn't want to install because perl seems to behave strange in feisty. Can anybody get it to work with edgy (or feisty for that matter?)?

As stated before I would then use this mounted drive to backup the data using dar. But I would really appreciate if someone with some more knowledge about that would be able to tell me how I can use dar to create a (in this case 'local') incremental encrypted backup of - some of - my folders in home. Or in another case, if someone has more experience with hubackup, if that provides encrypted backups.

Thank you for your help!

---

### Post by roderikk on 2007-04-03
Hm, I just found out that fuse (don't know which :-$ ) creates a 'fuse' group in the user/groups part. However, after adding my user (root and local) this didn't make any change... (or do I need a restart?).

---

