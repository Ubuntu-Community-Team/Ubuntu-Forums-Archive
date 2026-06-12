---
title: "Ubuntu 14.04 -&gt; SDLMAME make Error 127"
date: 2014-06-25
forum: Gaming &amp; Leisure
---

### Post by KingHanco on 2014-06-25
How come I can't make mame64 and mess64 on another hard drive? It will run make but I get a permission warning screen at the end and then it stop make with an error. I had to moved all the source back onto Ubuntu hard drive from the Windows 8.1 hard drive.

/home/gateway/UME/source/trunk < Ubuntu

/media/gateway/Files-1/UME/source/trunk < Windows

Is there away to bypass this permession? Just trying to keep the source all in one place.

Did mount and got these infos.

```

gateway@gateway-GT5628:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
/home/gateway/.Private on /home/gateway type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=3906eda50ee365f8,ecryptfs_fnek_sig=c93c80cd6919dd14)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=gateway)
/dev/sdg1 on /media/gateway/Files-1 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
/dev/sdh1 on /media/gateway/Files-2 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
gateway@gateway-GT5628:~$

```

Error I was talking about.

```

obj/sdl64/build/m68kmake obj/sdl64/emu/cpu/m68000 src/emu/cpu/m68000/m68k_in.c
make: execvp: obj/sdl64/build/m68kmake: Permission denied
make: *** [obj/sdl64/emu/cpu/m68000/m68kops.c] Error 127
make: *** Waiting for unfinished jobs....
make: *** wait: No child processes.  Stop.

```

Anyway I tried get help here. [http://forums.bannister.org/ubbthreads.php?ubb=showflat&Number=94776#Post94776](http://forums.bannister.org/ubbthreads.php?ubb=showflat&Number=94776#Post94776) and nobody there know how to bypass the permission.

---

