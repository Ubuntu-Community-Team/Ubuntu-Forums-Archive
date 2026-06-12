---
title: "manual flashdrive mounting help"
date: 2009-03-26
forum: General Help
---

### Post by chrisruls00 on 2009-03-26
I play some windows games off of my flashdrive, one of them is Diablo II. Diablo II saves the install directory and save directory in the fake registry for wine, so it needs to be mounted to the same folder everytime. I first tried using the "mount" command, but soon found out that since you need to use sudo to use mount that the flashdrive is mounted with root as the owner, so my games will not save. I then found out about the /etc/fstab file, so I tried setting it up in there with the user command, but since it is a flashdrive, the device name under the /dev/ directory changes everytime, so I must re-start my computer a lot. Is there a way to manually mount it so that it is mounted under my user and in the same mount point everytime using the "mount" command?

---

### Post by aeiah on 2009-03-26
i suggest doing it in fstab. see here:
[http://www.linuxforums.org/forum/redhat-fedora-linux-help/58151-mount-user-not-so-simple-solved.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/58151-mount-user-not-so-simple-solved.html)

now, i know you said that the problem is that the /dev/ name changes every time. in fstab instead of specifying /dev/sda1 you can specify a UUID. im no expert so you'll have to read up i guess but i think this should be enough to identify the usb device each time it's plugged in and not mistake it for any other, or get confused when it pops up under a different name. you'll also have to find out how to get hold of the UUID for the usb partition :p

one of my fstab entries is as follows, for example (this isnt for a usb flash drive obviously):

```
UUID=a193e00f-0dea-44c3-8e16-97f25ea8d0bf /home     ext3      defaults   0   2
```

---

### Post by chrisruls00 on 2009-03-26
Thanks! That ended up helping a WHOLE lot!:)

---

