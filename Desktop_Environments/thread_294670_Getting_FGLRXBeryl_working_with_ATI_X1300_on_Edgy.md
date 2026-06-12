---
title: "Getting FGLRX/Beryl working with ATI X1300 on Edgy"
date: 2006-11-07
forum: Desktop Environments
---

### Post by sbfisher on 2006-11-07
There are a number of guides about how to do this out there and none of them worked for me by themselves, so I'll compile the information about what I did to get things working.

**My symptoms:** I would get mesa as my driver instead of ATI from fglrxinfo.  If I did *dmesg | grep fglrx* I'd get some messages about "fglrx:firegl_unlock error using context 0."  I don't have the time to rewrite everything, so I'll reference what I did that actually worked.  Also the driver would sometimes work for a few boots and then mysteriously stop working before long.
[B]
My setup:[/B]
ATI X1300 video card
Asus K8N and 64-bit Sempron CPU
Edgy 32-bit version (64-bit Edgy was ten times as impossible to get Beryl working on, believe me)
Other hardware junk that probably doesn't matter.

**First of all, install FGLRX and get 3D acceleration according to the instructions at [http://www.ubuntuforums.org/showthread.php?t=291464]("http://www.ubuntuforums.org/showthread.php?t=291464") . ** If I didn't do things this way I'd never get fglrx to work at all! This thread was the only way to install that worked even a bit for me. For the Beryl install steps he seems to have forgotten a couple of steps (like adding Beryl to the startup), so you may prefer another guide instead.  Oh, he also seems to have forgotten the step of 

```
mkdir /lib/modules/`uname -r`/misc
```

before doing the cp command in the first part (at least this folder didn't exist on my system so I had to make it first).

**For the Beryl install section you probably want to refer to the guide at [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html") (since it seems to be complete),** but *don't* reinstall your ATI fglrx drivers again when you run through that thread.

These steps got my 3D acceleration working reliably for 5 boots or so until I dared to try modifying my xorg.conf file (or was it coincidence?).  Once I modified it and even after putting the original file back my 3D acceleration was gone forever, AGAIN.  (I can't tell you how many times I reinstalled Edgy and how many different guides and troubleshooting things I did.  Seriously 30 or more hours worth of trying to get things working.)
[B]
So when your acceleration disappears forever, check *dmesg | grep fglrx* and see if it has a line with the words "fglrx:firegl_unlock error using context 0" i[/B]n it. Then [B]try out the fix at [http://ubuntuforums.org/showthread.php?t=115104]("http://ubuntuforums.org/showthread.php?t=115104")
.[/B]  Even though mine did show the correct amount of memory, this fix seemed to stop the 3D acceleration from crapping out regularly and mysteriously and reverting to  crappy mesa indirect mode.

That was easy! :o

Oh, and chant a few incantations while your at it to please the petulant spirits of Ubuntu. ;-)

Let me know if this actually fixes your problems.  It was the only procedure that seemed to work for me.  Believe me I tried a lot of things, too.

---

