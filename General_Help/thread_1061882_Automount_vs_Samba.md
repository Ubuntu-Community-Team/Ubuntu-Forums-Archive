---
title: "Automount vs Samba"
date: 2009-02-06
forum: General Help
---

### Post by stlucifer on 2009-02-06
Hi all

first of all, i'm new here in the forum and to the whole ubuntu/unix thing ... so be patient if i post some noob questions ^_^

Today i noticed a strange behaviour in ubuntu 8.10 ...

After installing the samba server (sudo apt-get install samba) it fails to mount any usb drive.
I can see the drive icon in the places menu, but i can't mount/access it.
Before installing samba everything worked fine.

Anyother encountered the same problem? Any suggestion on how resolve it?

Thanks anyone ;)

---

### Post by dannyboy79 on 2009-02-06
after you plug in the usb drive or usb stick, please post the output of this command

```
sudo mount
```

---

### Post by stlucifer on 2009-02-06
sudo mount:
```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

but looks like it's a bit more complicated than what i tought ...

a do access remotely to my ubuntu-server through freenx-server

if i plug a usb key in the server when i'm logged through freenx, the drive won't mount

but if there's a "local" session of the same user (i plugged a monitor and a keyboard to the server) on the server, the drive mount on both sessions

i'm gonna make more tests ...

---

### Post by stlucifer on 2009-02-06
it's possible that some needed service doesn't start when i login through freenx-server?

because the drive pops out (in both sessions) as soon as i login with the same user locally

edit:

if both sessions are present (remote and local) the sudo mount command shows this two additional rows:
> gvfs-fuse-daemon on /home/cyberpunk/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=cyberpunk)
/dev/sdb on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


if i unmount the drive in the local session i can't re-mount it from remote. but i can use and unmount it from remote and eventually re-mount it locally.

i ... feel ... pain ... in the head ...

---

### Post by dannyboy79 on 2009-02-06
it almost sounds like you don't have sudo capabilities when you're connected thru freenx? can you perform any other sudo commands when running remotely?

---

### Post by stlucifer on 2009-02-06
i googled more about freenx and remotely mounting usb drives
and it seems to be a common problem (not related to samba) but i had no luck resolving it so far

the rest of the system works fine, for what i've tested, through freen but if i need to mount a usb drive i must do 'sudo mount -a' and only root can use (write/unmount) that drive (i override the problem using 'gksudo nautilus')

i've found other people here in the forum having the same issue (like Prajna) but it seems that no one resolved it

any suggestion is welcome ...

---

