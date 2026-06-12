---
title: "Drive errors when trying to reinstall Ubuntu Studio"
date: 2020-04-12
forum: Desktop Environments
---

### Post by mrkay2 on 2020-04-12
Good afternoon,

I have a laptop with a 1TB drive divided into an Ubuntu 18.04 partition and an UbuntuStudio partition (~100GB)  I attempted to do a clean install of UbuntuStudio 20.04 and it failed and borked GRUB in the process. I have been able to restore GRUB.  I performed an fsck on the drive, it found a corrected a few errors. I then reformatted the partition that I use for Studio and attempted another install it has failed again and indicated a problem with the CD/DVD media.  I am using a USB and did the sha-256 checksum on the file.

Next I downloaded 19.10 knowing that 20.04 is still in not officially released and wondered if there may be a bug causing the problem I am having.  This install also fails.  I wiped the drive went back to install 20.04 and saved the contents of /var/log if any of that would assist in finding the problem.

In reading the forums I noted some who had similar problems and their HDD/SSDs were failing. According to smartctl -a /mydrive  "SMART oreall-health self-assessment test result: PASSED"

I can post any of the logs or results of other pertinent test.

Thank you for your assistance.
M@

---

### Post by TheFu on 2020-04-14
Post the SMART test results as text, please.  Use code tags so everything lines up in these forums.

Usually a few partitions are required to install Linux on a modern computer.  An EFi partition, perhaps a /boot/ partition, perhaps a swap partition, the / and /home and perhaps /var would be handy.  We really need to see facts to help.  There's a **boot-info** script which can provide the facts we need.  it will post comprehensive data to an anonymous pastebin location so you can simply provide the URL back here.

---

