---
title: "Rsync Command Skips Directories?"
date: 2008-12-10
forum: General Help
---

### Post by CarlosinFL on 2008-12-10
I am trying to use Rsync to copy an entire directory from my PC to a server on the same LAN and for some reason my command is not working.

```
/usr/bin/rsync -vv -e ssh /media/usb/fback/it/* root@fback:/it/
```

I am copying the contents of everything in the 'it' folder on my external usb drive to the remote 'fback' server under the same directory name. The folder does exist on the remote server.

Here is what I get:

```
opening connection using: ssh -l root fback rsync --server -vve.L . /it/ 
root@fback's password: 
skipping directory carlos
skipping directory jason
skipping directory mike
skipping directory movies
skipping directory symantec_10.1.7
delta-transmission enabled
total: matches=0  hash_hits=0  false_alarms=0 data=0

sent 8 bytes  received 12 bytes  4.44 bytes/sec
total size is 0  speedup is 0.00

```

What am I doing wrong?

---

### Post by Titan8990 on 2008-12-10
Remove the wildcard and give rsync the -a option:

rsync -avv -e ssh /media/usb/fback/it/ root@fback:/it/


Haven't used rsync over ssh so I can't tell you if that syntax is correct.


It skipped all those directories because you didn't tell rsync to backup directories.

To do so you have to use the -a or -r options.

For future reference most applications that can manipulate both files and directories need -r option.


An example:

rm *

will only delete files and leave directories alone like you saw in rsync

rm -r * will delete all folders and files.

---

### Post by CarlosinFL on 2008-12-10
Thanks for that info!

I ran the following and it appeared to work!

```
cwilliams@tunafish:~$ /usr/bin/rsync -ave ssh /media/usb/fback/it/ root@fback:/it/
```

---

