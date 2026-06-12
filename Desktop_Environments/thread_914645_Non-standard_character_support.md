---
title: "Non-standard character support"
date: 2008-09-09
forum: Desktop Environments
---

### Post by kramer2718 on 2008-09-09
<p>So I have this NAS (specs here: [http://www.lacie.com/us/products/product.htm?pid=10844](http://www.lacie.com/us/products/product.htm?pid=10844)) that I had from way back when I used to run Windows (don't anymore, Windows doesn't work so well for me--that's another topic, though).  It isn't really big enough to use for backups.  It also is sealed so you can't swap out hds.  I am using it for storage convenience, though (it's nice that I can't mount it over Wifi).</p>

Anyway, I have it mounted over samba/cifs (not sure the difference) to my main box and would like to back it up (just got a hot swappable usb enclosure and a couple of cheap hds).  So I tried to copy (via rsync)  the files from my NAS to my backup disks (backup disks are formatted with NFS) It seemed to work okay except that it barfed on a bunch a files with weird characters in them that don't display correctly from the bash shell.  rsync gives this sort of error for each:
[FONT="Courier New"]file has vanished: "/mnt/edmini/c_music/Gal Costa/Aquele Frevo Axe [1999]/14 Sert?o.mp3"[/FONT]

This line in /etc/fstab mounts the NAS:

//192.168.2.2/musica /mnt/edmini smbfs credentials=/etc/.fstab-edmini-credentials,auto,users,umask=777,intr 0 0

I'm not sure what filesystem is on the NAS--tried googling for it.  Is there a command that I can run that would tell me?  I also have no idea how those file names are encoded.  Whatever Windows XP chose to do...  Is there a way that I could find out?  Is there any way that I could get them to copy--even better to change their names so that rsync will copy them (so that my backup routine can work repeatably)?  Or is there a way that I could just get Linux to recognize the aforementioned encoding?

Any help would be appreciated.

---

### Post by Pro-reason on 2008-09-11
I don't know if it will help, but you could try this tool:
```

sudo apt-get install utf8-migration-tool
utf8migrationtool

```

---

