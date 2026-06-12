---
title: "Rsync doesn't copy everyting"
date: 2009-05-31
forum: General Help
---

### Post by Scormen on 2009-05-31
Hi all,

I'm having some trouble with rsync. I'm trying to sync my local /etc directory to a remote server, but this won't work.

The problem is that it seems he doesn't copy all the files.
The local /etc dir contains 15MB of data, after a rsync, the remote backup contains only 4.6MB of data.

Rsync is running by root. I'm using this command:

```
rsync --rsync-path="sudo rsync" -e "ssh -i /root/.ssh/backup" -avz --delete --delete-excluded -h --stats /etc kris@192.168.1.3:/home/kris/backup/laptopkris
```

I hope someone can help.
Thanks!

Kris

---

### Post by Scormen on 2009-05-31
I found that if I do a local sync, everything goes fine.
But if I do a remote sync, it copies only 4.6MB.

Any idea?

---

### Post by LoneWolfJack on 2009-05-31
never used rsync on a remote machine, but "sudo rsync" looks wrong. you probably can't call sudo like that so the ssh connection needs to have the proper privileges for executing rsync.

just an educated guess, though.

---

### Post by Scormen on 2009-05-31
Thanks for your answer.

In /etc/sudoers I have added next line, so "sudo rsync" will work.
```
kris ALL=NOPASSWD: /usr/bin/rsync
```

I also tried without **--rsync-path="sudo rsync"**, but without success.

I have also tried on the server to pull the files from the laptop, but that doesn't work either.

---

### Post by LoneWolfJack on 2009-05-31
in the rsync help file it says that --rsync-path is for the path to rsync on the remote machine, so my guess is that you can't use sudo there as it will be interpreted as a path.

so you will have to do --rsync-path="/path/to/rsync" and make sure the ssh login has root privileges if you need them to access the files you want to sync.

--rsync-path="sudo rsync" probably fails because
a) sudo is interpreted as a path
b) the space isn't escaped
c) sudo probably won't allow itself to be called remotely

again, this is not more than an educated guess.

---

### Post by Scormen on 2009-05-31
I understand what you mean, so I tried also:

```
rsync -Cavuhzb --rsync-path="/usr/bin/rsync" -e "ssh -i /root/.ssh/backup" /etc kris@192.168.1.3:/home/kris/backup/laptopkris
```

Then I get this error:
> sending incremental file list
rsync: recv_generator: failed to stat "/home/kris/backup/laptopkris/etc/chatscripts/pap": Permission denied (13)
rsync: recv_generator: failed to stat "/home/kris/backup/laptopkris/etc/chatscripts/provider": Permission denied (13)
rsync: symlink "/home/kris/backup/laptopkris/etc/cups/ssl/server.crt" -> "/etc/ssl/certs/ssl-cert-snakeoil.pem" failed: Permission denied (13)
rsync: symlink "/home/kris/backup/laptopkris/etc/cups/ssl/server.key" -> "/etc/ssl/private/ssl-cert-snakeoil.key" failed: Permission denied (13)
rsync: recv_generator: failed to stat "/home/kris/backup/laptopkris/etc/ppp/peers/provider": Permission denied (13)
rsync: recv_generator: failed to stat "/home/kris/backup/laptopkris/etc/ssl/private/ssl-cert-snakeoil.key": Permission denied (13)

sent 86.85K bytes  received 306 bytes  174.31K bytes/sec
total size is 8.71M  speedup is 99.97
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1058) [sender=3.0.5]


And the same command with "root" instead of "kris".
Then, I get no errors, but I still don't have all the files synced.

---

### Post by Scormen on 2009-06-01
Sorry for this bump.
I'm still having the same problem.

Any idea?

Thanks.

---

### Post by binary10 on 2009-06-01
> **Scormen said:**
> I understand what you mean, so I tried also:

```
rsync -Cavuhzb --rsync-path="/usr/bin/rsync" -e "ssh -i /root/.ssh/backup" /etc kris@192.168.1.3:/home/kris/backup/laptopkris
```

Then I get this error:



And the same command with "root" instead of "kris".
Then, I get no errors, but I still don't have all the files synced.

Maybe there's a nicer way but you could place /usr/bin/rsync into a private protected area and set the owner to root place the sticky bit on it and change your rsync-path argument such like:

```

# on the remote side, aka kris@192.168.1.3
mkdir priv-area
# protect it from normal users running a priv version of rsync
chmod 700 priv-area
cd priv-area
cp -p /usr/local/bin/rsync ./rsync-priv
sudo chown 0:0 ./rsync-priv
sudo chmod +s ./rsync-priv
ls -ltra # rsync-priv should now be 'bold-red' in bash

```


Looking at your flags, you've specified a cvs ignore factor, ignore  files that are updated on the target, and you're specifying a backup of removed files.

```
rsync -Cavuhzb --rsync-path="/home/kris/priv-area/rsync-priv" -e "ssh -i /root/.ssh/backup" /etc kris@192.168.1.3:/home/kris/backup/laptopkris
```


From those qualifiers you're not going to be getting everything sync'd. It's doing what you're telling it to do.


If you really wanted to perform a like for like backup.. (not keeping stuff that's been changed/deleted from the source. I'd go for something like the following.

```

 rsync --archive --delete --hard-links --one-file-system --acls --xattrs --dry-run -i --rsync-path="/home/kris/priv-area/rsync-priv" --rsh="ssh -i /root/.ssh/backup" /etc/ kris@192.168.1.3:/home/kris/backup/laptopkris/etc/
```

Remove the --dry-run and -i when you're happy with the output, and it should do what you want. A word of warning, I get a bit nervous when not seeing trailing (/) on directories as it could lead to all sorts of funnies if you end up using rsync on softlinks.

---

### Post by Scormen on 2009-06-01
Thanks for your help, binary10.

I've tried what you have said, but still, I only receive 4.6MB on the remote server.
Thanks for the warning, I'll not that!

Did someone already tried to rsync their own /etc to a remote system? Just to know if this strange thing only happens to me...

Thanks.

---

### Post by binary10 on 2009-06-01
> **Scormen said:**
> Thanks for your help, binary10.

I've tried what you have said, but still, I only receive 4.6MB on the remote server.
Thanks for the warning, I'll not that!

Did someone already tried to rsync their own /etc to a remote system? Just to know if this strange thing only happens to me...

Thanks.

Ok so I've gone back and looked at your original post, how are you calculating 15MB of data under etc - via a du -hsx /etc/  ??


I do daily drive to drive backup copies via rsync and drive to network copies.. and have used them recently for restoring.


Sure my du -hsx /etc/ reports 17MB of data of which 10MB gets transferred via an rsync.  My backup drives still operate. 

rsync 3.0.6 has some fixes to do with ACLs and special devices rsyncing between solaris. but I think 3.0.5 is still ok with ubuntu to ubuntu systems.

Here is my test doing exactly what you you're probably trying to do. I even check the remote end..

```

binary10@jsecx25:~/bin-priv$ ./rsync --archive --delete --hard-links --one-file-system --stats --acls --xattrs --human-readable --rsync-path="~/bin/rsync-priv-os-specific" --rsh="ssh" /etc/ rsyncbck@10.0.0.21:/home/kris/backup/laptopkris/etc/

Number of files: 3121
Number of files transferred: 1812
Total file size: 10.04M bytes
Total transferred file size: 10.00M bytes
Literal data: 10.00M bytes
Matched data: 0 bytes
File list size: 109.26K
File list generation time: 0.002 seconds
File list transfer time: 0.000 seconds
Total bytes sent: 10.20M
Total bytes received: 38.70K

sent 10.20M bytes  received 38.70K bytes  4.09M bytes/sec
total size is 10.04M  speedup is 0.98

binary10@jsecx25:~/bin-priv$ sudo du -hsx /etc/
17M	/etc/
binary10@jsecx25:~/bin-priv$ 

```

And then on the remote system I do the du -hsx 

```

binary10@lenovo-n200:/home/kris/backup/laptopkris/etc$ cd ..
binary10@lenovo-n200:/home/kris/backup/laptopkris$ sudo du -hsx etc
17M	etc
binary10@lenovo-n200:/home/kris/backup/laptopkris$ 



```

---

### Post by Scormen on 2009-06-01
> ow are you calculating 15MB of data under etc - via a du -hsx /etc/ ??
Indeed, on my laptop I see:

> root@laptopkris:/home/kris# du -sh /etc/
15M	/etc/


If I do the same thing after a fresh sync to the server, I see:
> root@server:/home/kris# du -sh /home/kris/backup/laptopkris/etc/
4.6M	/home/kris/backup/laptopkris/etc/


On both sides, I have installed Ubuntu 9.04, with version 3.0.5 of rsync.
So strange...

---

### Post by binary10 on 2009-06-01
it does seem a bit odd.

I'd start doing a few diffs from the outputs find etc/ -printf "%f %s %p %Y\n" | sort 

And see what type of files are missing.

- edit - Added the %Y file type.

---

### Post by Scormen on 2009-06-01
Hmm, it's going stranger.
Now I see that I have all my files on the server, but they don't have their full size (bytes).

I have uploaded the files, so you can look into them.

Laptop: [http://www.linuxontdekt.be/files/laptop.files](http://www.linuxontdekt.be/files/laptop.files)
Server: [http://www.linuxontdekt.be/files/server.files](http://www.linuxontdekt.be/files/server.files)

---

### Post by binary10 on 2009-06-01
If you look at the files that are different aka the ssl's they are  links to local files else where aka linked to /usr  and not within /etc/

aka they are different on your laptop and the server

---

### Post by Scormen on 2009-06-01
I understand that soft links are just copied, and not the "full file".

But, you have run the same command to test, a few posts ago.
How is it possible that you can see the full 15MB?

---

### Post by binary10 on 2009-06-01
I was starting to think that this was a bug with du.

The de-referencing is a bit topsy.

If you rsync copy the remote backup back to a new location back onto the laptop and do the du command. I wonder if you'll end up with 15MB again.

---

### Post by Scormen on 2009-06-01
Good tip.

On the server side, the backup of the /etc was still 4.6MB.
I have rsynced it back to the laptop, to a new directory.

If I go on the laptop to that new directory and do a du, it says 15MB.

---

### Post by binary10 on 2009-06-01
> **Scormen said:**
> Good tip.

On the server side, the backup of the /etc was still 4.6MB.
I have rsynced it back to the laptop, to a new directory.

If I go on the laptop to that new directory and do a du, it says 15MB.

I think you've now confirmed that RSYNC DOES copy everything.. just tht du confusing what you had expected by counting the end link sizes.

It might also think about what you're copying, maybe you need more than just /etc of course it depends on what you are trying to do with the backup :) 

enjoy.

---

### Post by Scormen on 2009-06-01
Yeah, it seems to work well.
So, the "problem" where just the soft links, that couldn't be counted on the server side?

---

### Post by binary10 on 2009-06-01
> **Scormen said:**
> Yeah, it seems to work well.
So, the "problem" where just the soft links, that couldn't be counted on the server side?

The links were copied as links as per the design of the --archive in rsync.

The contents of the pointing links were different between your two systems. These being that that reside outside of /etc/ in /usr And so DU reporting them differently.

---

### Post by Scormen on 2009-06-01
Okay, I got it.
Many thanks for the support, binarty10!

---

### Post by Scormen on 2009-06-01
Just to know, is it possible to copy the data from these links as real, hard data?
Thanks.

---

### Post by binary10 on 2009-06-02
> **Scormen said:**
> Just to know, is it possible to copy the data from these links as real, hard data?
Thanks.

Yep absolutely

You should then look at other possibilities of:
```

 -L, --copy-links            transform symlink into referent file/dir
     --copy-unsafe-links     only "unsafe" symlinks are transformed
     --safe-links            ignore symlinks that point outside the source tree
 -k, --copy-dirlinks         transform symlink to a dir into referent dir
 -K, --keep-dirlinks         treat symlinked dir on receiver as dir

```

 but then you'll have to start questioning why you are backing them up like that especially stuff under /etc/. If you ever wanted to restore it you'd be restoring full files and not symlinks the restore result could be a nightmare as well as create future issues (upgrades etc) let alone your backup will be significantly larger, could be 150MB instead of 4MB.

---

### Post by Scormen on 2009-06-02
Okay, now I'm sure what its doing :)
Is it also possible to show on a system the "real disk usage" of e.g. that /etc directory? So, without the links, that we get a output of 4.6MB.

Thank you very much for your help!

---

### Post by binary10 on 2009-06-02
What does the following respond with.

```

 sudo du --apparent-size -hsx /etc

```

If you want the real answer then your result from a dry-run rsync will only be enough for you.

```

 sudo rsync --dry-run --stats -h --archive /etc/ /tmp/etc/

```

---

