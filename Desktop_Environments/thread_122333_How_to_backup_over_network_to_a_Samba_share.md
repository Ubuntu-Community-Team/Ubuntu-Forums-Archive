---
title: "How to backup over network to a Samba share?"
date: 2006-01-27
forum: Desktop Environments
---

### Post by kenquad on 2006-01-27
Hi all:

I'm a Kubuntu user on a windows network and I would like to periodically, automatically back up my entire Desktop and email to a remote Samba share where I have rwx privileges on the shared folder.  Konserve doesn't seem able to do this but maybe I'm missing something.

Thanks,
kenquad

---

### Post by uselpa on 2006-01-27
Just mount the samba share and have your backup written to the local mountpoint.
Something like this in /etc/fstab:
//server/backup  /mnt/backup smbfs noauto,ucredentials=/etc/fstab.smbcred.server 0 0

---

### Post by kenquad on 2006-01-30
Thanks, but still a problem: It didn't work.

I added the text you specified, replacing ```
//server/backup
``` with ```
smb://hostname/folder/folder
``` but got a file does not exist error when attempting to mount.  ???

---

### Post by uselpa on 2006-01-30
Just add the line as I indicated, replacing only //server/backup with your server name and the share name.

Don't add smb://
Don't indicate 2 folders, just the server name and the share name.

---

### Post by kenquad on 2006-01-30
Didn't work.  I'm still getting no such file errors.  BTW, the graphical filesystems applet in kcontrol does not see my network when I browse from there, though I can go all through the network via remote places.  Maybe if I can correct this the problem will be fixed.

---

### Post by uselpa on 2006-01-30
Could you post your /etc/fstab or the command you use to mount the samba share?
If you mount the filesystem manually, are you getting any error?

---

### Post by kenquad on 2006-01-30
Here's the line in my /etc/fstab (actual text anonymized):
```
//remotecomputer/sharedfolder /mnt/backup smbfs ucredentials=/etc/fstab.smbcred.server,loop,uid=1000,gid=1000,auto,rw,users,credentials=/etc/fstab_smb_credentials_1 0 0
```
I am not sure how to go about trying to mount the drive manually but I very much doubt that would work either.  If you could post the code I'd like to try it.

Thanks

---

### Post by uselpa on 2006-01-31
The mount command would simple be "mount /mnt/backup", mount will get its details from /etc/fstab.
I don't see why you'd need "ucredentials" and "credentials", "ucredentials" should do as in my (actually working) example. Also "loop" must not be used (why did you add that?). "auto" only makes sense if the samba server is always available (is it?).
Now post the result of the mount command to see where the problem is.

---

### Post by kenquad on 2006-01-31
OK; the extraneous code in /etc/fstab was produced by my futile attempts to use Kcontrol to correct the problem.  I deleted all that and replaced it with your code modified exactly as you specified.  Here is the result of trying to mount (anonymized, of course):
```
kenquad@kenquad:~$ sudo mount /mnt/backup
[mntent]: warning: no final newline at the end of /etc/fstab
mount: wrong fs type, bad option, bad superblock on //remotecomputer/Shared_Folder,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
???

---

### Post by uselpa on 2006-01-31
You must have package "smbfs" installed. Just add it.

---

### Post by kenquad on 2006-01-31
Whoaa!!! It works!!  Thanks a million, uselpa.  BTW, I'm also having trouble mounting an NTFS partition into storage media.  Is there some package I need in order to do that perchance?

---

### Post by uselpa on 2006-02-01
Not sure, I don't have a Windows partition on my Ubuntu Box.
In Slackware, I have this in my /etc/fstab:

```

/dev/hda1 /mnt/win ntfs  noauto,ro,gid=100,umask=0,nls=iso8859-15 1 0

```

Now do the same as for Samba: change fstab, mount the partition manually, post the error... you know the drill ;-)

---

### Post by kenquad on 2006-02-01
Worked like a dream, uselpa.  You've been a huge help.  Thank you.\\:D/

---

### Post by anthro398 on 2006-02-02
You can also see [this script]("http://ubuntuforums.org/showthread.php?t=106795") I wrote for automating network backups.  It incorporates encryption with a pgp key, but you can take that out.  I also posted my [remote mount]("http://www.braggtown.com/projects.html") script.  I had to write my own stuff since I don't use Windows.  Everybody else her uses Windows or Mac and have backups done for them.  The odd-balls who use FreeBSD, Solaris, and Linux have to roll their own.

---

