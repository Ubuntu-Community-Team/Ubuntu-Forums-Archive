---
title: "Restoring a backup with Deja Dup or Duplicity?"
date: 2009-01-23
forum: General Help
---

### Post by Hund on 2009-01-23
I've made a backup of my homefolder with "Deja Dup" and now I want to restore my homefolder. I have about 2400 encrypted files (Why is it so many files btw?) that looks like this:

> D5FJK2~K.GPG      DBW4IZ~W.GPG  DHONQA~I.GPG  DN821K~K.GPG  DTONW9~H.GPG
D5GPG0~T.GPG      DBXVU6~D.GPG  DHP4DA~V.GPG  DN8IKR~T.GPG  DTP02A~R.GPG
D5H3EV~0.GPG      DBYF89~R.GPG  DHPNOF~Q.GPG  DN91K5~8.GPG  DTPQG5~4.GPG

Etc.

When I'm trying to restore my backup with "Deja Dup" i just crashes:

> johan@Tiji:/media/disk/Backup_Deja_Dup_190109$ deja-dup
** (deja-dup:10197): DEBUG: DuplicityInstance.vala:114: Running the following duplicity (10200) command: ionice -c3 duplicity collection-status file:///media/disk/Backup_Deja_Dup_190109 --verbosity=9 --log-fd=19

** (deja-dup:10197): DEBUG: DuplicityInstance.vala:417: duplicity (10200) exited with value 0

Segmentation fault

When I try to use Duplicity:

> johan@Tiji:/media/disk/Backup_Deja_Dup_190109$ duplicity file:///media/disk/Backup_Deja_Dup_190109/ /home/johan/temp/
GnuPG passphrase: 
Traceback (most recent call last):
  File "/usr/bin/duplicity", line 583, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 577, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 540, in main
    restore(col_stats)
  File "/usr/bin/duplicity", line 300, in restore
    restore_get_patched_rop_iter(col_stats)):
  File "/usr/bin/duplicity", line 317, in restore_get_patched_rop_iter
    backup_chain = col_stats.get_backup_chain_at_time(time)
  File "/usr/lib/python2.5/site-packages/duplicity/collections.py", line 785, in get_backup_chain_at_time
    raise CollectionsError("No backup chains found")
CollectionsError: No backup chains found

How do I restore my backup? Or atleast how do I decrypt my backup? I cant understand how stupid I was to trust apps like this.. :(

---

### Post by mikix on 2009-01-27
Hello!  I am the maintainer of Deja Dup, and found this post.  Maybe I can help.

> **Hund said:**
> I have about 2400 encrypted files (Why is it so many files btw?)

duplicity creates many files (it calls them volumes) that together make up the backup.  This way it can restore only certain files easier (less to download) and retry failed uploads faster (less to upload).  It defaults to 5M, but you may have some 1M files too, as Deja Dup defaulted to 1M for a release.  This can add up rather quickly.

> **Hund said:**
> When I'm trying to restore my backup with "Deja Dup" i just crashes:

That seems very bad!  I take such crashes seriously, as obviously they make the point of Deja Dup rather moot.  If you're interested in helping me track such a crash down, could you please report it in our bug tracker?  [https://bugs.launchpad.net/deja-dup](https://bugs.launchpad.net/deja-dup)

If possible, install the 'deja-dup-dbg' package, and run deja-dup in gdb to get a stack trace:

```
$ sudo apt-get install deja-dup-dbg
$ gdb deja-dup
(gdb) run
...
... do your thing, after crash do:
...
(gdb) bt
```

If you're not sure how to do that, I'd at least like the last 50 or so lines from running the following:

```
export DEJA_DUP_DEBUG=1
deja-dup > /tmp/deja-dup-log.txt
```


> **Hund said:**
> How do I restore my backup? Or atleast how do I decrypt my backup?

It appears that your external disk was formatted with FAT or NTFS.  When using such disks, Deja Dup passes duplicity the --short-filenames option to make duplicity work.  You should be able to restore from duplicity by using that flag.

> **Hund said:**
> I cant understand how stupid I was to trust apps like this.. :(

Not entirely stupid!  While Deja Dup is, in my opinion, greater than sliced bread :), it is somewhat untested (only 4 months old).  However, the underlying tool duplicity does have lots of testing and as far as I can tell is rather robust.

It just isn't user friendly (e.g. your inability to restore because you didn't know you needed some magic flag).  That's where Deja Dup is *supposed* to come in, but obviously it failed you here.

---

### Post by mikix on 2009-01-29
I just released Deja Dup 7.0, which should fix the crash you saw.

If you ever try Deja Dup again, I hope it's a better experience!

---

