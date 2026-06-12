---
title: "Sbackup nor NSSbackup wil not start"
date: 2009-05-09
forum: General Help
---

### Post by lsutiger on 2009-05-09
I was trying to do a backup this evening, but sbackup nor nssbackup will not start. I opened a shell and ran top while trying to start sbackup and what I saw pop up for a second was "sbackup<defunct>.
I googled a bit, but could no find an answer.

Could anybody help me out on this one?
thanx in advance!

---

### Post by snaga on 2009-05-18
Bumping this. I am having the same problem. Simple Backup was working fine until a couple of weeks ago, but now it will do no auto backups and I get the same defunct status on the pid when I try a manual backup. Still digging. I'm not sure, but it may have happened when I had to switch where my backups are going to. I copied all the old backups over to the new spot.

---

### Post by lsutiger on 2009-05-18
Hey snaga..I dug a little bit more and found the common thread. It hapenns when you backup to a network drive and the connection fails...well that's what I got out of it.

So what I did was pull the drive from the networked computer and attached via usb. I have sense been able to do a successful backup.

Hope this helps!
 
PS - Another sign is that your / folder will fill up.

---

### Post by snaga on 2009-05-18
Thanks. I discovered, to some embarrassment, that I was having some permissions issues on the new network drive I was trying to write to.

---

### Post by lsutiger on 2009-05-19
Well, I am trying to backup my office computer and have something a bit different.
This is the first time it has been run on this computer.

It would not start, so I ran  ```
sudo gksu simple-backup-config
```
This is what it spit out:```


(simple-backup-config:9514): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed
/usr/sbin/simple-backup-config:1002: Warning: g_error_free: assertion `error != NULL' failed
  gtk.main()

(simple-backup-config:9514): GLib-GIO-CRITICAL **: g_simple_async_result_set_from_error: assertion `error != NULL' failed

(simple-backup-config:9514): GLib-GIO-WARNING **: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)


```

Any idea whats going on here?

---

### Post by lsutiger on 2009-05-22
The above error happens when I try to run nautilus as sudo.
This seems to be a GTK library bug.

---

### Post by danielgenin on 2010-06-20
I am trying to backup to an external USB hard drive but am having the same problem: sbackup pops up a window with the pid of the backup process but when I ps the pid the process is defunct. The permissions for the backup folder also appear to be correct. Anyone else have the same problem?

---

