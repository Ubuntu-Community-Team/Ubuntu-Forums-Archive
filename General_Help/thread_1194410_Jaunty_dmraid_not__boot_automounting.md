---
title: "Jaunty dmraid not  boot automounting"
date: 2009-06-22
forum: General Help
---

### Post by mike4ubuntu on 2009-06-22
Has anybody gotten dmraid "fakeraid" drives to automount during boot?  dmraid seems to setup fakeraid devices ok, but the line in fstab doesn't seem to work during boot.  However, the sudo mount -a does mount it successfully.

/etc/fstab:
```

/dev/mapper/nvidia_fbcjbheb1                  /mnt/raid       ext3    auto,rw,defaults,acl           0       0

```

I have it mirror-striped:

```

$ ll /dev/mapper
total 0
0 drwxr-xr-x  2 root root     140 2009-06-19 07:55 ./
0 drwxr-xr-x 17 root root    4860 2009-06-20 06:00 ../
0 crw-rw----  1 root root  10, 61 2009-06-19 07:54 control
0 brw-rw----  1 root disk 252,  2 2009-06-19 07:55 nvidia_fbcjbheb
0 brw-rw----  1 root disk 252,  0 2009-06-19 07:55 nvidia_fbcjbheb-0
0 brw-rw----  1 root disk 252,  3 2009-06-19 07:55 nvidia_fbcjbheb1
0 brw-rw----  1 root disk 252,  1 2009-06-19 07:55 nvidia_fbcjbheb-1

```

---

### Post by ronparent on 2009-06-22
I've encountered the same problem with a raid0 setup and reported it as a bug with launchpad. In my case the setup doesn't occur and I had to manually activate the array prior to manually mounting. There maybe some work-around available in the server forum. In my case I decided to fall back to intrepid.

My reading indicates that this may not be a prevalent problem and that the investigator may not consider it serious enough to find a solution at this time. The problem may be resolved for the next major release???

---

