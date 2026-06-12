---
title: "Can't delete .Tiff files..."
date: 2009-06-07
forum: General Help
---

### Post by trekon86 on 2009-06-07
Hey all,
Last night I was using something called Hugin to create panoramas out of a bunch of Jpg fotos. I saved em as .Tiff files on my external HD.
When I went today to go delete some of the unnecessary ones, I click on the Tiffs and Thunar (or whatever file manager is included in Xubuntu) kind of locks up. It doesn't appear to lock but when I try to close it out it just hangs. It's a real pain, and I can't delete those dang files either way.
Also, when I tried to unmount my USB drive about an hour ago it wouldn't let me. Told me that there was another application keeping it from unmounting. So I waited, and I tried again, and then I rebooted a couple of times. Now it takes forever to mount and I still can't delete the Tiffs.
Please help if you can. I'm new to this stuff, just learning to use the Terminal and all.
Thanks!
PMZ

---

### Post by trekon86 on 2009-06-07
Well, it must've had something to do with Thunar mainly, cause I just tried PCman File Manager and it worked like a charm.
Is there a way to make Thunar go away and PCman the default FM?
Thanks,
PMZ

---

### Post by lovinglinux on 2009-06-07
I think the problem might be the image preview. Try to disable them and check if it works.

If you find yourself in this situation again in the future, delete the files with command line.

For example, to delete all TIFF files in the Pictures folder use this:

```
sudo rm -f ~/Pictures/*.tiff
```

---

