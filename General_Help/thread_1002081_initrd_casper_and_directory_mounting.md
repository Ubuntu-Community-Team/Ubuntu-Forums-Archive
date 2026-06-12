---
title: "initrd casper and directory mounting"
date: 2008-12-04
forum: General Help
---

### Post by prozacgod on 2008-12-04
I was poking around in the initrd and in the scripts/casper file and found this...

```

is_casper_path() {
    path=$1
    if [ -d "$path/casper" ]; then
        if [ "$(echo $path/casper/*.squashfs)" != "$path/casper/*.squashfs" ] ||
            [ "$(echo $path/casper/*.ext2)" != "$path/casper/*.ext2" ] ||
            [ "$(echo $path/casper/*.dir)" != "$path/casper/*.dir" ]; then
            return 0
        fi
    fi
    return 1
}

```

to me this means that any file ending in ".dir", ".ext2", ".squashfs" is considered valid for the casper root image

the idea of bind-mounting sounded like an easy way to install and remove software and test the system, on say a virtual machine - for creating custom installs, .. without having to repack the FS every time.

but ...

further down in the file we get this ...
```

    if [ -n "${SHOWMOUNTS}" ]; then
        for d in ${rofslist}; do
            mkdir -p "${rootmnt}/casper/${d##*/}"
            case d in
                *.dir) # do nothing # mount -o bind "${d}" "${rootmnt}/casper/${d##*/}"
                    ;;
                *) mount -o move "${d}" "${rootmnt}/casper/${d##*/}"
                    ;;
            esac
        done
        # shows cow fs on /cow for use by casper-snapshot
        mkdir -p "${rootmnt}/cow"
        mount -o bind /cow "${rootmnt}/cow"
    fi


```

here it looks like the working part of the script is neutered?

so my question, does this work ?  can I bind mount a .dir folder?  or do I have to modify my initrd  - also can you do a read-only bind mount?  or does the unionfs/aufs stuff take care of that implicitly.

---

