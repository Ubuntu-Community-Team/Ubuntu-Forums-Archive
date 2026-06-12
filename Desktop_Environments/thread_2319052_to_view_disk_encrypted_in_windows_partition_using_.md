---
title: "to view disk encrypted in windows partition using ubuntu"
date: 2016-03-31
forum: Desktop Environments
---

### Post by Vavar_N on 2016-03-31
I have  two partitions in my laptop.One for windows while other is for ubuntu.I have encrypted a disk in windows using bit locker and i cant view it in Ubuntu.What can i do??? Kindly post your replies.

---

### Post by QDR06VV9 on 2016-03-31
Make two folders, /media/bitlocker and /media/mount:
```
sudo mkdir /media/bitlocker /media/mount
```

Download and then extract [URL="http://www.hsc.fr/ressources/outils/dislocker/download/"]Dislocker.

[/URL]
Install some needed packages:

```
sudo apt-get install libfuse-dev
```
also needed this: **"sudo apt-get install libpolarssl-dev"** - otherwise make would fail

Change directory to the dislocker/src folder:
```
cd dislocker/src
```

Then install dislocker:

```
sudo make
sudo make install

```
Identify your encrypted parition:
```
sudo fdisk -l
```

Now you can decrypt using:

```
sudo dislocker -r -V /dev/sdaX -p[COLOR=#ff0000]1536987-000000-000000-000000-000000-000000-000000-000000[/COLOR] -- /media/bitlocker

```

You should replace **"1536987-000000-000000-000000-000000-000000-000000-000000"** with your recovery password.

OR if u dont have recovery password,decrypt using your user password:
```
sudo dislocker -r -V /dev/sdaX -[COLOR=#ff0000]uPASSWORD[/COLOR] -- /media/bitlocker

```
You should replace uPASSWORD with your User password.

Now mount the file:
```
sudo -i
cd /media/bitlocker
mount -o loop dislocker-file /media/mount
```

Now you can move to the /media/mount folder and see your decrypted data.
Credit:To Maythux

---

