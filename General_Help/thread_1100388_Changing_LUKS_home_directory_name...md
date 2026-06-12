---
title: "Changing LUKS /home directory name.."
date: 2009-03-19
forum: General Help
---

### Post by hopelessone on 2009-03-19
Hi,

I just did a full encrypted install..

and i wanted to change the name from **sda4_crypt** to **home_crypt**

so i changed them:

fstab:
Old > /dev/mapper/sda4_crypt /home           ext3    defaults        0       2
New > /dev/mapper/home_crypt /home           ext3    defaults        0       2

crypttab:
Old > sda4_crypt /dev/disk/by-uuid/3411509d-99d1-4ac5-9d25-22e0563d0946 /root/keyfile luks
New > home_crypt /dev/disk/by-uuid/3411509d-99d1-4ac5-9d25-22e0563d0946 /root/keyfile luks
is that it?

reboot and hope for the best?

Thanks..

---

### Post by hopelessone on 2009-03-19
Do I have to Set up the device mapping again?

> cryptsetup luksOpen /dev/sda4 home_crypt

something like this?

---

### Post by hopelessone on 2009-03-19
*anyone* know what to do before i reboot?

---

### Post by hopelessone on 2009-03-22
yes it can be done as per first post...

But don't change the /root one...had many headaches sortin that one back....

---

