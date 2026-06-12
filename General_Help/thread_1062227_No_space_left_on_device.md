---
title: "No space left on device"
date: 2009-02-06
forum: General Help
---

### Post by pgillhaus on 2009-02-06
I seem to be having trouble downloading files which are saved to /tmp
When I use the python easy_install utility I get this message:
```
~$ sudo easy_install --upgrade lxml
Searching for lxml
Reading http://pypi.python.org/simple/lxml/
Reading http://codespeak.net/lxml
Best match: lxml 2.2beta2
Downloading http://cheeseshop.python.org/packages/source/l/lxml/lxml-2.2beta2.tar.gz
error: No space left on device

```

When clicking on a file in firefox, I get this message:
```
There is not enough room on the disk to save /tmp/3JCeq7Jr.part.

Remove unnecessary files from the disk and try again, or try saving in a different location.
```

However, if I right-click and save-as, I can easily save the file to my home directory.  When running df, I get this:

```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb6              12G  9.6G  1.9G  84% /
varrun                189M  224K  188M   1% /var/run
varlock               189M     0  189M   0% /var/lock
udev                  189M   56K  189M   1% /dev
devshm                189M  192K  188M   1% /dev/shm
lrm                   189M   39M  150M  21% /lib/modules/2.6.24-19-generic/volatile
overflow              1.0M  104K  920K  11% /tmp
tmpfs                 189M   39M  150M  21% /lib/modules/2.6.24-23-generic/volatile
gvfs-fuse-daemon       12G  9.6G  1.9G  84% /home/philroot/.gvfs
/dev/sdb1              24G   16G  7.8G  67% /media/disk

```
I've deleted the contents of /tmp, but still no dice.  Any advice?

---

### Post by lykwydchykyn on 2009-02-06
Notice in the list /tmp is mounted on "overflow".  I've seen this before on my system when I maxed out the root fs.  Some how it remounted /tmp on this "overflow" filesystem, which I can only guess is some kind of RAM disk (not sure about that, anyone know?)

Anyway, clearing enough space on / (which you have) and rebooting sorted me out.

---

### Post by taurus on 2009-02-06
Try

```
sudo apt-get clean
sudo apt-get autoremove
df -h
```

---

