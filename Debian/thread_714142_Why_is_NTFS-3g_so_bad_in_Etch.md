---
title: "Why is NTFS-3g so bad in Etch?"
date: 2008-03-03
forum: Debian
---

### Post by regomodo on 2008-03-03
I'm confused at why there is no package for ntfs-3g in Debian Etch. I'd thought it would be a crucial one to have.

You can compile from source but it's not recommended. I did so but under heavy load i lose communication to my ntfs drive and can't get it back until a reboot. This happens every time. Say, rdiff-backup (backup from), mysql, and image processing.

It is not a major issue for me as i've had enough of these bugs and going to format to ext3. 

Anybody have any idea?

---

### Post by polmir on 2008-03-03
add to your  **/etc/apt/sources.list**
```
deb http://www.backports.org/debian etch-backports main contrib non-free
```

```
apt-get update
```

```
gpg --keyserver subkeys.pgp.net --recv-keys IDXXXXXXX
```
```
gpg --armor --export IDXXXXXXX | sudo apt-key add -
```

```
apt-get update
```

```
apt-cache search ntfs-3g
```

[QUOTE=out search]libntfs-3g-dev - ntfs-3g filesystem in userspace (FUSE) library headerslibntfs-3g2 - ntfs-3g filesystem in userspace (FUSE) library
ntfs-3g - read-write NTFS driver for FUSE[/QUOTE]

```
apt-get install ntfs-3g
```

---

### Post by regomodo on 2008-03-04
ah, that looks a lot better than what i had found so far. Using old packages people had made using checkinstall.

I had seen the backports repo but i was always under the impression you had to edit the apt-preferences file to set the priorities of each.

I don't have a proper ntfs partition any more but cheers for the help anyway.

---

### Post by dptxp on 2008-03-10
It is not advisable to write to NTFS from Linux.

---

### Post by p_quarles on 2008-03-10
> **dptxp said:**
> It is not advisable to write to NTFS from Linux.
It's not advisable to make statements advising against something that is commonly done without backing it up.

---

### Post by dptxp on 2008-03-11
I may be wrong as I use FAT 32 only. But this is based on all the information I collected from internet while choosing between NTFS and FAT32 for Window$. 
One link is here-
[http://manual.sidux.com/en/hw-dev-hw-dri-en.htm#hd-ntfs3g](http://manual.sidux.com/en/hw-dev-hw-dri-en.htm#hd-ntfs3g)
Maybe Ubuntu handles it safe.

But then we use so many things regularly without problems though they carry warnings.

---

### Post by markharding557 on 2008-03-14
i think you should upgrade to debian lenny this is much more up to date and if you want to make it almost as solid as etch you can lock the kernel version so it can't be changed unless you want it to

---

