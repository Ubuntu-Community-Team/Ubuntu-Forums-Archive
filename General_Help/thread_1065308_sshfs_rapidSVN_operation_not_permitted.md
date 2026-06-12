---
title: "sshfs rapidSVN operation not permitted"
date: 2009-02-09
forum: General Help
---

### Post by pfwd.tech on 2009-02-09
I've searched Google and I still cant find a solution to this problem...
I have svn set-up on my dev server and I can access the svn commands(svnadmin co ci etc) as normal via the comandline. I now want to control my projects via rapidSVN on my local machine but every time I checkout a new working copy i get the error:
```
Execute: Checkout
Error: Error while performing action: Can't move '/media/test2/test2/.svn/tmp/entries' to '/media/test2/v1/.svn/entries': Operation not permitted
Ready
```media/test2 is a mount point to media on the server
These are my attempts in fstab
```
sshfs#<user>@<ip>:/media  /media/test2    fuse    -o workaround=rename    0       0

sshfs#<user>@<ip>:/media    /media/test2    fuse    defaults,users,allow_other,auto 0       0

sshfs#<user>@<ip>:/media /media/test2     fuse    users,allow_other,uid=1000,gid=1000,umask=000     0       0
```Each of these attempts is giving the same error.
These are my permissions
on the server
```
drwxrwxrwx   8 pfwd pfwd     4096 2009-02-09 18:30 media
```On the local machine
```
drwxrwxrwx 1 pfwd pfwd  4096 2009-02-09 23:30 test2
```Both the user on the server and on the local machine is called pfwd

This is the output from sshfs -V 
```
SSHFS version 2.0
FUSE library version: 2.7.3
fusermount version: 2.7.3
using FUSE kernel interface version 7.8

```I don't think its the workaround=rename issue as mentioned here
[http://apps.sourceforge.net/mediawiki/fuse/index.php?title=SshfsFaq#Why_does_SVN_.28etc....29_fail_to_rename_files.3F](http://apps.sourceforge.net/mediawiki/fuse/index.php?title=SshfsFaq#Why_does_SVN_.28etc....29_fail_to_rename_files.3F)

Please note that this is a home dev server and not a production server and that I am aware about the 777 permissions the above  directories  have. Once I have sorted this out I will change these permissions back.

If any one could lend me a hand I would appreciate it very much.

---

### Post by pfwd.tech on 2009-02-10
bump can any one point me in the right direction?

---

### Post by pfwd.tech on 2009-02-21
Just solved it.
heres the explanation [http://liquidat.wordpress.com/2008/08/10/short-tip-moving-files-on-sshfs-mounts/#](http://liquidat.wordpress.com/2008/08/10/short-tip-moving-files-on-sshfs-mounts/#)

heres my fstab options:
```
sshfs#<USER>@<IP>:/var/www        /media/http     fuse     rw,workaround=rename,cache=no,user,allow_other 0 0
```-o workaround=rename is needed!
Hope this helps someone else.

---

### Post by chikko on 2009-02-23
helped me! thanks!!

---

### Post by catacgc on 2009-03-14
I had the same problem with subversion add operation. Your solution worked very well. tks

---

### Post by spiderbaby33 on 2011-04-28
I realise this is an old thread but this really helped me as well. I was pulling hair trying to figure out what was wrong.

Thanks :-)

---

### Post by freek_zero on 2011-08-16
This is a first. I googled for a solution to this issue and this was the ONLY hit. And it was actually what I needed. Talk about niche. Thank you!

---

