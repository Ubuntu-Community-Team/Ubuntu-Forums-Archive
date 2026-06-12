---
title: "Running Vista through Ubuntu?"
date: 2009-05-23
forum: General Help
---

### Post by jbecks on 2009-05-23
I have both Vista and Ubuntu operating systems installed on my computer. I think I have a virus on my Vista OS, because it will not start up. It will not boot using safe mode or a boot disk either.  A couple of times it has even shut down after I decided to boot using Ubuntu before Ubuntu fully boots. It doesn't shut down if Ubuntu fully boots though, and their are no problems after the boot. Is it possible to run my already installed Vista OS through Ubuntu, or perform a virus scan on the Vista partition?

---

### Post by RichardG891 on 2009-05-23
Install ClamAV from synaptic, and then mount your vista partition and point the scanner at it. It'll take an age, and it doesn't have a huge definition list. Doesn't really sound like a virus though. Do you have the full Vista retail disk or just a set of OEM recovery disks - it may "just" be a corruption in the MBR or Grub, and a retail disk should have some repair tools; the OEM stuff just restores the system to its factory state, and will wipe everything in the process.

---

### Post by jbecks on 2009-05-23
I have the original disk.  It will not boot to anything besides Ubuntu.  It will get to a point in the boot process, and just shut down.  If I boot to Vista it acts like it will run fine, but shuts down shortly after showing the desktop and starting all of the processes.  If I boot using safe or the disk, it shuts down even sooner in the process.  I believe it's a virus because a couple days ago my virus scanner found a virus and supposedly deleted it.  It has never found a virus before, so I don't think it's just coincidental.

---

### Post by RichardG891 on 2009-05-23
Give ClamAV a go... I would copy any personal files you have on the vista partition over to ubuntu or an external drive first, and scan them separately.

---

### Post by Mirge on 2009-05-23
> **RichardG891 said:**
> Give ClamAV a go... I would copy any personal files you have on the vista partition over to ubuntu or an external drive first, and scan them separately.

I'm with Richard here. Back up all of your files via Ubuntu onto an external drive, or onto your Ubuntu partition if you don't have any external storage. You might end up formatting Windows.

---

### Post by sgosnell on 2009-05-23
From the description, I think it's more likely to be a hardware problem, not a virus.  You're having problems at least part of the time with every OS, and every boot device.  I think you may have a motherboard problem of some sort, maybe just a glitch with a peripheral device.  Most viruses don't prevent booting in this manner.

---

### Post by RichardG891 on 2009-05-23
> **sgosnell said:**
> From the description, I think it's more likely to be a hardware problem, not a virus.  You're having problems at least part of the time with every OS, and every boot device.  I think you may have a motherboard problem of some sort, maybe just a glitch with a peripheral device.  Most viruses don't prevent booting in this manner.
Yes. If ubuntu sometimes doesn't boot up properly either, then it's not due to a virus on Vista. I couldn't comment on low level viruses though (boot sector, CMOS), 'cos I'm just a casual geek.... If it were my computer, I would back up everything I wanted to keep, throw a hissy fit and spend Sunday installing everything again from scratch. If reinstallation generated errors, then it's hardware-related... another hissy fit and go shopping.

---

