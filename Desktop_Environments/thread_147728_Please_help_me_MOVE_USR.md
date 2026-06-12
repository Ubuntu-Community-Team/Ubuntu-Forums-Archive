---
title: "Please help me MOVE /USR"
date: 2006-03-20
forum: Desktop Environments
---

### Post by stabface on 2006-03-20
Hi I want to move my /usr to the home partition it is taking a lot of room on my / partition which is almost full. what do i need to do and am i going to break anything if i do that?

---

### Post by cilynx on 2006-03-20
This is a pretty ugly proposition you're looking at.  The "easiest" way I can see would be to "cp -r" your real /usr to /home/usr then "ln -s" the newly created /home/usr to /usr.  Rename your original /usr to something like /usr.old before making the symlink.  Make sure you do all of this with as little running on the machine as possible.  Single user mode is prefered.  Once you know things are running properly with the symlink established, you can rm your backup /usr.old.  Just to make sure this is the best route, what's your 'df' look like?

---

### Post by stabface on 2006-03-22
here is my df

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hdb1              3842376   3328864    318324  92% /
tmpfs                   388276         0    388276   0% /dev/shm
tmpfs                   388276     12588    375688   4% /lib/modules/2.6.12-10-386/volatile
/dev/hdb3             70769848   1949936  65224968   3% /home
/dev/hda2             20472848    682816  19790032   4% /media/hda2


I don't want anything to get messed up. is it going to be risky? 
could you explain the details a little clearer. I have been using linux for a while but nothing too extreme

---

### Post by aysiu on 2006-03-22
It is dangerous.

Theoretically, if done correctly, it should work, but I would create yet another partition (carved out of your /home partition) instead of placing it *with* your /home partition.

The best way to do this would be:

1. Back up your essential data
2. Boot a live CD (preferably something like Knoppix--though, you can use the Ubuntu live CD, too, but you might have to do some mounting from the command-line)
3. Use QTParted (of GParted or DiskDrake) to resize your /home partition and create a new partition
4. Mount your Ubuntu partition and the new partition. Copy over the entire contents of your /usr directory to that new partition. You'll need to do this as root. Then delete the old /usr directory.
5. Edit your Ubuntu's /etc/fstab file (also needs to be edited as root) to include a line that's something like ```
/dev/hdb5 /usr ext3 defaults 0 0
``` This assumes, of course, that your new partition is /dev/hdb5. It may be /dev/hdb4.
6. Save and reboot without the live CD.

---

### Post by GeneralZod on 2006-03-22
Before trying anything risky like this, you might want to look into the /var/cache/apt/archives directory for all of the *.deb files that have been downloaded since you installed.  You should be able to safely delete all of these and maybe free up some space.

---

### Post by cilynx on 2006-03-22
Speaking as a non-forum-god, what aysiu said makes the most sense to me.  When you finish that process, you have a properly setup system again as opposed to a hack which is what you would have following my initial directions.  (I'm a little too used to the hack method...it's amazing my production machines continue to run.)

---

### Post by towsonu2003 on 2006-03-22
[QUOTE=aysiu]
4. Mount your Ubuntu partition and the new partition. Copy over the entire contents of your /usr directory to that new partition. You'll need to do this as root. Then delete the old /usr directory.[/QUOTE]
Is this done with cp -r /bla? If so, will the existing symlinks and permissions will be transferred to the new location? if not, using tar would be better? (as in: tar usr, copy tar, untar archive -> these are not commands)

---

### Post by aysiu on 2006-03-22
You're right, townsonu2003. Tarring might be better for moving it over than copying. I guess it depends how many symlinks there are.

---

### Post by stabface on 2006-03-23
ok, I can do all of that with out a problem i think, Before i start i only want to be sure on what command i should use. what would be the best command line command to copy the own the whole dir?

---

### Post by towsonu2003 on 2006-03-23
[QUOTE=stabface]ok, I can do all of that with out a problem i think, Before i start i only want to be sure on what command i should use. what would be the best command line command to copy the own the whole dir?[/QUOTE]
I believe ```
sudo tar -cvf usr.tar /usr
```
but check out ```
man tar
``` bc I don't have breezy here and can't check it out myself (bad memory guy here)..

also, I believe tar has a feature that allows you to compare the dir and the tar contents. again, man tar ;)

PS. you did your backups right? .....

---

### Post by Ramses de Norre on 2006-03-23
Doesn't cp -r --preserve=all keep permissions? (seems easier as using tar)

---

### Post by towsonu2003 on 2006-03-23
[QUOTE=Ramses de Norre]Doesn't cp -r --preserve=all keep permissions? (seems easier as using tar)[/QUOTE]
not sure (can't read the man page in windows ;) ) but there may be problems with symlinks...

---

