---
title: "Mounting mobile phones"
date: 2022-04-17
forum: Desktop Environments
---

### Post by oygle on 2022-04-17
I've been using the following for years to mount a Samsung Galaxy S5

```
go-mtpfs ~/myphone
```

and it mostly worked. That is, if I got the correct sequence of attaching, press 'allow' on the phone, maybe sometimes a restart ,etc.

Now in Kubuntu 21.10 it refuses to work, either

> 2022/04/17 10:30:37 detect failed: no MTP devices found


OR

> 2022/04/17 10:40:36 OpenSession failed: LIBUSB_ERROR_IO; attempting reset
2022/04/17 10:40:38 selectStorages failed: EOF

searched many posts and solutions , nothing worked for me. Then came across a package called **android-file-transfer **and it is actually in the official repositories ( see [https://packages.ubuntu.com/search?keywords=android-file-transfer&searchon=sourcenames](https://packages.ubuntu.com/search?keywords=android-file-transfer&searchon=sourcenames) ). Installed it, and after a few mins of working out how to deal with conflicts (the GUI finds anything else that has the MTP device and you can kill the process), it works just fine.

I needed to mount the phone, so ..

```
aft-mtp-mount ~/myphone
```

and that was it, done. The usual **umount** with

```
fusermount -u  ~/myphone
```

So, just recommending this package. There is good support for it at [https://github.com/whoozle/android-file-transfer-linux](https://github.com/whoozle/android-file-transfer-linux) and [https://whoozle.github.io/android-file-transfer-linux/](https://whoozle.github.io/android-file-transfer-linux/)

Problem solved.  :D

---

### Post by ActionParsnip on 2022-04-17
If you install openssh-server then you can use AndFTP and send data to and from the system over WiFi using SFTP.

---

