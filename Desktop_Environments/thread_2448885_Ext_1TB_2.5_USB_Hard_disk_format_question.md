---
title: "Ext 1TB 2.5 USB Hard disk format question"
date: 2020-08-15
forum: Desktop Environments
---

### Post by xendistar2 on 2020-08-15
I have the above mentioned ext usb hard disk which I use connected to my Lenovo Laptop for backups.

I decided to wipe the enitre disk and set it backup with a single partition and formatted to ext4, I did this using gparted

When I looked at the results afterwards while it said it had completed without error it had the following:

[HTML]mkfs.ext4 -F -O ^64bit -L '' '/dev/sdb1'  00:00:31    ( SUCCESS )    64-bit filesystem support is not enabled. The larger fields afforded by this feature enable full-strength checksumming. Pass -O 64bit to rectify.
Creating filesystem with 244190208 4k blocks and 61054976 inodes
Filesystem UUID: 9bfb9f31-440c-4288-85ad-3f6961a671f5
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,
102400000, 214990848

Allocating group tables: done
Writing inode tables: done
Creating journal (262144 blocks): done
Writing superblocks and filesystem accounting information: done

mke2fs 1.45.5 (07-Jan-2020)
[/HTML]

The bit that concerns me is the second line where it says 64bit filesystem support is not enabled?? Then it says to pass the -O 64bit and looking at the first line the command it ran it looks like is has passed the -O option

Now confused, can anybody advise?

---

### Post by CatKiller on 2020-08-15
> **xendistar2 said:**
> The bit that concerns me is the second line where it says 64bit filesystem support is not enabled?? Then it says to pass the -O 64bit and looking at the first line the command it ran it looks like is has passed the -O option

From **man mkfs.ext4** about options passed with the -O switch:

> The filesystem feature set is comprised of a list of features, separated  by commas, that are to be enabled. To disable a feature, simply prefix  the feature name with a caret ('^') character.

So the command line that was passed specifically excluded 64-bit filesystem support. Why that is, and how useful a feature it is, I really couldn't say.

---

### Post by TheFu on 2020-08-15
What version of Ubuntu and what sort of hardware?  Is this a raspberry-pi v3 or earlier?
uname -a would provide the kernel too.

---

### Post by xendistar2 on 2020-08-16
]Hi I am running on a Lenovo laptop T530, Xbuntu 20.04 (latest fresh install) kernel 5.4.0.42 and gparted version 1 which I downloaded via synaptic

Looking at Catkiller comments, I manually ran the format command without the ^ in the command

[HTML]mit@telstar:~$ sudo mkfs.ext4 -F -O 64bit -L '' '/dev/sdb1'
[sudo] password for mit: 
mke2fs 1.45.5 (07-Jan-2020)/dev/sdb1 contains a ext4 filesystem 
   last mounted on Sat Aug 15 22:56:11 2020
Creating filesystem with 244190208 4k blocks and 61054976 inodes
Filesystem UUID: 04d578e3-78a4-474a-bac5-d048e001f565
Superblock backups stored on blocks:     32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,     
4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968,     
102400000, 214990848
Allocating group tables: done                           
Writing inode tables: done                           
 Creating journal (262144 blocks): done
Writing superblocks and filesystem accounting information: done   [/HTML]

But I can not find anyway to check that it has formatted correctly, I can only assume it has.

I could not find any options in gparted where you could set the -O 64bit option, it seems that you can only do it manually

---

### Post by TheFu on 2020-08-16
The obvious, quick fix, is to just run **mkfs** manually.
The manpage says the '^' matters.
```
       -O [^]feature[,...]
              Create a filesystem with the given features (filesystem options),  overriding  the
              default  filesystem  options.  The features that are enabled by default are speci&#8208;
              fied by the base_features relation,  either  in  the  [defaults]  section  in  the
              /etc/mke2fs.conf  configuration  file,  or  in  the [fs_types] subsections for the
              usage types as specified by the -T option, further modified by the features  rela&#8208;
              tion  found in the [fs_types] subsections for the filesystem and usage types.  See
              the mke2fs.conf(5) manual page for more  details.   The  filesystem  type-specific
              configuration  setting  found  in  the [fs_types] section will override the global
              default found in [defaults].

              The filesystem feature set will be further edited using  either  the  feature  set
              specified  by this option, or if this option is not given, by the default_features
              relation for the filesystem type being created, or in the  [defaults]  section  of
              the configuration file.

              The  filesystem  feature set is comprised of a list of features, separated by com&#8208;
              mas, that are to be enabled.  To disable a feature, simply prefix the feature name
              with a caret ('^') character.  Features with dependencies will not be removed suc&#8208;
              cessfully.  The pseudo-filesystem feature "none" will clear  all  filesystem  fea&#8208;
              tures.
```
Inside the mke2fs.conf manpage, it says:
```
       auto_64-bit_support
              This relation is a boolean which specifies whether mke2fs(8) should  automatically
              add  the  64bit  feature if the number of blocks for the file system requires this
              feature to be enabled.  The resize_inode feature is  also  automatically  disabled
              since it doesn't support 64-bit block numbers.
```
Inside my mke2fs.conf file (the default):
```
        ext4 = {
                features = has_journal,extent,huge_file,flex_bg,uninit_bg,dir_nlink,extra_isize
                **auto_64-bit_support = 1**
                inode_size = 256
        }

```
So worrying about the 64-bit support isn't something I'll do.

---

### Post by xendistar2 on 2020-08-16
> **TheFu said:**
> The obvious, quick fix, is to just run **mkfs** manually.

Inside my mke2fs.conf file (the default):
```
        ext4 = {
                features = has_journal,extent,huge_file,flex_bg,uninit_bg,dir_nlink,extra_isize
                **auto_64-bit_support = 1**
                inode_size = 256
        }

```
So worrying about the 64-bit support isn't something I'll do.

Here is what my mke2fs.conf ext4 entry says
```
[COLOR=#000000]ext4 = {[/COLOR]        features = has_journal,extent,huge_file,flex_bg,metadata_csum,64bit,dir_nlink,extra_isize
        inode_size = 256
    }
```

I take that you have not tweaked your ext4 entry, why would there be a difference??

---

### Post by TheFu on 2020-08-16
> **xendistar2 said:**
> 
I take that you have not tweaked your ext4 entry, why would there be a difference??

Nope. Mine is the default for a 16.04.7 Mate desktop. On the 20.04.1 desktop, it looks like yours.  You didn't say which release was being used, so I didn't think to log into a test system. 20.04 is too new for me to use in production.

```
        ext4 = {
                features = has_journal,extent,huge_file,flex_bg,metadata_csum,64bit,dir_nlink,extra_isize
                inode_size = 256
        }

```

---

### Post by xendistar2 on 2020-08-16
Well thanks for the update, I have noted it down so that when I come to format a partition I will do it by hand using the -O 64bit.

Having formatted the drive with the -O 64bit it seems to have resolved an issue I had, which was failing to boot (have the external drive in my fstab file so it mounts for backup) with the drive connected to the laptop. Plug it in after and mount it it worked perfectly, checked it with e2fsck and it responded that it was ok no errors, it was only that comment I found in the gparted results that brought it to my attention.

Anyway thanks for the help.

---

