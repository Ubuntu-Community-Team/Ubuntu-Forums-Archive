---
title: "After moving /home to new partition - gnome error &quot;Unable to store value at key... &quot;"
date: 2009-05-07
forum: Desktop Environments
---

### Post by donovanh on 2009-05-07
Hi,

Today I tried following the ubuntu blog tutorial to move my /home directory to a new partition. It seemed to work at the time, with /home/username bringing up the right files, but I think that I must have copied the files wrongly. (I booted off a live-usb and used sudo cp to copy the files across, as copying within the system gave permission errors).

I fixed the first few errors with:

```

sudo chown username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username /home/username
chmod 755 /home/username

```

I then got error 256 from gconf-sanity-check-2, which I tried every recommendation I could find, eventually chown'ing everything in /home/username to username.

Along the way I've done "sudo chmod 775 /etc/gconf.xml.system" and "sudo usermod -d /home/username username".

The welcome sound now plays, but gnome doesn't load, instead giving the error that "gnome panel" is unable to store a value at key.. And among the suggestions includes something to do with NFS file locking. It seems that maybe the permissions are still wrong on the gconf files, but I cannot work out what to do.

Any help much appreciated!

D

---

