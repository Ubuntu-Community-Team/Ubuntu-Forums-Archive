---
title: "Kernel hangs up"
date: 2008-06-19
forum: Debian
---

### Post by JohnLM_the_Ghost on 2008-06-19
I completely messed up my Debian box.
Well I updated the kernel to 2.6.24, but removed the old kernel image prematurely.
New kernel gives heaps of errors at boot and hangs up before INIT.
It most probably doesn't initialize hard disks properly.

As I don't want to reinstall, where can I get the 2.6.18 kernel files to insert into it, so I can boot up make everything right again?

And some pointers how to do it right might be most useful!

Ask any infos needed.

EDIT:
Ok I got my hands on a kernel's tarball!
I'm going to put it's files where they should be (according to where current kernel's files are).
Good Ideas are always welcome!

EDIT2:
Damn its source code! Hoped to get precompiled stuff! I had to know better that they don't come in tarballs.

---

### Post by cdiem on 2008-06-20
You could try searching in [http://packages.debian.net/](http://packages.debian.net/) , if all else fails.

---

### Post by JohnLM_the_Ghost on 2008-06-20
ok now I have a deb package... unpacked it, and the files look quite straightforward.
Only is the configscripts absolutely necessary to run the kernel? Wouldn't it be enough to put the kernel files in appropriate places.

except of course I surely need to edit menu.lst, so I can run the kernel

EDIT:
The INITRD file has been "missing" from the deb, which I suspect is created during normal installation of deb package.
I tried to make my own, with no luck. (It leaded to Kernel Panic)
And also tried other INITRD's, also no luck. (but no Panic)

So as the last resort I would ask someone to upload/send me the debian's **initrd.img-2.6.18-6-486** if someone uses or can get it.
Thanks in advance!

EDIT:
So I risked health of my Ubuntu box, an installed the deb package there, got the initrd file, moved to Debian box.
No luck again... only it did not give as much errors.

Probably the responsible error is (might not be exact, writing from memory):
```
PIIXa: bad irq(0), probing later
```

Oh well I will try to fresh reinstall then...
Problem probably solved! (I will mark when I have successfully reinstalled Debian)

---

### Post by voteforpedro36 on 2008-06-20
Well, here goes nothing...

I put it on Mediafire, I didn't figure uploading to the forum would work very well.

**This is going to take like 16 minutes, I'll edit back when it's done, okay?

EDIT: Nevermind, since you've just decided to reinstall. Sorry I was late.

---

### Post by JohnLM_the_Ghost on 2008-06-21
Thanks!
Though the thing probably wouldn't have worked anyways. Initrd file is quite machine specific... I suspected that already when it didn't came with the package, but needed to be built.

So I will give last chance trying even older kernel... If that won't help then have to reinstall. After such a headache, I wasn't in mood to reinstall the shitbox yesterday.

Arghh! It is only my own fault. I will now know better when tinker with toys from 'testing' repository

---

### Post by JohnLM_the_Ghost on 2008-06-25
I'm quite afraid reinstalling... and I haven't done it yet.
So it would be very nice to hear any good ideas!

*BUMP*

EDIT: Hmm... I get the feeling it is now a hardware problem. To be precisely Hard Disk's.
Well my attempt to install Debian failed! The install failed to mount hda2 (my main ext2 partition) as /
And something messes with the HDD's at general. I got some obscure errors all around.
Perhaps /dev/hda is conflicting with the rest.
(maybe I should low-level format all of them and start over again...)

Funny, reason I expected (the testing kernel update) might have nothing to do with this other than happening right at the same time. Oh well, this thread is neither solved nor in the right place. As it is so me-specific, one might as well remove this thread. I will post if I ever have any progress resolving or idea what actually happened!

Have a nice and productive day!

---

### Post by JohnLM_the_Ghost on 2008-07-01
THE COMPUTER IS DEAD!

Well I figured that out after changing HDD's few times, set compatiblity mode in BIOS, and it still didn't install Debian.
And whatever I did it still gave me PIIXa errors.

Join me in a moment of silence.
May the soul of this computer rest in peace and reach the heavens of master kernel.

Thread Closed._

---

