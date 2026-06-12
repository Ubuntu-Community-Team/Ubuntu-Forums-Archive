---
title: "ext4 option &quot;data=writeback&quot; makes breaks my system"
date: 2009-04-07
forum: General Help
---

### Post by latebeat on 2009-04-07
Hi there,
I'm new to linux so please forgive me if my questions are kinda "naive" or stupid!
I've read an article on how to speed-up ext4 by using the following options when mounting:
```
defaults,data=writeback,noatime,barrier=0,extents,journal_checksum
```
This is just a test pc, not my main pc so I don't mind the instability issues or the consequences of enabling writeback cache.
All other options work fine however when I add data=writeback in the /etc/fstab for my root partition the system doesn't boot with the following error:
```
Could not start the X server due to some internal error. blabla, please restart gdm when the problem is corrected
```

Any ideas on how to correct this and enable writeback cache?

---

### Post by latebeat on 2009-04-07
wow can't believe how popular ubuntu forums are! In just a couple of hrs my thread went to page 6!

---

### Post by sdennie on 2009-04-07
Are you sure the two are related?  If you tried to mount root with the wrong journal mode, you have problems very early (much earlier than trying to start gdm).  Or, possibly, you've already run into the infamous ext4 bug where it zeros out files on a crash and some needed file has been zeroed.

---

### Post by ibuclaw on 2009-04-07
I second sdennie, it looks more like you are having a display driver issue, than a filesystem issue.

Are you able to login via the console? Press **Alt+Ctrl+F1** and login with your name and password.

Then type in:
```
sudo shutdown now
```
You'll reach a new screen with several options.

Choose the one that says "**Fix X**". Then select the "**Continue with Normal Boot**".

Regards
Iain

---

### Post by 67GTA on 2009-04-24
I can confirm this with fresh Jaunty install using ext4. I added data=writeback to fstab for my root partition, and got the same error at next boot. Removed using recovery mode with nano, and booted normally afterwards.

---

### Post by eurgain on 2009-04-28
The problem is, that you cannot just add data=writeback to your fstab entry and expect everything to work well.

If you look at your logs, you will see that the system complains when mounting the root fs because it cannot change the journaling model by itself.  It mounts the fs read-only, and it just happens that it is X that is the first process in the normal bootup sequence that throws a complete wobbly on account of this.

You need to use tune2fs to change the journal if you really want to do this.  With the root partition mounted readonly (e.g., after one of your failed boot attempts -- but MAKE SURE IT IS RO) do:

# tune2fs -o journal_data_writeback /dev/sdXY

(where sdXY is the partition of interest)

Then, reboot, and all should work.

Look at my /etc/fstab for a system based on an ssd and you will see that it *can* work.

```
eurgain@juno:~$ cat /etc/fstab
UUID=57db94de-99f2-227a-83fe-3ca75c4d7f6e /               ext4    noatime,barrier=0,data=writeback,nobh,commit=100,nouser_xattr 0       1
/swapfile	none	swap	sw	0	0
tmpfs   /var/log    tmpfs   defaults,noatime,size=5M   0   0

fuchsia:/home   /mnt/fuchsia/home       nfs     bg,retry=20 0 0
```

A

---

### Post by 67GTA on 2009-04-28
Okay, now I feel like an idiot:oops: This how to still applies to ext4. [http://ubuntuforums.org/showthread.php?t=107856](http://ubuntuforums.org/showthread.php?t=107856)

---

