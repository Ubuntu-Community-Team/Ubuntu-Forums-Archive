---
title: "Reliable, simple backup and restore"
date: 2009-02-09
forum: General Help
---

### Post by Midahed on 2009-02-09
I hope stepheny won't mind me resurrecting his excellent post from a thread that now resides in the read-only section of the forum....

I've been trying to use this method for backing-up my system, but have run into a problem.

I've been following stepheny's method exactly as described in the original thread, which is here - [http://ubuntuforums.org/showthread.php?t=617771](http://ubuntuforums.org/showthread.php?t=617771)

[QUOTE=steheny]

**Simple system backup that works.**

Having recently been let down by mondorestore in Gutsy I have been researching a new backup strategy. I didn't want to leave myself again trusting in a tool which lets you down when you really need it, so the strategy had to use readily available and trustworthy software. The solution I have decided upon and tested by doing several complete restores is as follows:

**Backing up.**

Firstly you need to copy your home directory using sudo grsync (preserve time, owner, permissions and group) or

```
sudo rsync -r -t -p -o -g -v --progress -l /home/ /media/disk/home/
```

Keep a copy of this somewhere so that you can find it when your system dies, ie on an external drive. Sync it regularly, rsync will only update changes to the original so after the first copy has been made, updates usually only require a few seconds.

Then make a list of all of the packages in your installation using the command

```
sudo dpkg --get-selections | grep '[[:space:]]install$' | \awk '{print $1}' > package_list
```

Copy this file together with /etc/apt/sources.list to the same medium you have used for your /home/ directory backup.

You could initiate a cron job to keep this list up-to-date using by putting the following script in /etc/cron/dailypackage_list and making it executable.

```
#!/bin/sh
sudo dpkg --get-selections | grep '[[:space:]]install$' | \awk '{print $1}' > package_list
```

**Restoring.**

First boot the live cd and install Ubuntu.

After Ubuntu has rebooted to the HD version set up the restricted drivers for your graphics card if applicable, there is no need to reboot yet. Then replace the existing sources list with the one from your lost system. assuming that it is on an external disk (together with the /home/ directory backup) you would use

```
sudo mv /media/disk/sources.list /etc/apt/sources.list
sudo apt-get update
```

Then update the packages using:

```
cat /media/disc/package.list | xargs sudo apt-get install

```
If you are using some unauthorized packages you will get the following warning

"WARNING: The following packages cannot be authenticated!
libxxx libxx libx xxxplayer
skype-common skype xxxcodecs
Install these packages without verification [y/N]? E: Some packages could not be authenticated"

for some reason you cannot answer yes or no to this, it's a bug. So simply install all of these packages using

```
sudo apt-get install libxxx libxx libx xxxplayer skype-common skype xxxcodecs
```

When that has completed run

```
cat /media/disc/package.list | xargs sudo apt-get install
```

again and this time it should complete without problems.

Now copy your /home directory to the new system using sudo grsync (preserve time, owner, permissions and group) or

```
sudo rsync -r -t -p -o -g -v --progress -l /media/disk/home/ /home/
```

That's it! You need to reboot and your system should be exactly as it was. I have tested this three times without problems.[/QUOTE]

I've tested this under 8.04 LTS using two separate PCs.  I made a backup of /home from my main PC onto a USB drive and attempted to restore it onto a clean 8.04 LTS installation on my other PC.

The data looks like it's all restored OK, but the restored system is not, as stepheny claims, "exactly as it was".

When I update the packages with

```
cat /media/disk/package.list | xargs sudo apt-get install
```

I found that it reported that numerous packages wouldn't be installed - apparently due to dependency failures.  It didn't even restore kubuntu-desktop!

Initially I had tried to use this procedure to move my data from 8.04 to 8.10, but when it failed I concluded that it was only intended to work when restoring to the same version of Ubuntu.  However, my later attempts using 8.04 on both the backup and restore PCs have failed in the same way.

Am I missing something fundamental that maybe wasn't documented in stepheny's original post?

Mike

---

### Post by Midahed on 2009-02-12
Bump.

Anyone got any ideas on this?

---

