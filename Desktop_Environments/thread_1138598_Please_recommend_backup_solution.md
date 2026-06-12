---
title: "Please recommend backup solution"
date: 2009-04-26
forum: Desktop Environments
---

### Post by srdjo on 2009-04-26
I have setup ubuntu 8.10, LTSP and MySQL.

Now I need a backup solution. Something that would allow me to restore all settings and files as they were last time it was backed up in less then an hour.

I must backup these things:

*mySQL databases
*LTSP settings and images
*HOME directory and all files in it
*any other folder that might be needed

In Windows, I would just use Acronis, Norton Ghost or something like that, but I dont know about any software like these for linux. (That can be booted from CD and restore from image)

Computer has RAID mirroring setup with two disks, and I created a separate partition called Backup just for backup.

What do you recommend ?

---

### Post by hictio on 2009-04-26
Take a look at [Rsnapshot](http://www.rsnapshot.org/), free, super easy to install & setup. And, of course, it's on the repositories, so install it is a piece of cake.
To make 1 hour snapshots, edit the /etc/rsnapshot.conf filem and set the interval directive to:

```

interval       hourly  1

```

Then add the crontab entry to run every hour, remember to separate the values on the config file using tabs!

---

### Post by srdjo on 2009-04-26
Can it also backup mysql databases ?

---

### Post by hictio on 2009-04-26
It can backup whatever the hell you want to :)
Take a look at the docs/ FAQ on the site, there are examples, also (if you choose to install it), there is a sample config file.

---

