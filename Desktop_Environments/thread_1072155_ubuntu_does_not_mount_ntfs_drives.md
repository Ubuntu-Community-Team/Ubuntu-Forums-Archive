---
title: "ubuntu does not mount ntfs drives"
date: 2009-02-17
forum: Desktop Environments
---

### Post by grantcentral on 2009-02-17
I have both internal drives (for xp) and external USB drives. None of them mount under ubuntu. Is there somethimg I am missing? Win32 drives can be seen but not ntfs.

Any help would be appreciated.

---

### Post by dzark on 2009-02-17
Have you install ntfs-3g?

Try
```

sudo aptitude install ntfs-config
```

It's a little GUI that should make things a bit easier..

---

### Post by grantcentral on 2009-02-17
Is there a place to go to to find little niceties such as this?
I maybe a newby to ubuntu but not to unix.

---

### Post by grantcentral on 2009-02-17
Thanks for the app. It mounted the internal drive, but not the external USB ntfs drives.

---

### Post by dzark on 2009-02-17
Did you try System->Admin->NTFS Config Tool? Tick box to enable external drive support....

Dont ask me why this isn't ticked by default....

---

### Post by mozkill on 2009-02-17
> **grantcentral said:**
> Is there a place to go to to find little niceties such as this?
I maybe a newby to ubuntu but not to unix.

Yes, there is:  [http://www.ubuntuhq.com/wiki/index.php/Ubuntu_Howtos](http://www.ubuntuhq.com/wiki/index.php/Ubuntu_Howtos)

A few hours of reading through that WIKI and you'll be a Ubuntu/Debian expert.  Also, use Clonezilla to back up your system before you fiddle with it so that you can restore and experiment again!

---

### Post by grantcentral on 2009-02-17
Thanks for thee 'How To' site.
There is no 'NTFS' config tool in my admin menu. Is there a way to get it?

---

### Post by taurus on 2009-02-17
> **grantcentral said:**
> Thanks for thee 'How To' site.
There is no 'NTFS' config tool in my admin menu. Is there a way to get it?

Look at post #2.  

However, if you didn't use the _safely remove hardware_ option in windows when you last used the external harddrive to unmount it before you unplugged it, you need to

1.  boot into windows and safely remove it,
2.  use ntfsfix (part of ntfsprogs package) to fix it,
3.  or use the force option to mount it.

---

### Post by mozkill on 2009-02-18
like I said before.   the WIKI has everything. 


[http://www.howtoforge.com/ntfs_3g_ubuntu_feisty](http://www.howtoforge.com/ntfs_3g_ubuntu_feisty)

[http://www.howtoforge.com/ntfs_3g_ubuntu_feisty_p2](http://www.howtoforge.com/ntfs_3g_ubuntu_feisty_p2)

---

