---
title: "How can I make a floppy image file without a floppy drive?"
date: 2009-04-26
forum: General Help
---

### Post by col48 on 2009-04-26
This is not as daft as it sounds.

I am running an Ubuntu 8.04 host machine with a Windows95 virtual machine as guest.  Sometimes the W95 machine expects to find some files on a floppy.  I have the files on the host, so I need to make a floppy image on the host which I can then pass to the guest via a virtual floppy drive.

Can anyone tell me how I can make a floppy image file in Linux given a set of files I want to be included?  The "disk" does not need to be bootable.

I do NOT have a physical floppy drive on the machine.

---

### Post by dandnsmith on 2009-04-26
I don't know the answer to this, as I've no idea what will convince W95 within a virtual machine.
I'd look for a solution using a filesystem within a suitable sized space, mount it via loop, and point /dev/fd0 to it.

It would go something likethis:
The filesystem space can be made with
dd if=/dev/zero of=yourfilename BS=1000 count=2
and then
mkfs.fat -F yourfilename
mount -o loop yourfilename yourmountpoint

Please don't rely on the parameters being correct - use the man pages if in doubt.

---

### Post by col48 on 2009-04-27
Thanks Derek.  It has pointed me in a helpful direction, although the documentation (thousands of lines) is full of jargon I am not at home with.

But I dimly understand where that is going.  Since my original post, I had an idea (unlike me, I know!) and created a floppy disk image on another machine which I have copied over to the Ubuntu machine.  Now if I can fool both Ubuntu and the VM that this is a virtual floppy for both read and write then I am home.

Snag for Ubuntu is I do not have /dev/fd0 so I cannot mount it as you describe.  I have not yet searched for the way to do this, but there must be one.

On the VM side, I know how to tell the W95 machine where to find the virtual floppy but it thinks the drive is not ready.  I will pursue this aspect elsewhere.

---

### Post by col48 on 2009-04-27
The following threads put meat on the Ubuntu side of the equation.  Someone has asked about a virtual floppy disk before!

[http://ubuntuforums.org/showthread.php?t=1035940](http://ubuntuforums.org/showthread.php?t=1035940)

and

[http://ubuntuforums.org/showthread.php?t=570903](http://ubuntuforums.org/showthread.php?t=570903)

So thanks to users dandnsmith, milosz-galazka, TheLions.

---

### Post by dandnsmith on 2009-04-28
Perhaps the last stage can be done by creating a pseudo floppy in linux, and I think you'll need a symbolic link to the mounted image from /dev/fd0.
This is what used to get linked to the 'real' floppy in the appropriate read/write mode.

use ln -s
and read the parameters - I always get them wrong first time off, especially since it is so seldom that I need to do it.

---

