---
title: "Couple of questions about Nautilus"
date: 2009-09-06
forum: Desktop Environments
---

### Post by RalphS on 2009-09-06
Hey

I have a NTFS partition on an internal HHD mounted in fstab like this:

UUID=90CC8EFECC8EDDBA	/media/D	auto	defaults	0	1

1) Yes, it does have photos on it, but how do I prevent the 'The medium contains digital photos... ' banner from appearing at the top? I have turned off all the media handling in preferences.

2)Not a biggie but why is there an eject icon here? its an internal HDD, and only root can unmount it so pressing it fails anyway.

---

### Post by quixote on 2009-09-08
I'm not sure your fstab entry is being used at all because there seem to be a few errors in it.  I'd be willing to bet the behavior you're seeing is because gnome has become confused and has decided it's some kind of removable media and is mounting it a la gnome.

fstab requires:
```

uuid or device   mount point      **filetype**    options              backup  and check options
UUID=whatever    /mount/directory     ntfs     user,auto,noatime	0	2

```
the options should be without spaces and separated by commas.  I'm also not exactly sure what the code is for an ntfs filesystem, so try a search for "fstab ntfs" to make sure what's right.

Hope this helps.

---

### Post by amac777 on 2009-09-08
> 1) Yes, it does have photos on it, but how do I prevent the 'The medium contains digital photos... ' banner from appearing at the top? I have turned off all the media handling in preferences.


This might not work, but try renaming or removing the DCIM directory so the hard drive won't look like it's a memory card from a digital camera.

---

### Post by RalphS on 2009-09-10
Renaming the DCIM directory did the trick, thanks. 

I am pretty sure its being mounted by fstab ok because:

a)I can still get to them if I log in with a failsafe terminal instead of gnome session.

b)I have a 3rd NTFS partition (the 10.5GB one), and clicking that gets me a system policy prevents mounting internal media popup and I need to supply my password to mount it. Once mounted like this, the button does unmount it. I suspect its showing the button for the others because it thinks they have been mounted in this way.

---

