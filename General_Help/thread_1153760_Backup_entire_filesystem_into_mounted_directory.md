---
title: "Backup entire filesystem into mounted directory"
date: 2009-05-09
forum: General Help
---

### Post by BradJohnson on 2009-05-09
Hi, first post.

I have ubuntu 8.10 installed on sda1, and sdb1 mounted there in /share.

I would like to back up my entire (sda1) filesystem into something like /share/backup.

My first thought was something like 

sudo cp -R / /share/backup/

...but I'm afraid that will try to recopy itself as /share fills up?

What's the correct way to do this?

Thanks
Brad

---

### Post by Legace on 2009-05-09
You could use rsync, like this:

```
sudo rsync -av --delete --exclude-from="***PATH***/exclude" / /share/backup
```

Where ***PATH*** is the directory where exclude is saved.

exlude should be like this (you don't need to back those up, you could backup /boot if you want):

```
boot/
proc/
dev/
lost+found/
sys/
media/
tmp/
share/backup/
```

Note that share/backup/ is the folder your system will be backed up to. If you decide to change that location, do so in the exclude file aswell.



To restore the backed up files, you would use:
```
sudo rsync -av --delete --exclude-from="***PATH***/exclude" /share/backup /
```



Note that this will take a while to complete.
Also note that after doing this once, the following times will be much faster (as it will update only changed files)..

---

### Post by BradJohnson on 2009-05-09
Cool ok thanks for the reply, I just want to make sure I have the syntax correct.

"exclude" is a file I create, perhaps in /home/brad/, right?

So therefore:

sudo rsync -av --delete --exclude-from="/home/brad/exclude" / /share/backup






edit: nevermind, it's running now... appears exactly what I was looking for, thanks again

---

### Post by BradJohnson on 2009-05-09
Can anybody decode this?  

```
sent 1289248219 bytes  received 616643 bytes  14252650.41 bytes/sec
 total size is 1286898691  speedup is 1.00
 rsync error: some files could not be transferred (code 23) at main.c(1058) [sender=3.0.3]
 
```Exact cmd line was 

```
sudo rsync -av --delete --exclude-from="/home/brad/exclude" / /share/backup

```and exclude file is

```

proc/
dev/
lost+found/
sys/
media/
tmp/
share/

```I don't really know how to check if it worked or not.

I'm thinking maybe I should have added cdrom/ to the exclude file?  It's light blue in / but red in /share/backup...

---

### Post by Legace on 2009-05-09
It usually has erros. Some files might not be copied, but those files will most likely not be crucial. Nothing to worry about :)

---

