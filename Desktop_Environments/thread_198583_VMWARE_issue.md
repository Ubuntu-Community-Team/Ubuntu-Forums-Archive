---
title: "VMWARE issue"
date: 2006-06-17
forum: Desktop Environments
---

### Post by totalnoob on 2006-06-17
I'm using the tutorial at this link [http://www.ubuntuforums.org/showthread.php?t=84275](http://www.ubuntuforums.org/showthread.php?t=84275)

here is the out put when I try to create the vm file

:/home/kryoblue# wine qemu-img.exe create -f vmdk WindowsXPPro.vmdk 2G Formating 'WindowsXPPro.vmdk', fmt=vmdk, size=2097152 kB
wine: creating configuration directory '/root/.wine'...
wine: '/root/.wine' created successfully.
wine: could not load L"c:\\windows\\system32\\qemu-img.exe": Module not found

is this a bad install of qumu, or something else? Thanks

---

### Post by GarlicFish on 2006-06-17
Sounds like you dont have the windows version of Qemu installed anywhere!

If you just want to try VMWare or just get XP working, I suggest downloading the free VMWare server.  Just fill in your details and they send you a key.

[http://www.vmware.com/download/server/](http://www.vmware.com/download/server/)

This allows you to build virtual machines with no messing about.

Of course if you are trying the Qemu route "because you can" then keep plugging and good hunting ;-)

---

