---
title: "Hard drive permission"
date: 2005-12-06
forum: General Help
---

### Post by Minn3h on 2005-12-06
This must be a common question, but for the life of me I can not find a solution.

I have a harddrive with three partitions:
1. Ubuntu (hdb1)
2. Swap
3. Empty ext3 (hdb3)

I can mount and read hdb3 without a problem, but am unable to write to this partition.  I'm not sure what changes I need to make to be able to do this.  I thought for a while it had to do with my fstab, but I'm fairly sure that's not the problem.  I believe I need to chown or chmod something, but I'm not familiar enough with these commands to do anything.  If someone knows the exact commands I need, that would be awesome.

---

### Post by apolyak on 2005-12-06
Let's say that:
- hdb3 is mounted as /hdb3_mount_dir.
- your user name = your_user_name
- your main group = your_user_name

To find out your main group type:

	ls -l /home 

and look for

drwxr-xr-x  45 your_user_name your_main_group 1792 2005-12-06 21:17 your_home_directory

Create <test> directory as root:

	sudo mkdir /hdb3_mount_dir/test

Now change owner and group of the <test> directory to yourself:

	sudo chown your_user_name /hdb3_mount_dir/test
	sudo chgrp your_user_name /hdb3_mount_dir/test

Later you can learm how to combine these two commands into one.

---

### Post by Minn3h on 2005-12-06
Awesome, thanks. I didn't realize it was so simple and all the +w -r things confused me.

---

### Post by apolyak on 2005-12-06
No problem. Things like +w, +x or 644 relates to file access mode (permissions): read, write execute. You may find this link very useful [http://www.onlamp.com/linux/cmd/](http://www.onlamp.com/linux/cmd/)

---

