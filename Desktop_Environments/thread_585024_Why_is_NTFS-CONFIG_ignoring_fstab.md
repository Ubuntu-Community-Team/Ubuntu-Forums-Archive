---
title: "Why is NTFS-CONFIG ignoring fstab"
date: 2007-10-21
forum: Desktop Environments
---

### Post by raulb on 2007-10-21
Rant Alert: Why is ntfs config ignoring fstab? I am getting all my ntfs partitions mounted automatically which I don't want or need and removing the entries from fstab has absolutely no impact, so whats the purpose of fstab in Ubuntu?

 If Ubuntu is going change things and have things being auto mounted from scripts in hal and god knows where at least document the way for people to enable/disable the automounts. Now I have to spend time I don't have to figure out how Ubuntu has set up the automount to disable it. This is just so unnecessary. Can someone more clued in to the way Ubuntu is setting this automount system up tell me how I can disable my ntfs partitions from mounting? I have just spent an hour searching google and this forum looking but with little result. Thanks.

---

### Post by benerivo on 2007-10-21
You have probably seen this already, but have you tried the noauto option in fstab as described [here]("http://www.tuxfiles.org/linuxhelp/fstab.html")?

---

### Post by raulb on 2007-10-21
Yup, tried that quite some time ago, Ubuntu is ignoring fstab altogether so whatever I do there doesn't matter much, do noauto or delete the ntfs entries altogether has zero effect, the ntfs drives keep on being automounted. I think I am going to uninstall ntfs-config and see if that resolves the problem.

---

### Post by benerivo on 2007-10-21
Uninstalling should work. I'm on gutsy and fstab keeps control of my ntfs mount, and my other ntfs partition does not get mounted automatically but it can be mounted manually from nautilus. With ntfs read/write built in to gutsy, the format of partitions (ntfs or otherwise) seems largely irrelevant.

---

### Post by raulb on 2007-10-21
This is ridiculous, I uninstalled ntfs-config and yet like a bad dream the ntfs drives are still automounting, there are no ntfs drives n my fstab, ntfs-config is uninstalled so no hal policies either. please ubuntu experts tell me what is controlling the mount so I can go and fix it.

---

### Post by benerivo on 2007-10-21
Try looking in /etc/mtab for an entry relating to the ntfs drives.

---

### Post by raulb on 2007-10-21
Hey, I always thought mtab reflected fstab, but I discovered entries for all my ntfs drives on it, am going to delete them right away and reboot and see. So here's an update of what's happened so far: 

A simple task of disabling ntfs drives from automounting, you would think Ubuntu by far the best linux distribution would make this simple but no:

1. Add noauto to fstab - fail
2. Delete ntfs entries from fstab - fail
3. Delete ntfs policy from /etc/hal/ - fail
4. Uninstall ntfs-config - fail
5. Delete mtab entries - will justl reboot and see....

---

### Post by raulb on 2007-10-21
This is highly frustrating, surely somebody will have a answer to what should be a trivial issue, mounting and unmounting disks of your choice which is something fstab did very well. The mtab thing didn't work.

Surely Ubuntu folks should document if they are deprecating fstab so we can get things done without wasting so much time and effort. This is really my first sad experience on Linux after a very long time, usually research and persistence pays off but this is trivial issue and if its taking a person who is fairly familiar with Linux so much time there is something wrong.

---

### Post by raulb on 2007-10-21
hey this is so strange, I am drawing a blank everywhere, there seems to be no info anywhere on this.  I just can't disable ntfs mounting on its own. I need the flexibility but I think I have no choice but to uninstall ntfs-3g. Hopefull then fstab will able to control which drives get mounted.

---

