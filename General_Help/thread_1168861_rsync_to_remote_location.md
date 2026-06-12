---
title: "rsync to remote location"
date: 2009-05-24
forum: General Help
---

### Post by dbrine on 2009-05-24
I have 2 server and I want to rsync directories/ files from multiple hard drives on server 1 to multiple hard drives on server 2. Can someone point me in the right direction?


I also know that I need to setup ssh with a blank password so it doesn't prompt me during the backup but what about the ssh I already setup to remote into the boxes? While the blank password one overwrite the one for remote access?

---

### Post by Kareeser on 2009-05-25
You're looking for the "e" switch in rsync. It allows you to tunnel rsync through SSH, for example.

To answer your second question:
[http://ubuntu.kareeser.com/?p=36](http://ubuntu.kareeser.com/?p=36)

---

### Post by XCan on 2009-05-25
> **dbrine said:**
> I have 2 server and I want to rsync directories/ files from multiple hard drives on server 1 to multiple hard drives on server 2. Can someone point me in the right direction?


I also know that I need to setup ssh with a blank password so it doesn't prompt me during the backup but what about the ssh I already setup to remote into the boxes? While the blank password one overwrite the one for remote access?

You can manually specify which dirs goes where on the backup station using multiple rsync commands. Don't know if you were looking for some automated distribution way, like raid?

Regarding the ssh issue, do you really want to remove the ssh password?! I would strongly recommend that you use the ssh keyfiles instead. For example when I rsync down my workstation I use the keyfile in the following way (you can specify an alternate ssh port with the -p flag):
```
rsync -avz --progress --delete --rsh="ssh -p22 -i /path/to/ssh/key/rsync-ssh-key" user@host.location /local/path/to/be/backed/up/to
```

---

### Post by dbrine on 2009-05-25
thanks for the great replies. Is there a good tutorial for rsync? I definitely don't want a blank password SSH key. Also Xcan, what would the full command be to back up to a remote location?

[HTML]rsync -avz --progress --delete --rsh="ssh -p22 -i /path/to/ssh/key/rsync-ssh-key" user@host.location /local/path/to/be/backed/up/to
[/HTML]

Where is the directory you are backing up? I see the destination. what is -p22?

---

### Post by XCan on 2009-05-25
> **dbrine said:**
> thanks for the great replies. Is there a good tutorial for rsync? I definitely don't want a blank password SSH key. Also Xcan, what would the full command be to back up to a remote location?

[HTML]rsync -avz --progress --delete --rsh="ssh -p22 -i /path/to/ssh/key/rsync-ssh-key" user@host.location /local/path/to/be/backed/up/to
[/HTML]

Where is the directory you are backing up? I see the destination. what is -p22?

Actually, when I started with rsync I was too looking for some easy tutorial summing up the useful flags and such. I wasn't too successful and ended up just looking at some code examples at [http://www.samba.org/rsync/examples.html](http://www.samba.org/rsync/examples.html) and putting the pieces together with the man page at [http://www.samba.org/ftp/rsync/rsync.html](http://www.samba.org/ftp/rsync/rsync.html) . :)

Let me explain the incomprehensible flags a bit. First of all -p22 just tells ssh to use port 22, of course the default port is 22, but since I changed my ssh port I thought it might be good for reference to show how one would proceed for other ports.

The easiest case scenario we can imagine is you running rsync locally on your computer. Say that you want to backup /home/me/important to /media/backup/ you would simply run
```
rsync -avz /home/me/important /media/backup/
```
where, -a stands for archive mode (preserves timestamp ownerships etc), -v verbose mode, -z compression during transfer (doesn't really make sense on backups locally but is quite useful if done over the internet).

Now, since we want to backup from a remote location using ssh and an ssh keyfile (so that we don't need to enter our password every time) our syntax gets lots messier, but the basic principle is the same, where we state the source location first, and the destination second. As an example, we have a dir in /home/me/important on a remote machine (127.0.0.1) we want to backup into a local machine /media/backup using ssh, we would write

```
rsync -avz --rsh="ssh -p22 -i /path/to/ssh/key/rsync-ssh-key" me@127.0.0.1 /media/backup
```

Notice that in my previous post I added the flags --progress and --delete. --progress is quite self explanatory, --delete simply tells us that in case the remote machine has deleted some files since we last backed it up, we would like to delete it on our local machine as well. The only thing that I haven't explained is how to generate ssh keys, but I feel there are guides that are much more comprehensible than anything I can whip up here, a good starting point could, for example, be [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) .

---

### Post by dbrine on 2009-05-27
XCan,

  I already have a ssh key that I use to remote into the system. I created another key but I still get prompted for a pass phrase??

---

### Post by Kareeser on 2009-05-27
You most likely did it wrong. Make sure the key is generated from the computer who's doing the connecting, and not the other way around.

Follow my link: [http://ubuntu.kareeser.com/?p=36](http://ubuntu.kareeser.com/?p=36)

---

### Post by dbrine on 2009-05-27
Dumb question.... How many keys can I have? Can I use the rsync ssh key just for rsync and my normal SSH key for remote access?

---

### Post by Kareeser on 2009-05-27
I believe the key is assigned on a per-user basis. So if you export a key from one account, any ssh connections to the host will be passwordless.

If you want to limit it to rsync only, you could potentially create a new user just for backups or whatnot.

There may be a more elegant solution out there...

---

