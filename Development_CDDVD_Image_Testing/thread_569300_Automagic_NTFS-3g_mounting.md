---
title: "Automagic NTFS-3g mounting?"
date: 2007-10-06
forum: Development CD/DVD Image Testing
---

### Post by BrandonPerry on 2007-10-06
Hi, I am editing an initrd.gz and was just wondering if this bit of code would work assuming ntfs-3g has been installed...

    fstype=$(get_fstype "${devname}")
    if is_supported_fs ${fstype}; then
       if "${fstype}" = "ntfs"
         ntfsfix "${devname}"
         mount -t ntfs-3g "${devname}" $mountpoint
       fi
        mount -t ${fstype} -o ro "${devname}" $mountpoint || continue
        if is_casper_path $mountpoint; then
            echo $mountpoint
            return 0
        else
            umount $mountpoint
        fi
    fi

I have no way to test this for a week or so, so I figured someone a bit more well versed in shell-scripting and the initrd.gz would be able to answer this for me before I get back home.

---

