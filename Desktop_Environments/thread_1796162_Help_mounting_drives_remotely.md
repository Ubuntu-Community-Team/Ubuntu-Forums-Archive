---
title: "Help mounting drives remotely"
date: 2011-07-03
forum: Desktop Environments
---

### Post by DavidWeight on 2011-07-03
Hi,

Bit of an annoying problem-hopefully someone can point me in the right direction. I've got a server running which has had the power restarted, and so the drives (aside from the boot drive) have not been mounted, and not showing up in /media
Normally I'd just open them from the menu, but the only access I have to the server is though a webmin interface as I'm abroad at the moment (a command line, basic file manager etc.). I was looking to mount them through the command line, but got stuck when I couldn't remember what file system is on there.
Is there a way to do the equivalent of opening the drive up on the desktop but through the command line, and if not, is there a way to get these mounted and working remotely?

Thanks!

---

### Post by drdos2006 on 2011-07-03
Webmin will do that for you.
Go to System -> Disk and Network FileSystems. Mount your drive with Add Mount.

regards

---

### Post by steinerd on 2011-07-03
Well, might seem as I am playing the master of the obvious but have you tried

```
mount -a
```from the command shell utility in webmin?  I'll take a look at my config and see if I can help you out...  As I typed that I figured out what a retard that I am.  If they were in the fstab they would have mounted at boot.  Are you speaking of network drives?  NFS CIFS SMB?  also, is it that you have the noauto flag set for local drives, and this is why they are not mapping?

From webmin command shell you should be able to do a 

```
showmount -e {server}
```to find your desired mount point if you are using nfs...  then

```
mount -t nfs server:path/to/files /local/path
```similar commands are sufficient of SMB and CIFS.

Typing
```
mount /path/to/device /mount/dir/
```should be sufficient to mount your drive with defaults.

Hope this helped some...

Edit:  Just tried my server from the command shell in webmin.  was able to mount/umount all of my network drives and my usb disk.  Pretty sure you are on the right track with command shell guess it's just a matter of finding the right syntax.  There seems no difference from running it local as far as my machine is concerned.

---

### Post by DavidWeight on 2011-07-03
Thanks guys-didn't realise you could mount it graphically once I got the file system from the command line! Still slowly learning about Webmin-and cheers for the pointer about being able to mount with defaults

---

