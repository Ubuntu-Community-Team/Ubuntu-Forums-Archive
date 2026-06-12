---
title: "File check."
date: 2009-02-27
forum: General Help
---

### Post by noseforsharpies on 2009-02-27
Automatic file check will not complete at boot. Gets stuck at 1%, then informs me that file check failed and to do manual file check. Not sure what to do. Help?

---

### Post by whoop on 2009-02-27
do a manual check after that message:
fsck

---

### Post by noseforsharpies on 2009-02-27
Is there a way to go ahead and initialize a manual file-check?

---

### Post by issih on 2009-02-27
<edit> BAD ADVICE...DO NOT DO THIS, I WAS BEING A PLONKER </edit>

Open a terminal window and enter:
```
fsck
```
The info was in the previous post...just hidden :)

<edit> You may need to throw a -a on the end of that fsck if you have a few different partitions/drives lurking about.

---

### Post by whoop on 2009-02-27
> **issih said:**
> Open a terminal window and enter:
```
fsck
```
The info was in the previous post...just hidden :)
I am not a 100% sure but I believe it is better to run fsck right after you get the file system check error when booting. This because it will give you a "special" read-only terminal to run fsck from.

---

### Post by noseforsharpies on 2009-02-27
WARNING!! Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage.

Their emphasis, not mine..so is it bad to run from the terminal?

---

### Post by whoop on 2009-02-27
> **noseforsharpies said:**
> WARNING!! Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage.

Their emphasis, not mine..so is it bad to run from the terminal?

Did you read my previous post?

> 
I am not a 100% sure but I believe it is better to run fsck right after you get the file system check error when booting. This because it will give you a "special" read-only terminal to run fsck from.


If I am not mistaken the boot process will throw you in the command line when it runs it's automated file system check and fails. you can run fsck from there.

---

### Post by albinootje on 2009-02-27
> **noseforsharpies said:**
> Automatic file check will not complete at boot. Gets stuck at 1%, then informs me that file check failed and to do manual file check. 

Boot from the Ubuntu installation cdrom, choose the "live session", and run fsck on your Linux partition(s), for example :
```

sudo fsck /dev/sda3

```
Make sure you find out which the Linux partitions are by doing this first :
```

sudo fdisk -l

```

---

### Post by issih on 2009-02-27
Doh..stupid me I knew that if I was awake.

I think you can do umount -a first can't you?, although that probably needs to be done from a terminal session rather than from within the DE.

---

