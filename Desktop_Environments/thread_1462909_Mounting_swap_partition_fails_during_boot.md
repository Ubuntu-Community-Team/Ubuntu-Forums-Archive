---
title: "Mounting swap partition fails during boot"
date: 2010-04-26
forum: Desktop Environments
---

### Post by rclimb514 on 2010-04-26
When I recently tried to boot my laptop (running karmic) I ran into an issue where briefly after the log on screen appears, the system will crash--the display will return to startup splash screen, drop back to the text boot messages, and then go black and become unresponsive.

On one boot, I noticed an error message saying the system couldn't mount the swap partition (I haven't been able to get that back, so I can't copy the exact wording) and, after commenting out the swap line in /etc/fstab, the system boots and runs fine.

My first assumption was that my swap partition had somehow become corrupted, but I can mount it using "sudo swapon -v /dev/sda5" and that seems to work fine.

Any suggestions about how to diagnose and correct this issue would be much appreciated.

Thanks,
Michael

---

### Post by Elfy on 2010-04-26
Check the swap's UUID

```
sudo blkid
```

Then check the UUID for the swap partition in fstab

```
cat /etc/fstab |grep swap
```

Make sure they match - if not then edit fstab and correct the line there.

```
gksudo gedit /etc/fstab
```

When you are done try to turn swap on 

```
sudo swapon -a
```

---

### Post by rclimb514 on 2010-04-26
Thanks--it looks like UUID had changed and resetting it did the trick.

---

### Post by Virus666 on 2012-03-02
> **forestpiskie said:**
> Check the swap's UUID

```
sudo blkid
```Then check the UUID for the swap partition in fstab

```
cat /etc/fstab |grep swap
```Make sure they match - if not then edit fstab and correct the line there.

```
gksudo gedit /etc/fstab
```When you are done try to turn swap on 

```
sudo swapon -a
```

That does the job. Thank you!

---

