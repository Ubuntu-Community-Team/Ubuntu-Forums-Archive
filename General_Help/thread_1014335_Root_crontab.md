---
title: "Root crontab"
date: 2008-12-17
forum: General Help
---

### Post by cK-judic on 2008-12-17
I've created a script that svnadmin dumps all my repositories, tarballs the dump files, and then moves that file to a windows box. When logged in as root I can run the script and everything works perfectly. However, I setup a root crontab (I did not do sudo crontab -e, I logged in as root) to execute the script and everything works...except my tarball is at 0 :confused:. It does not seem to tar the files correctly, however it does still move the empty tar to the windows box.

Here's the script
```


# File permissions below
#-rwxr-xr-x 1 root            328 2008-12-17 18:34 repos_dump


#!/bin/bash
SVNDIR=/home/svn
TARNAME=repositories_dump.tar

cd $SVNDIR

rm -f *.svndump
rm -f *.tar

for repo in $(ls -d */)
do
        filename=`basename $repo | cut -d\. -f1`
        svnadmin dump $repo > $SVNDIR/$filename.svndump
done

tar -cvf $SVNDIR/$TARNAME *.svndump

cp $TARNAME /mnt/windozebox/home/
```

Here is the crontab```
# m h  dom mon dow   command
35 18 * * * /home/svn/repos_dump

```

Again this works when i do ./repos_dump as root, but not through root's crontab. I'm so confused. Any help is appreciated. Thanks.

---

### Post by ibuclaw on 2008-12-17
Try:
```
35 18 * * * exec /home/svn/repos_dump
```
Regards
Iain

---

### Post by cK-judic on 2008-12-17
> **tinivole said:**
> Try:
```
35 18 * * * exec /home/svn/repos_dump
```
Regards
Iain
Unfortunately, adding "exec" did not work.

---

### Post by geirha on 2008-12-17
Install [mailx](apt://mailx) and run ```
sudo mail
``` Cron mails you the output of the script (using a local mailing system), so those mails should contain the error messages the script produces.

BTW, no need to use ls in your for loop.
```
for repo in */
``` is much better.

---

### Post by ibuclaw on 2008-12-17
Maybe
```
35 18   * * *    cd /home/svn && ./repos_dump
```
instead?


Only other option I'd suggest is putting it in the /etc/crontab file

```
sudo gedit /etc/crontab
```
And put in:
```
35 18   * * *   root    cd /home/svn && ./repos_dump
```


Regards
Iain

---

### Post by Dr Small on 2008-12-17
Since the file is being moved, and the tar ball being created (at 0bytes) I have reason to suspect the issue is related to tar. I'll have to look over your script again.

---

### Post by cK-judic on 2008-12-17
Okay, I'm even more confused now. I installed mailx as suggested, and then I decided I didn't want to setup a mail server. Instead of having crontab mail me error information, I decided to simply direct the output to /home/svn/repos_dump.log

So my crontab is now
```

52 20 * * * /home/svn/repos_dump > /home/svn/repos_dump.log

```

It only output the single filename, which means it didn't redirect svndump's output of revision history, but, IT WORKED. :confused:

What's more is that I then REMOVED the log piece so that _EVERYTHING_ was the same as it was previously, and then it still worked. :confused::confused::confused::confused:

---

