---
title: "Hardy - automount. Disable!"
date: 2009-03-29
forum: Desktop Environments
---

### Post by AR_Kozz on 2009-03-29
I finally decided Gutsy was getting to old recently and upgraded to Hardy... in addition to giving me back the hated Totem movie player, Gnome is now able to successfully autodetect and mount usb drives formatted in fat-32. Which it wouldn't do under the ubuntu 7's. I wish it still couldn't do it, because it does it WRONG... namely, as read-only. 

able to use "sudo mkdir" no problem, but as soon as I try to write actual data to the disc, the "read-only filesystem" popped up... using umount and then mounting from terminal doesn't seem to help, it remains "read-only"; shutting down the drive, reactivating it and trying to mount from terminal doesn't help either, Gnome mounts it immediately like a horny billy goat.

I sure do miss the older versions of Gnome where they had menu options for telling it not to try to automount stuff. "Removable Drives and Media" has options for cameras, pda's, printers, and input devices - everything except actual removable drives, apparently. 

I know I'll get the damn thing mounted right eventually but I might as well ask if anyone knows where to get at Gnome, or whatever is responsible for the automounting, and configure it manually, so it will stop trying to automount. without having to add to fstab hopefully.

(and no, the drive isn't, in fact, read-only, nor write-protected)

<edit> ok, got it to work by mounting with -o rw option... that is supposed to be the default. Pretty annoying to have to type it. Still want to put a leash on the automount.

<more> so basically the deal is even after editing fstab to make sure it mounts as -rw, what happens is that it only remains rw for a while... after about 10 minutes of writing, it suddenly reverts to read only! My best guess is either:

1) the operation is losing its root privileges somehow, which seems unlikely; or
2) the Session manager is trying to grab and remount the drive as read-only. This seems possible because when I unmount the drive, and leave it unmounted, after a few minutes the Session manager re-mounts it again, and as read-only - completely ignoring fstab.

I have disabled the Volume Manager, but Gnome still can't seem to keep its grubby auto-mounting hands off the usb drive... might stop after I reboot I guess.

My ps3 can still write to the drive just fine.

---

