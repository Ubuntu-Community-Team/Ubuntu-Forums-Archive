---
title: "Configuration file &quot;/home/user/.config/konsolerc&quot; not writable. Please contact your"
date: 2018-12-21
forum: Desktop Environments
---

### Post by a_guenther on 2018-12-21
Hi,
I get suddenly on Kubuntu 18.10 the error message "Configuration file "/home/anton/.config/konsolerc" not writable.
Please contact your system administrator." (anton = username) This is just an example for the terminal, similar for opening Dolphin and others.

I checked already ls -l, it looks writable to me:
```
anton@anton-ThinkPad-T540p:~$ ls -l /home/anton/.config/konsolerc
-rw------- 1 anton anton 350 Dec 19 19:50 /home/anton/.config/konsolerc

```

Also if I look at the permission in Dolphin for everything in the .config folder, all seem both read and writable for user anton. Any idea?

I think I had earlier this week the same problem on 18.04, reboot led me into emergency mode (solved here: [https://ubuntuforums.org/showthread.php?t=2408538](https://ubuntuforums.org/showthread.php?t=2408538) ). I updated to 18.10, it worked for a 1-2 days, now I get the same error. If I would reboot, I might get again the previous problem, haven't tried yet.
In between working and not working I got some updates, not sure if they caused it...

Any idea what's happening?

---

### Post by a_guenther on 2018-12-21
Actually, did dmesg now and get quite a few error messages, among others:

```
[27658.241131] EXT4-fs error (device sda9): ext4_journal_check_start:61: Detected aborted journal
[27658.241141] EXT4-fs (sda9): Remounting filesystem read-only

```

sda9 is my /home. So if this is mounted read-only, I could not write... How to fix this? And how did it get there?

---

### Post by CatKiller on 2018-12-21
You should probably run fsck on that drive.

---

### Post by a_guenther on 2018-12-21
That's what I thought, but I'm not 100% sure how. Doing straight away fsck /dev/sda9 warns me of damage since it is mounted.
sudo umount /home gives me "in use", so I can't unmount and therefore not run fsck right now. Is through a live system the only way?

---

### Post by CatKiller on 2018-12-21
Through a live system is easiest. There may be a way to tell it to run fsck on the next boot, but I only know how to do that for the / partition, and that wouldn't work if you can't write to the partition anyway.

---

### Post by a_guenther on 2018-12-22
Restarted, and as expected was in emergency mode. From there I was able to run fsck sucessfully. For not it works again.
What worries me that this is the second time in 3 days this partition had an error, so I wonder what causes this...

---

### Post by CatKiller on 2018-12-22
Glad to hear it's working again. 
> **a_guenther said:**
> What worries me that this is the second time in 3 days this partition had an error, so I wonder what causes this...
That sounds like imminent hardware failure. Back up your suff.

---

### Post by a_guenther on 2018-12-22
I do it right now, the last bits which were not before. The laptop's harddrive is now 4 years, so this could be for sure the end of its life (would be the first harddrive failing for me though, the last laptop's went over 8 years, just the laptop itself fell apart).

Is that it happens in the same partition a sign towards it? Or just random?

---

### Post by CatKiller on 2018-12-22
> **a_guenther said:**
> Is that it happens in the same partition a sign towards it? Or just random?

No idea. If it's your /home partition it could feasibly have different access patterns to the other partitions.

---

### Post by oldfred on 2018-12-22
My .config shows as a directory with drwx... permissions.
All folders inside it are drwx....
I do not have Kubuntu, so do not have exact same configuration.
But most but not all files then are -rw-rw-rw-

Did you change permissions in /home?

---

### Post by CatKiller on 2018-12-22
> **oldfred said:**
> My .config shows as a directory with drwx... permissions.
All folders inside it are drwx....
I do not have Kubuntu, so do not have exact same configuration.
But most but not all files then are -rw-rw-rw-

Did you change permissions in /home?

You're behind the times, oldfred. It was mounted read-only because of errors. It's now happened more than once.

---

