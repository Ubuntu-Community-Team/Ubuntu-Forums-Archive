---
title: "samba Windows shares slow system"
date: 2006-01-02
forum: Desktop Environments
---

### Post by DoomedTX on 2006-01-02
I've been using samba fairly successfully for about 2 years, first with Mandrake 9.1-10.0 and then with Ubuntu. Because I want the Windows shares available in the Save dialog, I mount them on startup like so:

```

//192.168.1.3/MP3       /mnt/MP3        smbfs credentials=/etc/samba/ellen,dmask=777,fmask=777        0       0

//192.168.1.3/pix       /mnt/pix        smbfs   credentials=/etc/samba/ellen,dmask=777,fmask=777        0       0

//tedxp/D       /mnt/TedShared  smbfs   credentials=/etc/samba/tedxp,dmask=777,fmask=777        0      0
```

This works great except for when one of the Windows machines is powered down or rebooted. When I was first using samba back in MDK 9.1, the shares would simply disappear when the Windows machine went away and then reappear when it restarted.

However, since MDK 9.2 and on through into Ubuntu, whenever I lose one of the Windows shares it takes about a full minute to do anything involving listing files such as opening a save dialog or changing directories in nautilus.

I discovered that the umount -l option will let me get rid of the Windows shares and then later remount them when the Windows machine comes back online; I even wrote a simple script to do it. It is getting tedious to have to run this script every time the Windows machines are rebooted (3-10 times a day between the 2 Windows boxes). If I forget to run the script I find out as soon as I try opening Nautilus or saving a file and get the 1 minute wait.

Is there any way to fix my samba setup or something else to alleviate the problem or am I stuck?

---

