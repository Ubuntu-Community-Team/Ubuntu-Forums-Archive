---
title: "rsync question"
date: 2009-04-29
forum: General Help
---

### Post by HyperX on 2009-04-29
I have this new buffalo terrastation with 3 terabytes of storage. When I ran a port scan against it, I noticed that it had the rsync port open. So when i ran rsync rsync://192.168.0.7 against it, it showed me a folder called array1_backup. So for the hell of it, I ran my backup job against it. It went fine. So now there is a new folder in there called array1_backup\dan\ with all my stuff (over 5 gigs with music, etc). So since I am new to rsync, and I can't just browse to that folder in any way that I know, how do I get my backup back if I need it? Lets say I only need 4 files and not the entire thing. Anyone know?

Is there a way to browse an rsync share?

---

### Post by Kareeser on 2009-04-29
You can treat rsync like a synchrnoizing command. It can work practically anywhere there's a connection... between two directories in a single partition, to two directories across the world.

I've never tried "browsing" an rsync share, but you can push and pull data off of it with the rsync command.

For example, if you wanted to pull your music back over, run this command:

```
rsync -avz rsync://192.168.0.7/array1_backup/dan/ ~
```

It would check the files in your home directory and update any files that are newer on the NAS device.

---

### Post by StuartN on 2009-04-29
> **HyperX said:**
> Is there a way to browse an rsync share?

I use a Buffalo Linkstation with multiple computers that backup and share data through rsync. On the Buffalo I set up "path = /mnt/disk1/Stuart/" in /etc/rsyncd.conf so that I can rsync to a directory within my own share, rather than use the predefined backup. You could probably achieve the same effect by logging in to the Buffalo and creating a symbolic link (ln -s backupdir) to your backup directory within your share, assume the users and permissions are okay.

---

### Post by HyperX on 2009-04-29
> **StuartN said:**
> I use a Buffalo Linkstation with multiple computers that backup and share data through rsync. On the Buffalo I set up "path = /mnt/disk1/Stuart/" in /etc/rsyncd.conf so that I can rsync to a directory within my own share, rather than use the predefined backup. You could probably achieve the same effect by logging in to the Buffalo and creating a symbolic link (ln -s backupdir) to your backup directory within your share, assume the users and permissions are okay.

You know what... i can't telnet into my buffalo to hack it as per instructions. Even with a port scan, port 23 is closed. On all 3 of my terras. Any ideas there? I used that acp_commander thingy, and it worked but could not telnet to do the rest.

---

### Post by StuartN on 2009-04-29
> **HyperX said:**
> You know what... i can't telnet into my buffalo to hack it as per instructions. Even with a port scan, port 23 is closed. On all 3 of my terras. Any ideas there? I used that acp_commander thingy, and it worked but could not telnet to do the rest.

As far as I can see, the instructions for gaining telnet on the Terastation are different from the Linkstation. There are details and telnet-enabled firmware here: [http://homepage.ntlworld.com/itimpi/buffalo.htm#TERA_ORIG](http://homepage.ntlworld.com/itimpi/buffalo.htm#TERA_ORIG)

Once you have telnet, you can configure anything else you want.

---

