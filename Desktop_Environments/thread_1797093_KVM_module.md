---
title: "KVM module"
date: 2011-07-04
forum: Desktop Environments
---

### Post by cybernet on 2011-07-04
i installed KVM using [https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

for some reasons i want to uninstall it

i removed the programs installed earlier and rebooted but the KVM module still loads with the kernel ( at least that what VirtualBox says )

the question is how can i completely remove KVM ?

ubuntu lucid

---

### Post by cybernet on 2011-07-08
no one knows :confused:

---

### Post by cybernet on 2011-07-09
for those who found this thread with google and didn't got their answer
is
```
sudo modprobe -r kvm-intel
```
```
sudo modprobe -r kvm-amd
```

i guess you can figure out the difference :)

---

