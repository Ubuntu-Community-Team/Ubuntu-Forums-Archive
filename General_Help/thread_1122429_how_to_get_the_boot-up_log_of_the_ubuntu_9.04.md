---
title: "how to get the boot-up log of the ubuntu 9.04"
date: 2009-04-11
forum: General Help
---

### Post by youxiang95 on 2009-04-11
I saw some fialed message(After the message "reading file needed to boot") when the ubuntu was booting up and it's moving too fast for me to read. I want to check what's wrong with this failed.I check the dmesg after login but got not any failed message. and I check the /var/log/boot but got nothing except one line "Nothing has been logged yet".I also have changed the /etc/default/bootlogd by changing the value into "yes" and still no effort. 

Waiting for the resolve. Thanks!

---

### Post by Peter09 on 2009-04-11
I cannot help you find the messages but just note to say that you can get what appear to be error messages but are not during the boot sequence.

For instance there is often a message which is something like -

"Failed to get Hibernation File" - or similar wording.

It just means that the machine was not in a hibernation state when booted.

---

### Post by youxiang95 on 2009-04-11
more confusion with your words:confused:

---

### Post by Elfy on 2009-04-11
Try a look in messages - System Logs

or from a terminal you could do

```
cat /var/log/messages |grep fail
```

---

### Post by youxiang95 on 2009-04-11
I used the command above and got some fail message like "read_super_block: bread failed (dev sda2, block 8, size 1024)".I used "df -T" to check the partition info but there was not any partition named /dev/sda2 deing mounted. And I can't mount /dev/sda2 too!Is it possible that /dev/sda2 is the swapping partition? Anyway, I think these messages have nothing to do with the failing output when booting.

I used GParted to check the disk and found that /dev/sda2 is the extended partition while there's a another primary partition which is install windows system.

---

