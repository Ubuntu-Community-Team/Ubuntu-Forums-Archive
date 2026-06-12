---
title: "mldonkey on init"
date: 2005-07-17
forum: Desktop Environments
---

### Post by msxuser on 2005-07-17
How I can initiate mldonkey in the starting of the system? I have mldonkey-distrib-2.5.30.17.tar.bz2 from spiralvoice.

I have this script on init, but dont work :(

root@host:/var/lib/mldonkey # /etc/init.d/MLDonkey start
Starting mldonkey:
root@host:/var/lib/mldonkey #                 

Regards

---

### Post by varunus on 2005-07-17
You need to make the proper symlinks for the script to be run when you boot up.  Do the following:

```
cd /etc/rc2.d
sudo ln -s /etc/init.d/MLDonkey S99MLDonkey
[repeat for rc3.d, rc4.d, rc5.d]
```

That should work.  It will create bootup scripts for you.

---

### Post by msxuser on 2005-07-18
the  symlinks I have them created by means of:

chmod +x /etc/init.d/MLDonkey
update-rc.d MLDonkey defaults

but continuous without working :(


[QUOTE=varunus]You need to make the proper symlinks for the script to be run when you boot up.  Do the following:

```
cd /etc/rc2.d
sudo ln -s /etc/init.d/MLDonkey S99MLDonkey
[repeat for rc3.d, rc4.d, rc5.d]
```

That should work.  It will create bootup scripts for you.[/QUOTE]

---

