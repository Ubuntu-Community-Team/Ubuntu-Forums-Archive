---
title: "Error when running nautilus from terminal"
date: 2008-12-11
forum: General Help
---

### Post by thegizmoguy on 2008-12-11
I ran: 
sudo-i 
nautilus

and I get this output (then nautilus starts up):

```
Initializing nautilus-share extension
seahorse nautilus module initialized

(nautilus:21527): GLib-GObject-WARNING **: Two different plugins tried to register 'NautilusBurn'.

(nautilus:21527): GLib-GObject-CRITICAL **: g_type_add_interface_dynamic: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(nautilus:21527): GLib-GObject-CRITICAL **: g_type_add_interface_dynamic: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:21527): WARNING **: Unable to add monitor: Operation not supported

--- Hash table keys for warning below:
--> file:///root

(nautilus:21527): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 1 element at quit time (keys above)

(nautilus:21527): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 1 element at quit time
seahorse nautilus module shutdown
Shutting down nautilus-share extension

```

Help?

---

### Post by karlr42 on 2008-12-11
There's nothing wrong. As long as nautilus starts up and works as you expect it to, you can ignore all that. It's just info the developers probably left in for debugging.
And don't use sudo -i, it can be dangerous. Use ```
gksudo nautilus
```

---

### Post by thegizmoguy on 2008-12-11
Ahhh and I'm running 9.04 alpha....makes sense.  Can you explain why some folders are visible (.mozilla-thunderbird) in the regular nautilus but not in the root nautilus.  Even with "show hidden" enabled.

---

### Post by karlr42 on 2008-12-11
Are you in your home directory? When you start nautilus as root it defaults to showing /root(the root user's home directory). Your home, which you usually see in nautilus, is at /home/<yourusername> .  Navigate there and see if the file you're looking for is visible.

---

### Post by thegizmoguy on 2008-12-11
*Bangs head on desk*

You are very correct.  I don't know why I didn't see it was in the root home.  So I assume root is basically like a separate user?

---

### Post by karlr42 on 2008-12-11
Exactly!

---

### Post by thegizmoguy on 2008-12-11
Great! Thanks for the help.  I'm still having this problem: [http://ubuntuforums.org/showthread.php?t=1008257](http://ubuntuforums.org/showthread.php?t=1008257)

(I was trying to see if a root nautilus would have the file permissions but this problem is so annoying)

---

### Post by glotz on 2008-12-11
(ignore me, too laggy forum today)

---

### Post by karlr42 on 2008-12-11
What do you get from 
```
sudo cp -r /media/<path to folder> ~
```
?
You can just tab-complete the path, assuming it's in media/ . Usually it's /media/disk/Documents\ and\ Settings/...

---

### Post by thegizmoguy on 2008-12-11
I probably did it wrong but:

[email]drowned@unknown:~/.mozi[/email]lla-thunderbird$ sudo cp -r /media/Windows\ XP/Documents\ and\ Settings/dr.owned/Application\ Data
cp: missing destination file operand after `/media/Windows XP/Documents and Settings/dr.owned/Application Data'
Try `cp --help' for more information.
[email]drowned@unknown:~/.mozi[/email]lla-thunderbird$

Wait...added / after Data and it's going...hold on.

---

### Post by thegizmoguy on 2008-12-11
Ok I got a TON of Permission: denied errors.  I also tried copying them to a flash drive and still got permission: denied.

---

### Post by karlr42 on 2008-12-11
You need to put a destination, like 
```
cp -r </path/to/src> </path/to/dest>
```
Your destination is ~, which is your home directory.

---

### Post by karlr42 on 2008-12-11
I'm not sure I can help. Maybe you've only mounted the XP partition in read mode? 
```
mount | grep Windows
```
and check if it says "r" or "rw" in the brackets.

---

### Post by thegizmoguy on 2008-12-11
drowned@unknown:~$ mount | grep Windows
/dev/sda6 on /media/Windows XP type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /media/Windows Vista type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

This might have something to do with this bug I was having until I installed ntfs-config [https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/300443](https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/300443)

---

### Post by karlr42 on 2008-12-11
Hm, it seems to be mounted correctly, and I can't think why cp'ing as root would give a permission denied, seeing as it was most likely root who mounted the drive at startup, but this isn't my area of expertise. 
I'm sure someone more knowledgeable than myself will be along shortly to help!

---

