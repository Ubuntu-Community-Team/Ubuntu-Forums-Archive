---
title: "Dell Vostro 1500 won't boot correctly..."
date: 2010-11-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by camn on 2010-11-22
Hello... Earlier I was using my computer and the AC adapter accadentally came unplugged (I leave the battery out because it's totally dead). So I plugged it back in and turned it back on... Then while it was booting I accadentally unplugged it again... Now it boots into GRUB (which it almost never does) And when I choose any update of Ubuntu from GRUB a shell screen shows up (can't post pictures, I'm having to post this from my phone...) and says ```
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init=bootarg
```
What happened? ;_;

---

### Post by carl4926 on 2010-11-22
> What happened? ;_;You tried your hardest to 'Jeff' it up didn't you.

Boot a live CD
Run gparted and run a check on your partitions

reboot

If it still fails come back

---

### Post by camn on 2010-11-22
> **carl4926 said:**
> You tried your hardest to 'Jeff' it up didn't you.

Boot a live CD
Run gparted and run a check on your partitions

reboot

If it still fails come back

Yeah, the LiveCD won't boot... It just gets stuck on the purple Ubuntu logo load-ey thing...

---

### Post by carl4926 on 2010-11-22
Do you have access to another computer?
So you can download partedmagic [http://partedmagic.com/download.html](http://partedmagic.com/download.html)

Boot from that. You don't even need a HD to run that. It should boot. It has gparted. Use it to do a check on your partitions.

---

### Post by camn on 2010-11-22
> **carl4926 said:**
> Do you have access to another computer?
So you can download partedmagic [http://partedmagic.com/download.html](http://partedmagic.com/download.html)

Boot from that. You don't even need a HD to run that. It should boot. It has gparted. Use it to do a check on your partitions.

Actually, I won't have computer access until tommorow... And I need the computer tonight for school...
EDIT: Got on a different computer today, burnt the disc and now my computer works, thanks :D

---

