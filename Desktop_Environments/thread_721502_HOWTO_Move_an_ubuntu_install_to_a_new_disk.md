---
title: "HOWTO: Move an ubuntu install to a new disk"
date: 2008-03-11
forum: Desktop Environments
---

### Post by keratos on 2008-03-11
After searching the posts here, I found many people were struggling with moving an existing ubuntu install to a new or existing hard disk.

I have performed this activity from the command line, using a series of shell commands, from within a Terminal window, without rebooting or logging out.

If there is sufficient interest, I am prepared to put this into bash script that people can download from here and run from within a Terminal window. Ultimately, I'd like to develop this into a GUI app with a "Select the disk, press the button and wait" strategy. Dead simple!

The end result of my commands, was that I had a mirror copy of my Ubuntu install transferred, data and all, onto a new faster disk I purchased. On restart, the system presented me with a new boot option, which I selected and the system booted fine and I logged into GNOME. No probs.

So, I suppose is there sufficient interest in my progressing this app? Should I even do this , i.e. is there an existing app "out there"?

Thanks.

---

### Post by ung/xunil on 2008-03-11
Hi keratos,

I don't know how your script works, but supposing it is in BASH, to make it more GUI or CLI (even both?) you can try zenity. Zenity is kind of a lib that is installed in all Ubuntu Desktop (not sure).

In "CLI mode" you can make your BASH script look like "aptitude" (menus, lists, questions and selections).

In the "GUI" mode (GTK) it makes your app look like other Gnome applications. An example of this: [http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/]("http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/").

About apps that make clones of an install, there are various, all different with different approaches. Some copy complete partitions, others backup data. If you search for this keywords, with others, in Synaptic, you will see them.

One that I liked was [mondorescue]("http://www.mondorescue.org/"), but the package in the repositories is not completely working since Dapper. This app (when working correctly) makes a complete backup of all files and data, creates a "boot CD/DVD" with all the backup files compressed, various volumes if needed. Almost "just-boot-the-first-dvd-and-type-nuke" and done. Unfortunatly this "Boot DVD" is the feature that isn't working ATM. But there are more applications for this like partimage (copy partitions) and others.

---

### Post by keratos on 2008-03-15
Ah, so there are some scripts.

No point me reinventing the wheel then.

My script is basically:
{ mount the device/partition to hold the backup }
{ 'cd' to the root directory to backup }
{ create a backup archive using 'tar' and pipe the output to a restore 'tar' on the mounted partition }
{ unmount device/partition }

e.g.
```

mount /dev/hdd2 /media/backup
cd /
tar --exclude=/tmp vcf - . | ( cd /media/backup/backup ; tar xvpf - )
umount /media/backup

```

I was going to put a GUI around the backup device selection, the directory to backup and what to exclude (like /tmp and /usr tmp plus user's directories of choice etc.). Thats as far as I got until I realised there is loads of stuff in the repos that work just like this.

:-(

---

### Post by ung/xunil on 2008-03-16
Very good, clean and simple. Nice one :)

---

### Post by keratos on 2008-03-16
Mmmm.

clean and simple - thats me.

Actually, rsync would probably be more suited if incrementals are require, alas I have since discovered a plethora of utilities to do the job in a variety of ways.

boo hoo

ah wel. :lolflag:

---

