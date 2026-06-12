---
title: "New Mounted partition read only!"
date: 2005-12-19
forum: General Help
---

### Post by thermopyl on 2005-12-19
Hi

I have mounted a new partition via my fstab:

/dev/hda2	/media/hda2	ext3	defaults,errors=remount-ro 0 1

However I can only use this as read only for some reason; not very useful as this is my backup partition!

Can anyone tell me how to resolve please?
Thanks

---

### Post by Ocxic on 2005-12-19
try 
/dev/hda2 /media/hda2 ext3 defaults,errors=remount-ro 0 0

---

### Post by thermopyl on 2005-12-19
Hi

thanks for the quick reply but has not worked...i even tried 
/dev/hda2 /media/hda2 ext3 defaults
but i still have the same problem...

---

### Post by Ocxic on 2005-12-19
unmount the drive and try mounting it manually with
```

sudo mount /dev/hda2 /media/hda2

```

---

### Post by aysiu on 2005-12-19
Can you chown it? Try ```
sudo chown -R thermopyl:thermopyl /media/hda2
```

---

### Post by priyaaank on 2006-04-08
"sudo chown -R thermopyl:thermopyl /media/hda2"

what does thermopyl:thermopyl means...
Pardon me I am just a newbie... still stumbling my way around! :D

---

### Post by Ocxic on 2006-04-08
chown chagnes the files owner and group permisions, jsut change the thermopyl to your username on the computer for me it would be

sudo chown -R admin:admin /media/hda2

the -R option makes it change the owners for every file on /dev/hda2

---

