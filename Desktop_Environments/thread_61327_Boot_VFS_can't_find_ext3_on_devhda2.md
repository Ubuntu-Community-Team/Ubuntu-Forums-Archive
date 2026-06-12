---
title: "Boot: VFS can't find ext3 on /dev/hda2"
date: 2005-08-31
forum: Desktop Environments
---

### Post by eeried on 2005-08-31
Hello,

I get the above message at boot time; /dev/hda2 is my / partition (filesystem: reiserfs)

Ubuntu boots fine though. Why does it complain ?

Cheers,

---

### Post by JOKe on 2005-08-31
i dont know :( and i wanna know too why is this error
im the same
ReiserFS everythink is fine but i get this messege

---

### Post by flying_nomad on 2005-09-07
I found this, maybe that's your answer..........

it looks like it is some kind of (not harmfull) bug in the reifer file system

```

From: "Henrique de Moraes Holschuh" <hmh@debian.org>


> On Sat, 01 May 2004, Bill Moseley wrote:
> > On Mon, Apr 26, 2004 at 04:35:51PM -0300, Broughton, Derek wrote:
> > > When I boot, I experience a number of filesystem related delays.
> > >
> > > All of my HD partitions are Reiser, but I get:
> > > VFS: Can't find ext3 filesystem on dev hda2.
> > > VFS: Can't find ext2 filesystem on dev hda2.
> > > Unable to identify CD-ROM format.
> > > FAT: bogus number of reserved sectors
> > > VFS: Can't find a valid FAT filesystem on dev hda2.
> > > found reiserfs format "3.6" with standard journal
>
> This is the kernel trying to find out what can read your root partition...
> (or the initrd doing the same, maybe).
>
> You can have only the filesystem of your root partition built-in the
kernel,
> and have all others loaded much later as modules, if you want to skip the
> above.

OK.  That fits with Bill's idea - if you build without initrd then you would
_have_ to have the root filesystem compiled into the kernel. I could see
that's what was happening (though it really strikes me as a pretty weak
algorithm - there's no point in checking ext3 and surely FAT could be
checked last), but wasn't sure of the correct solution.  Once I get a kernel
that works, I always tweak it anyway, so I'll just compile in reiser next
time.

Thanks, both of you
```

---

