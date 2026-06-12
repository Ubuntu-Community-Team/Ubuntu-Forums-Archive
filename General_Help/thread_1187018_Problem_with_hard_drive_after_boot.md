---
title: "Problem with hard drive after boot"
date: 2009-06-14
forum: General Help
---

### Post by lajo01 on 2009-06-14
Hi,
After a re-boot of my 9.04 system one of my storage drives won't play anymore. No changes was made to the system prior to the re-boot and I was editing files from that drive just fine.

fsck comes up with 
root@NAS2:~# fsck /dev/sde1
fsck 1.41.4 (27-Jan-2009)
e2fsck 1.41.4 (27-Jan-2009)
fsck.ext3: Device or resource busy while trying to open /dev/sde1
Filesystem mounted or opened exclusively by another program?

blkid reports the disk as is should:
/dev/sde1: LABEL="primary" UUID="c186177f-d678-4a6f-8ba4-a2d410730b5b" TYPE="ext3" SEC_TYPE="ext2"

Trying to mount it:
root@NAS2:~# mount /dev/sde1 /media/primary/
mount: /dev/sde1 already mounted or /media/primary/ busy

(and no it's not already mounted)

So I'm unable to mount or do anything with it. Any suggestions on what to do? I mean if the drive has crashed or file system become bad, I'd expect another error message, right?

Cheers 
Anders

---

### Post by dandnsmith on 2009-06-14
Have you tried, as a sanity check (industry term - not a reflection n your possible state of mind) booting from a liveCD, and trying the operation from that?

---

### Post by lajo01 on 2009-06-14
dandnsmith:
Well a sanity check on myself might result in un-desired self-knowledge so I'll pass on that... ;-)

However running liveCD as recommended (why didn't I think of that myself) resulted in a clean mount and fsck of the drive in question.

And, for no obviuos reason, rebooting on my real install the drive is mounted as it should again.

I have no idea why it works now, but thanks! :)

---

### Post by dandnsmith on 2009-06-14
Glad to help

---

