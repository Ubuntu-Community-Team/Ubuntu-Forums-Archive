---
title: "Error reading from file: input/output error"
date: 2017-09-02
forum: Desktop Environments
---

### Post by HDTimeshifter on 2017-09-02
I get the above error when I try to open a file. When I (local network) share it from this computer and tried to open it from another computer, I get a permission denied error. Somewhere (I can't duplicate it now) it said something about read-only file system. I originally copied this file and directory from the other computer, but now I can't open or delete the file. I got around this error by turning off file sharing and deleting it (I may have had to reboot), but I recopied the file and directory from the other computer and am getting the same errors again. I'm starting to think there is a disk problem.

---

### Post by gordintoronto on 2017-09-02
There are a variety of programs which can show you the SMART data for a drive. I have one installed called gsmartcontrol, another is called disks.

However, I think this might be a bug. Write down any error messages and Google them.

---

### Post by HDTimeshifter on 2017-09-03
I fixed the problem (again) by rebooting, deleting the directory locally, then was able to copy the directory back from the other computer. I'm basically using this computer as a file server for backups. I plan on using some automatic backup method in the future and will probably revert to NFS instead of local file sharing with Samba. There may have been a Samba bug as this was the same computer that kept reporting "Install Updates" and every time I clicked that button, it would update and say "Computer Up-To-Date", but then the button would revert to "Install Updates". I fixed that problem by updating and upgrading manually from the command line, which performed some Samba updates.

Disks shows all the SMART data ok for this drive.

---

### Post by lammert-nijhof on 2017-09-03
You probably have a problem with the permissions of the file. Right click the directory and select properties and the permission tab. Probably only the root will have permissions for the file. Do the same for the directory on the other computer. Are the user-ids you use on both PCs the same? If you start nautilus from the terminal with 'sudo nautilus' you should be able to correct the owner and/or other permissions of that local directory or file. Very probably it is not a bug, but a security feature. 

I would introduce a group of users that have full access to those network directories on both computers and make all relevant users of both PCs members of that group through the "Users & Groups" utility. And don't forget to change the permissions of those network directories, so that the group has full access to those directories.

---

### Post by HDTimeshifter on 2017-09-04
I have owner read/write permissions and am logged in as the owner on both computers. I ran into the problem again last night and the only fix was to reboot the server.
I have noticed strange sounds from the server like a clicking noise or whine when the disk activity light is fairly solid (like when I first wake it from sleep or when there was probably copy activity going on for a lot of files), so I'm afraid the disk is going bad even though there are no SMART errors.

---

### Post by HDTimeshifter on 2017-09-04
I just got the error again, this time with a completely different file and directory. I rebooted the server and the data drive in it that I use to back up my data from my main computer wouldn't mount. The error below is what I get (the last line "(udisks-error-quark,0" only shows up when I try to mount with the Disks utility:

```
Error mounting /dev/sdb1 at /media/roger/Data: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb1" "/media/roger/Data"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.
 (udisks-error-quark, 0)
```

I tried syslog, but it says:
```
No command 'syslog' found, did you mean:
 Command 'dsyslog' from package 'dsyslog' (universe)
```

I installed the dsyslog package, and it displays:
[CODE](dsyslog:3563): GLib-CRITICAL **: g_queue_push_tail: assertion 'queue != NULL' failed
logsocket:bind: Address already in use

(dsyslog:3563): GLib-CRITICAL **: g_queue_push_tail: assertion 'queue != NULL' failed
[\CODE]

---

### Post by HDTimeshifter on 2017-09-04
I just found this thread about remapping a superblock: [https://ubuntuforums.org/showthread.php?t=1245536]("https://ubuntuforums.org/showthread.php?t=1245536")

However, when I run
```
$ sudo mke2fs -n /dev/sdb1
```
it says:
```
mke2fs 1.42.13 (17-May-2015)
/dev/sdb1 alignment is offset by 512 bytes.
This may result in very poor performance, (re)-partitioning suggested.
Creating filesystem with 122096638 4k blocks and 30531584 inodes
Filesystem UUID: 34da2aa2-9d8d-4cd2-87e5-357d1f3d6397
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000
```

Since the alignment if offset for very poor performance, I think I'll try re-partitioning and hopefully it sets up the superblock at the next offset that is a good block...

---

