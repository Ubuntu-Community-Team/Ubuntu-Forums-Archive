---
title: "Make BMP play music across the network?"
date: 2006-01-04
forum: General Help
---

### Post by Greeface on 2006-01-04
I was just wondering if I could make Beep Media Player play music from across the network somehow.  I prefer BMP over Totem, but I suppose it isn't that big of an issue.  Thanks

---

### Post by sciurus on 2006-01-04
What OS is the computer where the music is stored running? If it's Linux or OS X, you have lots of possibilities for sharing the files, but the primary ones are ssh, samba, and daap (ie- itunes). If it's Windows, you'll probably want to use the built-in file sharing of which samba is the Linux implementation.

Sharing using [daap]("http://dotnet.org.za/matt/articles/48417.aspx") isn't ideal for you since Beep Media Player doesn't suport it. However, it should become a good option down the road if Dapper Drake ships with a daap-enabled [Rhythmbox]("http://gridpt1.fe.up.pt/mlopes/blog/index.php/2005/12/24/rhythmbox-092-deb-for-ubuntu-breezy/").

If the files are shared using Samba or Windows, then smbfs is the ideal solution. It lets you mount the share just like any other filesystem. Look up smbmount for more information.

If the files are on a computer running ssh, [sshfs]("http://www.ubuntuforums.org/showthread.php?t=103860") allows access similar to smbfs, but more securely.

---

### Post by Greeface on 2006-01-04
Yeah, they're shared on a windows computer, so I'll look into the SMBMount that you mentioned.

Thanks

---

### Post by Greeface on 2006-01-04
Okay, I tried messing around with the SMBMount stuff, but I almost completely screwed some stuff up, so do you know of any good tutorials out there for it?  I'm not too good at this type of stuff.

---

### Post by sciurus on 2006-01-06
[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

Also the "Mounting a samba share" section at [https://wiki.ubuntu.com/SettingUpSamba](https://wiki.ubuntu.com/SettingUpSamba)

---

### Post by Greeface on 2006-01-12
Wow, that works nice!  Thanks for the tip, this helps a lot.

---

