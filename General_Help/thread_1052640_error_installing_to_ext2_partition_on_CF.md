---
title: "error installing to ext2 partition on CF"
date: 2009-01-27
forum: General Help
---

### Post by alphaniner on 2009-01-27
_The short version:_

Does anyone know what options are used by the live installer when formatting an ext2 partition?

_The long version:_

I'm trying to install Ubuntu 8.04.2 to a CF drive.  Actually, I already did so and I'm using it to make this post.  But I encountered an issue when installing that I didn't actually resolve, but had to work around.  First a few details:

Intel DG945GCLF mobo w/atom CPU
Transcend 4GB 300x CF
addonics IDE -> CF adapter
Live install from Corsair 2GB Flash Voyager

So here's what happened.  Using fdisk, I created a new partition table on the CF and created one partition covering the entire device.  I formatted the partition with 'mkfs.ext2 -m 0'.  I then opened the installer and chose manual partitioning.  I set 'Use as:' to ext2, 'Mount point' to / and chose NOT to format.  When I clicked Next I got an error "File system has an incompatible feature enabled."  There was a further error (which I failed to record) saying there were errors in the fs and giving me the option to continue.  I declined.  I tried installing after a restart, and then I tried reformatting with 'mkfs.ext2 -m 1' just for kicks.  No dice.  But when I had the installer format the partition, the installation completed successfully.  I was kind of expecting it to fail, otherwise I would have tried some other methods; at least a default format with mkfs.ext2.  So... beyond the short version, I'm wondering if anyone has had any similar experiences.

---

