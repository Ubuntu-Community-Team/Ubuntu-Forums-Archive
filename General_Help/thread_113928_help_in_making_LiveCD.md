---
title: "help in making LiveCD"
date: 2006-01-07
forum: General Help
---

### Post by linux juggler on 2006-01-07
i was trying to make a liveCD for 4 days and i couldnt ..
here is a short description about my problem ...

i have installed Ubuntu 5.10 and then i update IT .
i have got the LiveCD of it and try to customize it but i couldnt .
i got some error in permissions on those steps :

```

$ sudo chroot mnt dpkg-query -W --showformat='${Package} ${Version}\n' > extracted_cd/casper/filesystem.manifest
sudo create_compressed_fs extracted_fs.new 65536 > extracted_cd/casper/filesystem.cloop

```
which said that i dont have the permission to edit it ;-(
then i try to make this move :
```

$sudo -s
#chroot mnt dpkg-query -W --showformat='${Package} ${Version}\n' > extracted_cd/casper/filesystem.manifest

```
then its work by this way .
but when i generate the ISO image the first one was 6XXmb 
and i try it and it boots smothly until the precomiled session .

the second one was 12xmb and i got the same error .
---------------
then i reliaze that i have to use the 5.04
and i try to customize it but then i got this errors :
```

juggler@ubuntu:~$ sudo mount -t proc proc mnt/proc
mount: mount point mnt/proc is not a directory

```
and when i try to ls it i got this errors :
```

juggler@ubuntu:~/mnt$ ls -l
ls: bin: Input/output error
ls: boot: Input/output error
ls: dev: Input/output error
ls: etc: Input/output error
ls: home: Input/output error
ls: initrd: Input/output error
ls: initrd.img: Input/output error
ls: lib: Input/output error
ls: media: Input/output error
ls: opt: Input/output error
ls: proc: Input/output error
ls: root: Input/output error
ls: sbin: Input/output error
ls: tmp: Input/output error
ls: usr: Input/output error
ls: var: Input/output error
ls: vmlinuz: Input/output error
total 3
drwxr-xr-x  2 root root 1024 2005-03-31 21:09 mnt
drwxr-xr-x  2 root root 1024 2005-04-07 00:21 srv
drwxr-xr-x  2 root root 1024 2005-03-24 00:41 sys

```

so any one have any idea abut what did i did wrong ?
ps : i didnt Un/install  any file or package .

---

### Post by linux juggler on 2006-01-08
any nwes ? 
any one have any idea ?

---

