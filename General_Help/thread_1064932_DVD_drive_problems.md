---
title: "DVD drive problems"
date: 2009-02-09
forum: General Help
---

### Post by Dr Small on 2009-02-09
I am copying non-encrypted DVDs (it's not illegal) and then burning them to another DVD (I'm making backups). I've been copying the DVD's to ISO files with dd and then burning them with growisofs, but the problem seems to be that everytime I burn a disc, the drive malfunctions at the end of the disc and won't copy the last 2 or 3 remaining minutes.

So, I've been copying them with this:
```
dd if=/dev/dvd of=07.iso bs=1MB
```

And burning them like this:
```
growisofs -speed=5 -Z /dev/dvd=07.iso
```

I have to reboot the system in order to get the drive to read the entire disc again, which is a real pain. I can copy several discs to the hard drive and then burn them all to their own discs, but when I go to copy another one VLC can't play to the end of it (from the disc) and even if I copy it to the hard drive VLC can't play the tail end of it.

I was thinking that it was a hardware problem, but it goes away if I reboot. It acts like something is holding a process after I am burning the disc and causing problems, but I don't know what to look for.

---

