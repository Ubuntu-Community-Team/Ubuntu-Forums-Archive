---
title: "autofs executable map not working"
date: 2012-08-01
forum: Desktop Environments
---

### Post by TheKeyMaker on 2012-08-01
Hi all,

I am having some difficulty lately setting up and executable map under ubuntu 12.04.  I have tried a number of different ideas but nothing seems to work so I am just trying to make it simplistic and get a bash script to echo back the right  parameters. 

My /etc/auto.master looks like this
```

/mnt/nfs    /etc/auto.disks

```

and then the /etc/auto.disks looks like this:
```
#!/bin/bash
echo "listen  -rw ip:[share dir] "
```

and then when I run cd /mnt/nfs/listen I get this:
```
bash: cd: /mnt/nfs/listen: No such file or directory
```

Ideas?

---

### Post by papibe on 2012-08-01
Hi TheKeyMaker.

/etc/auto.disks should hold a map for the automounter, not a shell script.

Check the format of both the master and the linked files by running:
```
man auto.master
```

Regards.

---

### Post by TheKeyMaker on 2012-08-01
thanks papibe, I like your picture!

anyways you should be able to user a shell script.  it is outlines in a number of examples like this site:

[http://docs.oracle.com/cd/E19963-01/html/821-1454/rfsrefer-75.html](http://docs.oracle.com/cd/E19963-01/html/821-1454/rfsrefer-75.html)

---

### Post by papibe on 2012-08-01
> **TheKeyMaker said:**
> thanks papibe, I like your picture!
:) Thanks.

> **TheKeyMaker said:**
> you should be able to user a shell script.  it is outlines in a number of examples like this site: [http://docs.oracle.com/cd/E19963-01/html/821-1454/rfsrefer-75.html](http://docs.oracle.com/cd/E19963-01/html/821-1454/rfsrefer-75.html)

Oopsy :oops:

You are right. I've used autofs for years, and I didn't know, thanks!

Try this:

First, confirm the server path:
```
showmount -d yourserver

```
The output should be something like:
```
Directories on yourserver:
/path/to/share
```

```
#!/bin/bash
echo "listen  -fstype=nfs,rw  yourserver:/path/to/share"
```
Let us know how it goes.
Regards.

---

### Post by TheKeyMaker on 2012-08-01
Yeah that seems ok...

Here is all the output.

```

user$ showmount -d [ip of server]
/share/media/glance
/share/media/watch

```

So these are the two directories that I am sharing

```

user$ less /etc/auto.master
/mnt/nfs    /etc/auto.disks --ghost 


```


```

user$ less /etc/auto.disks
#!/bin/bash
echo " watch -fstype=nfs,rw  [ip of server]:/share/media/watch "

```

Permisions:

```

user$ ls -al /etc/auto.*
-rwxrwxrwx 1 root root   77 Aug  1 21:27 /etc/auto.disks
-rw-r--r-- 1 root root   38 Aug  1 21:28 /etc/auto.master
-rw-r--r-- 1 root root  660 Mar 22 06:21 /etc/auto.master.ucf-dist
-rw-r--r-- 1 root root  524 Mar 22 06:21 /etc/auto.misc
-rwxr-xr-x 1 root root 1374 Mar 22 06:21 /etc/auto.net
-rwxr-xr-x 1 root root  687 Mar 22 06:21 /etc/auto.smb

```

as you can see I decided to set the permisions to chmod 777 to make sure that it wasn't a permisons issue and that everyone would be able to execute it. I get the same results as before.

I can mount it fine manually doing the following:

```
mount [ip of server]:/share/media/watch /mnt/nfs
```

---

### Post by TheKeyMaker on 2012-08-02
Have still been trying other ideas, but nothing seems to work.  
Doesn't autofs log to a log file somewhere?  I forget off hand.  
Would it send an error message to the logs if it can't mount the
location?

---

### Post by papibe on 2012-08-02
I tested it on my on system, and it actually works following the Oracle syntax:
```
#!/bin/bash
[[ "$1" == "watch" ]] && echo "-fstype=nfs,rw  yourserver:/share/media/watch"

```
Let's know how it goes.
Regards.

---

### Post by TheKeyMaker on 2012-08-02
> **papibe said:**
> I tested it on my on system, and it actually works following the Oracle syntax:
```
#!/bin/bash
[[ "$1" == "watch" ]] && echo "-fstype=nfs,rw  yourserver:/share/media/watch"

```
Let's know how it goes.
Regards.

Yes!! That did work, but there is one last part that is missing.  
I have to say that autofs seems a little more buggy when you add this option.

When I add the --ghost option and restart autofs it doesn't show the directory watch.  I did find after playing around with it that it does show the directory after I mount it sucessfully once, but then it fails to run the script after I umount and try and remount it again.

I will have to play around with this some more this weekend and let you know how it goes. Hopefully I can get it all working and consistent.


Thanks again papibe!!  You have move me closer in the right direction!

---

