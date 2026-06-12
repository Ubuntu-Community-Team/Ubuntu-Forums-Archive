---
title: "Unable to mount new media"
date: 2006-06-12
forum: Desktop Environments
---

### Post by RajivNair on 2006-06-12
Hello Everyone,
I today added an additional HDD to my existing one,i formatted it with ext3 partition,it shows up unmounted in my "Storage Media" place in Kubuntu.Whenever i try to mount it by right-clicking and choosing the option "mount", it throws up an error:-
  
  "mount: can't find /dev/hdc1 in /etc/fstab or /etc/mtab
   Please check that the device is plugged correctly."

Can anyone suggest, what im doing wrong and any place where i can get help on mounting and writing data into the new partition.

Thank You.

---

### Post by taurus on 2006-06-12
Open a terminal and type
```

sudo mkdir /mnt/storage

```
Now, you need to edit your /etc/fstab to include an entry for it as (from a terminal again)
```

sudo nano /etc/fstab

```
Then, add the following line to it...
```

/dev/hdc1  /mnt/storage  ext3  defaults  0  1

```
Save it and at the promtp, mount it with
```

sudo mount -a

```

---

