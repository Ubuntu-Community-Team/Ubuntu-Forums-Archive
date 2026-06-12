---
title: "How to schedule Disk Check at startup?"
date: 2011-06-04
forum: Desktop Environments
---

### Post by KonfuseKitty on 2011-06-04
When I was using Lucid 10.04, after every 100 startups, the Disk Check would automatically run on startup. Since I upgraded to Maverick 10.10, this seems to happen a lot less frequently. Where is the setting so I can set this back to every 100 startups? (Or even less, I would set it to 20.)

---

### Post by KonfuseKitty on 2011-06-05
Bump. Or should I repost this in General Help? I might have picked the wrong forum.

---

### Post by wildmanne39 on 2011-06-05
> **KonfuseKitty said:**
> When I was using Lucid 10.04, after every 100 startups, the Disk Check would automatically run on startup. Since I upgraded to Maverick 10.10, this seems to happen a lot less frequently. Where is the setting so I can set this back to every 100 startups? (Or even less, I would set it to 20.)Hi, this is the command to get it to run the next time you start the system.
```
sudo touch /forcefsck
```It is suppose to check every 30 times it starts, but if you hit the button earlier to get it to boot quicker it will skip it. I do not know how to change the setting.

---

### Post by KonfuseKitty on 2011-06-07
Thanks for the tip, it worked. If anyone knows how to change the startup setting, please post.

---

### Post by Rubi1200 on 2011-06-07
Hi,
you can use this command to check the mount count (last and current) and next check:
```
sudo tune2fs -l /dev/sdXY | grep -i -e "mount count" -e "check"
```change XY to reflect your partition e.g. sda1

To change the default value, which is every 30 mounts, use this command:
```
sudo tune2fs -c 50 /dev/sdXY
```In this example, the value is 50 but you can change it to pretty much whatever you want.

In my opinion, you should not change the defaults, but if you must I recommend not setting it lower than 20 and not higher than 50.

---

### Post by KonfuseKitty on 2011-06-07
Great, that's what I needed. I've set it to 20 and also noted there's an -i(nterval) option, set to 6 months, and I changed it to 1 month. I must say I was surprised that the Mount Count was set to 27 on root partition and 22 on home partition. I thought it was set a lot higher, as the checks have been very rare. I'll see how it goes now that I've changed it. Problem solved. :)

---

### Post by Rubi1200 on 2011-06-07
Excellent, I am glad you found this useful for dealing with your situation.

Enjoy :)

---

