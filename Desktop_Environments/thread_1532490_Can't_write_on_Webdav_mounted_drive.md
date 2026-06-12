---
title: "Can't write on Webdav mounted drive"
date: 2010-07-16
forum: Desktop Environments
---

### Post by Saorex on 2010-07-16
Hi guys. I use davfs2 to mount a Webdav drive at startup. It mounts correctly and I have read access to all files my account gives me access to. One big problem though: I can't create of modify any file. I know it is not a user account problem because everything works well when I mount the drive in Windows 7 using WebDrive.

Here's the entry in /etc/fstab to automatically mount the drive:
```
http://someserver.local/docs /home/my_user/km_docs davfs user,rw,auto 0 0
```

The Webdav is hosted on a local SAP Portal server (if anyone is familiar with this).

I also tried to use Cadaver. It connects and reads perfectly. But when I try to create a file, I get a "409 Conflict" error, even the file has never existed on the server before.

Any help would be much appreciated. Thanks a lot!

---

### Post by Saorex on 2010-07-21
I finally made a successful file creation with Cadaver. Turns out to be s very simple problem outside of Cadaver's scope.

I also found PHP WebDAV ([http://php-webdav.pureftpd.org/project/php-webdav](http://php-webdav.pureftpd.org/project/php-webdav)) which will be a great tool for this PHP project I'm working on.

Thanks to all those who read me and *tried* to help... Hehe! ;)

---

### Post by cbpilot on 2011-03-29
Hi Saorex,    

have the same problem or at least a similar: I get an "409 Conflict" error when I try to write with cadaver on my WebDAV space. Everything else works fine.  

What was the solution in your case?  

Gernot

---

### Post by cbpilot on 2011-03-29
> **Saorex said:**
> Turns out to be s very simple problem outside of Cadaver's scope.

Error 409 means: the problem exists on the client side. In my case it was a classical PEBKAC and is now solved, too. I used the wrong syntax.

You can put a file on the server with one of the following commands:
```
# put the file to the working dir (on the server)
put /tmp/test.file
# put the file to the server with a new name
put /tmp/test.file renamed.file
# put the file into an existing directory on the server
put /tmp/test.file /testdir/test.file
```Maybe this will help someone else to fix this issue. Or in other word: I hope that I'm not the only PEBKAC ;)

---

