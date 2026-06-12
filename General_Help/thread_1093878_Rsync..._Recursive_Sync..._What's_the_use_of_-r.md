---
title: "Rsync... Recursive Sync... What's the use of -r??"
date: 2009-03-12
forum: General Help
---

### Post by Roasted on 2009-03-12
I was just reading the man pages of rsync and I noticed that there's a switch for -r which is for recursive.

Isn't rsync = recursive synchronization anyway? I mean isn't the functions of -r already included in the ACTUAL rsync command itself?

I just didn't understand this and wanted to ask. I've been using rsync for a few years and it definitely takes everything in the folders... so I know it's recursive...

---

### Post by lloyd_b on 2009-03-12
> **Roasted said:**
> I was just reading the man pages of rsync and I noticed that there's a switch for -r which is for recursive.

Isn't rsync = recursive synchronization anyway? I mean isn't the functions of -r already included in the ACTUAL rsync command itself?

I just didn't understand this and wanted to ask. I've been using rsync for a few years and it definitely takes everything in the folders... so I know it's recursive...

I was under the impression that rsync stood for Remote SYNChronization.

I have no clue why there's a "-r" option if it's inherently recursive, though.  I've never used rsync myself.

Lloyd B.

---

### Post by amac777 on 2009-03-12
I think the r in rysnc stands for "remote".

Anyway, it doesn't recursively copy files from subfolders unless you tell it to. One way is by using the -r parameter, for example. Another way is the -a parameter, which is a short hand for -rlptgoD. There might be other ways too that I'm not aware of.

---

### Post by Roasted on 2009-03-12
You guys were right - it looks like it's remote.

And I guess that answers my question, cause I have the -a switch in my script.

Hmmm... how different would -r be from -a??

---

### Post by Yellow Pasque on 2009-03-12
-a implies -r
> -a archive mode; equals -rlptgoD

---

### Post by issih on 2009-03-12
Copied from the rsync man page:
```

  -v, --verbose               increase verbosity
        -q, --quiet                 suppress non-error messages
            --no-motd               suppress daemon-mode MOTD (see caveat)
        -c, --checksum              skip based on checksum, not mod-time & size
        -a, --archive               archive mode; same as -rlptgoD (no -H)
            --no-OPTION             turn off an implied OPTION (e.g. --no-D)
        -r, --recursive             recurse into directories
        -R, --relative              use relative path names
            --no-implied-dirs       don't send implied dirs with --relative
        -b, --backup                make backups (see --suffix & --backup-dir)
            --backup-dir=DIR        make backups into hierarchy based in DIR
            --suffix=SUFFIX         backup suffix (default ~ w/o --backup-dir)
        -u, --update                skip files that are newer on the receiver
            --inplace               update destination files in-place
            --append                append data onto shorter files
        -d, --dirs                  transfer directories without recursing
        -l, --links                 copy symlinks as symlinks
        -L, --copy-links            transform symlink into referent file/dir
            --copy-unsafe-links     only "unsafe" symlinks are transformed
            --safe-links            ignore symlinks that point outside the tree
        -k, --copy-dirlinks         transform symlink to dir into referent dir
        -K, --keep-dirlinks         treat symlinked dir on receiver as dir
        -H, --hard-links            preserve hard links
        -p, --perms                 preserve permissions
            --executability         preserve executability
            --chmod=CHMOD           affect file and/or directory permissions
        -o, --owner                 preserve owner (super-user only)
        -g, --group                 preserve group
            --devices               preserve device files (super-user only)
            --specials              preserve special files
        -D                          same as --devices --specials
        -t, --times                 preserve times
        -O, --omit-dir-times        omit directories when preserving times
            --super                 receiver attempts super-user activities
        -S, --sparse                handle sparse files efficiently
        -n, --dry-run               show what would have been transferred
        -W, --whole-file            copy files whole (without rsync algorithm)
        -x, --one-file-system       don't cross filesystem boundaries
        -B, --block-size=SIZE       force a fixed checksum block-size
        -e, --rsh=COMMAND           specify the remote shell to use

```

So -a is a shortcut for archive mode which is exactly the same as using -rlptgoD which is recursive, copy symlinks, copy permissions, copy times, copy groups, copy owner, etc.

-a does recursive, but it also does a whole lot more.

Have a look at ```
man rsync
```, theres a lot in there.

---

### Post by Roasted on 2009-03-12
Ahh, I didn't realize when you guys were saying -rlptgoD that it was taking in ALL of those individually. I assumed it was all 1 switch, as weird as that looks.

Anyway, thanks a lot. I'm glad whoever helped me on here with rsync 3 years ago talked me into using the -a switch. I started using it and never questioned why all this time. 

:popcorn:

---

