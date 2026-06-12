---
title: "Samba shares through Gnome open file widget"
date: 2007-06-18
forum: Desktop Environments
---

### Post by brendanarnold on 2007-06-18
I have all my data on a samba share on a fileserver. I can access this fine through Nautilus however when I get the Gnome 'open file' widget (for example when selecting which folders for Beagle to index) the samba shares are not displayed.

I read an earlier post in this forum which bemoaned the fact that Nautilus does not mount smb shares to the filesystem (which would fix this) but I was wondering if there was a temporary solution to this?

I tried entering the smb:// url but it does not work.

Regards,

Brendan

---

### Post by toobuntu on 2007-06-19
the gnome-vfs virtual filesystem does not make samba shares available to non gnome-integrated apps.

to make windows shares available to those apps, you will have to mount them using cifs:

e.g.
```
sudo mkdir /mnt/samba && sudo mount -t cifs //<server>/<share> /mnt/samba -o nocase,noacl,setuids,user=<username>,file_mode=0777,dir_mode=0777
```

---

### Post by brendanarnold on 2007-06-20
thanks, that worked great!

i should probably point out that the above did not work until the smbfs package was installed which augments the mount command with the cifs vfstype.

also i had to change the command slightly to,

mount -t cifs //<server>/<share> /mnt/samba -o nocase,noacl,setuids,user=<username>,file_mode=0777,dir_mode=0777

(that is explicitly stating 'user' rather than just 'u' and taking a space out of 'dir_mode')

regards,

brendan

---

