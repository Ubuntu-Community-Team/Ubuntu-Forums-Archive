---
title: "Encrypted root - initramfs cannot open volume"
date: 2009-04-15
forum: General Help
---

### Post by jorg_andersson on 2009-04-15
Hello,
I'm trying to set up encrypted root with luks. The initramfs I have doesn't seem to work. It can't open the device at boot. I also tried to use cryptsetup in the busybox shell but it fails with an error about device-mapper couldn't allocate tfm or something. 

/etc/initramfs-tools/modules
```

# List of modules that you want to include in your initramfs.
#
# Syntax:  module_name [args ...]
#
# You must run update-initramfs(8) to effect this change.
#
# Examples:
#
# raid1
# sd_mod
dm_mod
dm_crypt
aes

```

/etc/hooks/cryptroot
```

PREREQ=""

prereqs()
{
        echo "$PREREQ"
}

case $1 in
prereqs)
        prereqs
        exit 0
        ;;
esac

if [ ! -x /sbin/cryptsetup ]; then
        exit 0
fi

. /usr/share/initramfs-tools/hook-functions

mkdir -p ${DESTDIR}/etc/console-setup
cp /etc/console-setup/boottime.kmap.gz ${DESTDIR}/etc/console
copy_exec /bin/loadkeys /bin
copy_exec /bin/chvt /bin
copy_exec /sbin/cryptsetup /sbin

```

/etc/initramfs-tools/scripts/local-top/cryptroot
```

EREQ="udev"

prereqs()
{
        echo "$PREREQ"
}

case $1 in
# get pre-requisites
prereqs)
        prereqs
        exit 0
        ;;
esac

/bin/loadkeys -q /etc/console-setup/boottime.kmap.gz

echo 'blacklist padlock_aes' >> /etc/modprobe.d/blacklist
modprobe -Qb dm_crypt
modprobe -Qb aes

# The following command will ensure that the kernel is aware of
# the partition before we attempt to open it with cryptsetup.
/sbin/udevadm settle

if grep -q splash /proc/cmdline; then
    /bin/chvt 1
fi
sleep 2

/sbin/cryptsetup luksOpen /dev/sdc4 cryptoroot
if grep -q splash /proc/cmdline; then
       /sbin/usplash -c &
       sleep 1
fi

```

/etc/crypttab 
```

# <target name> <source device>         <key file>      <options>
cryptroot       /dev/sdc4               none            luks

```

/etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/sdc4
UUID=98f3a4c9-bcc1-4963-9154-65958186cc80 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdc2
UUID=1265eabd-808e-4167-829b-d3e91bdac2aa /boot           ext2    relatime        0       2
# /dev/sdc3
UUID=317c6974-2fb1-448b-bac0-e51a04ff7b37 none            swap    sw              0       0
/dev/sde1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

```

And as you can see that is the uuid of my encrypted loopback partition. 

Thank you.


Yours sincerely,
Jorg Andersson

---

