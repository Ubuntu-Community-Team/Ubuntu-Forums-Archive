---
title: "FTP Sync using curlftpfs and Unison"
date: 2009-02-26
forum: General Help
---

### Post by deeem119 on 2009-02-26
I've been looking for a way to sync a local directory with an FTP location. I'm trying to replicate the way Dreamweaver can edit files locally, and then sync them later with an FTP server.

After much searching, I thought I'd found a method - use curlftpfs to mount the FTP site as if it was a local folder, then use Unison to sync them. All went well in the setup, until I tried syncing from the REAL local folder to the mounted FTP folder.

For the sake of clarity, here is a mock up of my setup:

Real directory: /home/user/websites/mysite.com
Mounted FTP dir: /home/user/ftpmount/mysite.com

I can create/edit/delete files in both directories directly.
If I edit a file, or delete one, in the mounted FTP dir, then run Unison, it will sync those files back to the local dir. Great. If I change a file in the FTP dir, then sync, it errors, with something like the following:

```

test.txt
Error in copying locally:
No such file or directory [open(/home/user/ftpmount/mysite.com/.unison.test.txt.840c8ac9c84ef4c6286a10b13833dcf4.unison.tmp)]

```

Anyone see any obvious errors in what I've done, or have I been caught out by thinking I could get around Unison not supporting FTP by using curlftpfs?

Thanks,

---

### Post by deeem119 on 2009-05-18
Thought I'd reply with my own results... Not sure what I had done wrong, but after a couple of reboots the exact setup I had mentioned works fine, just very slowly.

It has acceptable performance for a small site (or a sync of a subfolder in a site) over a good ftp link.

---

### Post by sextheorist on 2010-11-09
Great tutorial........  It rocks :guitar:


For beginners heres how to set 
**[CurlFtpFS]("http://blog.mypapit.net/2007/05/how-to-use-ftp-filesystem-on-ubuntu-using-curlftpfs.html")**


First of all you need to install CurlFtpFS, which in case of Ubuntu or Debian based operating system is to run ```
sudo apt-get install curlftpfs
```Assuming you've successfully installed curlftpfs, all you need to do in order to mount ftp locally is to to run these commands. 
 ```
mkdir hostr
``` ```
sudo curlftpfs -o allow_other ftp://user:pass@ftp.example.com hostr
``` *user:p**** is the username and password  to log into ftp account.
and dir hostr is the *host point.*


 After that, you can change your working directory to the mount-point and use the regular unix utilities to work on the files that normally accessible on the FTP protocol. After you're done, you can unmount it by running the usual "*sudo umount [mountpoint]*" command.


This will b enough for CurlFtpFS. now your ftp folder will as a local folder.

[U][B]
[COLOR=Red]Installing and using unison

[/COLOR][/B][/U]Unison can be found in Ubuntu's Universe software repository, in the *unison* package. Many users will also want the *unison-gtk* package as well for a GTK GUI. See [InstallingSoftware]("https://help.ubuntu.com/community/InstallingSoftware") for information about installing software, and [Repositories]("https://help.ubuntu.com/community/Repositories") if you need help enabling Universe. 

**GUI usage**

 Unison includes a GUI interface that allows you to graphically work with the application. You can access it by going to **Applications -> Accessories -> Unison** or by pressing Alt+F2 and typing *unison*. 
 
[B]thanks for reading..
[/B]



[U][B][COLOR=Red]

[/COLOR][/B][/U]

---

### Post by jaya28inside on 2010-12-02
hello sextheorist,


seems that i'm un-aware of something here.
I did what u suggest for mounting them in.
And yes it works.

It just like,... hmmmmph.
The problem occured when I tried to copy or move some files
to or from it. It will generate Input / Output Error something like that. is there anyone encountered it as well? :o

---

