---
title: "multipath uid option"
date: 2009-05-26
forum: General Help
---

### Post by dowlingw on 2009-05-26
Hi Folks,

Running ubuntu/hardy (LTS) here, and am having some issues configuring a multipath block device for MySQL to write InnoDB tablespace to.

I've tried using the 'uid' configuration option in multipath.conf, however it looks like that argument isn't supported in the current version of multipath that ships with LTS.

```
root@host:/dev/mapper# cat !$
cat /etc/multipath.conf
multipaths {
        multipath {
                wwid    360a980005033526f434a4d5167656e65
                alias   na01_innodb1
                uid     mysql
        }
}
```


```
root@host:/dev/mapper# ls /dev/mapper/ -al
total 0
drwxr-xr-x  2 root root      80 2009-05-27 01:52 .
drwxr-xr-x 12 root root   14200 2009-05-27 01:52 ..
crw-rw----  1 root root  10, 62 2009-05-19 23:26 control
brw-rw----  1 root disk 254,  0 2009-05-19 23:26 na01_innodb1

```

A little bit stumped on how I'm going to give the mysql user permission to write to the block device.

Any ideas welcome, as this is the first time I've had to use multipath for a non-root user's use.

---

### Post by dowlingw on 2009-05-26
How embarassing, I've just realised the solution is staring me in the face.

I've added the MySQL to the disk group and it should work now :)

---

