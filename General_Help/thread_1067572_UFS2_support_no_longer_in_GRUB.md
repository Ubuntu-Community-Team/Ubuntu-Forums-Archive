---
title: "UFS2 support no longer in GRUB?"
date: 2009-02-12
forum: General Help
---

### Post by vmarcenne on 2009-02-12
Installed on one hard drive are three operating systems:
[LIST]
[*]sda1 is Windows XP Pro on NTFS.
[*]sda2 is PC-BSD 7.0.2 on UFS2.
[*]sda3 is extended with:
[list]
[*]sda5 as Intrepid Ibex on EXT3
[*]sda6 as Linux-swap
[/list]
[/LIST]

After familiarizing myself with [GRUB device syntax]("http://www.gnu.org/software/grub/manual/html_node/Device-syntax.html") and [a FreeBSD-specific GRUB setup]("http://lists.freebsd.org/pipermail/freebsd-hackers/2004-May/006944.html"), and going through the discouraging failure of [FONT="Courier New"]Error 17: Cannot mount selected partition[/FONT] many times, I've just about run out of solutions.

Jiafu He on the FreeBSD Mailing list went through the setup of GRUB for support of FreeBSD, and through his setup the file [FONT="Courier New"]/boot/grub/ufs2_stage1_5[/font] was successfully installed (from what the GRUB shell stated, it was embedded). Well, mine wasn't. I cannot find the file!

```
$ ls /boot/grub
default        images             menu.lst~        reiserfs_stage1_5
device.map     installed-version  menu.lst.backup  stage1
e2fs_stage1_5  jfs_stage1_5       menu.lst.GruBK   stage2
fat_stage1_5   menu.lst           minix_stage1_5   xfs_stage1_5
```

The file is nowhere to be found, and therefore is not installed for GRUB to recognize UFS2.

I cannot say for certain what the specific problem is. However, the only difference between my GRUB installation and He's installation is the absense of [FONT="Courier New"]ufs2_stage1_5[/font]. Could anybody provide any feedback on a possible solution?

[COLOR="Red"]EDIT:[/COLOR] Instead of installing GRUB from the FreeBSD port system (I could not because I still have not been able to boot) while booted onto FreeBSD, I installed it from the Ubuntu repository from within Ubuntu. Would this make a difference?

Citation:
[http://lists.freebsd.org/pipermail/freebsd-hackers/2004-May/006944.html]("http://lists.freebsd.org/pipermail/freebsd-hackers/2004-May/006944.html")
[http://www.gnu.org/software/grub/manual/html_node/Device-syntax.html]("http://www.gnu.org/software/grub/manual/html_node/Device-syntax.html")

---

### Post by dcstar on 2009-02-12
> **vmarcenne said:**
> Installed on one hard drive are three operating systems:
[LIST]
[*]sda1 is Windows XP Pro on NTFS.
[*]sda2 is PC-BSD 7.0.2 on UFS2.
[*]sda3 is extended with:
[list]
[*]sda5 as Intrepid Ibex on EXT3
[*]sda6 as Linux-swap
[/list]
[/LIST]

After familiarizing myself with [GRUB device syntax]("http://www.gnu.org/software/grub/manual/html_node/Device-syntax.html") and [a FreeBSD-specific GRUB setup]("http://lists.freebsd.org/pipermail/freebsd-hackers/2004-May/006944.html"), and going through the discouraging failure of [FONT="Courier New"]Error 17: Cannot mount selected partition[/FONT] many times, I've just about run out of solutions.

Jiafu He on the FreeBSD Mailing list went through the setup of GRUB for support of FreeBSD, and through his setup the file [FONT="Courier New"]/boot/grub/ufs2_stage1_5[/font] was successfully installed (from what the GRUB shell stated, it was embedded). Well, mine wasn't. I cannot find the file!

```
$ ls /boot/grub
default        images             menu.lst~        reiserfs_stage1_5
device.map     installed-version  menu.lst.backup  stage1
e2fs_stage1_5  jfs_stage1_5       menu.lst.GruBK   stage2
fat_stage1_5   menu.lst           minix_stage1_5   xfs_stage1_5
```

The file is nowhere to be found, and therefore is not installed for GRUB to recognize UFS2.

I cannot say for certain what the specific problem is. However, the only difference between my GRUB installation and He's installation is the absense of [FONT="Courier New"]ufs2_stage1_5[/font]. Could anybody provide any feedback on a possible solution?

Citation:
[http://lists.freebsd.org/pipermail/freebsd-hackers/2004-May/006944.html]("http://lists.freebsd.org/pipermail/freebsd-hackers/2004-May/006944.html")
[http://www.gnu.org/software/grub/manual/html_node/Device-syntax.html]("http://www.gnu.org/software/grub/manual/html_node/Device-syntax.html")

[http://ubuntuforums.org/showthread.php?t=822037](http://ubuntuforums.org/showthread.php?t=822037)

---

### Post by vmarcenne on 2009-02-12
> **dcstar said:**
> [http://ubuntuforums.org/showthread.php?t=822037](http://ubuntuforums.org/showthread.php?t=822037)

That doesn't help at all, unfortunately. I've tried:

```
title FreeBSD
root (hd0,0)
chainloader +1
```
and
```
title FreeBSD
root (hd0,0,a)
kernel /boot/loader
```

with no luck. The first one just makes GRUB reload over an over again. The second one gives me another [font="Courier New"]Error 17[/font].

Thank you, David, for the attempt.

---

