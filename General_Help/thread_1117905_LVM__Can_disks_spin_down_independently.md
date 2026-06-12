---
title: "LVM:  Can disks spin down independently?"
date: 2009-04-06
forum: General Help
---

### Post by Bllz on 2009-04-06
Hello!

I'm currently running a 2-disk raid0 server, but I've run into a couple of problems.

First, the disk noise is unbearable because of the fact that there are always 2 heads seeking.

Second, although file transfer time has gone down (especially on large files), the seek time has roughly doubled, which leads to a noticeable lag.

Since this is a DVR installation, both of these are real problems, and I was considering switching to a 2-disk logical volume in the hopes of mitigating them.  My question is simply, will a 2-disk logical volume allow the disks to spin down independently to lower noise and power consumption?  Or does some technical limitation force both disks to remain active together?

Thanks very much!
Also, additional relevant tips/general knowledge about LVMs are welcome, although I'm already aware of the risks of raid0 arrays!

---

### Post by Bllz on 2009-04-06
shameless self bump  (I promise it will be the only one)

---

### Post by sdennie on 2009-04-06
It probably depends on how you setup the lvm.  If it's not setup as striped, I don't see why the disks wouldn't sleep independently of each other as it's a hardware setting and not a software setting.  The hardware only cares that the disk is idle.  Whichever route you decide to go, you may also want to check out this guide: [  HOWTO: Decrease disk activity]("http://ubuntuforums.org/showthread.php?t=839998").  It may be that your current setup is salvageable.

---

### Post by Bllz on 2009-04-06
> **sdennie said:**
> It probably depends on how you setup the lvm.  If it's not setup as striped, I don't see why the disks wouldn't sleep independently of each other as it's a hardware setting and not a software setting.  The hardware only cares that the disk is idle.  Whichever route you decide to go, you may also want to check out this guide: [  HOWTO: Decrease disk activity]("http://ubuntuforums.org/showthread.php?t=839998").  It may be that your current setup is salvageable.

Thanks for the info and the link.

My current setup is raid0 -- which is striped, if I'm not mistaken.  That means I'm stuck reinstalling, right?

---

