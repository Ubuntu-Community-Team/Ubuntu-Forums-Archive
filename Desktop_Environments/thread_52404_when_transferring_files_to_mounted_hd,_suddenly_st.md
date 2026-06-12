---
title: "when transferring files to mounted hd, suddenly stops"
date: 2005-07-27
forum: Desktop Environments
---

### Post by aleahey on 2005-07-27
ok, new problem, new thread. when transferring files to my newly-formatted-and-mounted hd, it copies for a while and then suddenly stops with a "Read i/o: Filesystem read only" error. when i do "dmesg | tail" i get:

> end_request: I/O error, dev hdb, sector 87818303
EXT3-fs error (device hdb1): read_block_bitmap: Cannot read block bitmap - block_group = 335, block_bitmap = 10977280
Aborting journal on device hdb1.
ext3_abort called.
EXT3-fs error (device hdb1): ext3_journal_start_sb: Detected aborted journal
Remounting filesystem read-only
EXT3-fs error (device hdb1) in ext3_reserve_inode_write: Journal has aborted
EXT3-fs error (device hdb1) in start_transaction: Journal has aborted
EXT3-fs error (device hdb1) in ext3_mkdir: Journal has aborted
__journal_remove_journal_head: freeing b_committed_data


what oh what have i done wrong? :)

---

### Post by aleahey on 2005-07-27
[QUOTE=aleahey]ok, new problem, new thread. when transferring files to my newly-formatted-and-mounted hd, it copies for a while and then suddenly stops with a "Read i/o: Filesystem read only" error. when i do "dmesg | tail" i get:



what oh what have i done wrong? :)[/QUOTE]
 bump?

---

### Post by aleahey on 2005-07-28
[QUOTE=aleahey]bump?[/QUOTE]
 hate to be a pest, but im really stumped here, i changed it to ext2, same thing. is this hardware related?

---

### Post by cutOff on 2005-07-28
One thing: how do you mount your HD? show us, please,  your /etc/fstab.


Regards

---

