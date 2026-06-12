---
title: "can't burn dvds with k3b, k9, xdvdshrink or gnome baker"
date: 2006-08-02
forum: Desktop Environments
---

### Post by raul on 2006-08-02
i haven't been able to burn dvds after ripping them. i've tried using xdvdshrink and k9 to burn directly (ie, without first creating an iso file). i also tried first creating an iso to then burn it with gnomebaker, k3b or just by right-clicking on the file and selecting "write to disc...".  i've tried different speeds, as well as using different dvds (dvd+r dl and  dvdrw, of different brands). but it doesn't make a difference. i get the following errors:

- when right-clicking on the iso file:
```

There was an error writing to the disc:
Unhandled error, aborting

```

- when trying to burn the iso file through gnomebaker:
```

Executing 'builtin_dd if=/home/raul/docs/dvdrip/fitzcarraldo.iso of=/dev/sr0 obs=32k seek=0'
:-( Failed to change write speed: 2770->3324

```

- when trying to burn the iso file through k3b:
```

:-( Failed to change write speed: 2770->3324
Fatal error at startup: invalid argument
Unable to eject media.

```

- when trying to burn directly through xdvdshrink:

```
Writing new DVD                           Working!Error!

   DVDShrink has failed!
   Error:
      -> growisofs reported an error writing the new DVD!
   Command run:
      -> growisofs -speed=1 -Z /dev/dvd -dvd-video -V FITZCARRALDO /home/raul/docs/dvdrip/FITZCARRALDO/BUILD/ > /dev/null 2> /home/raul/docs/dvdrip/FITZCARRALDO/growisofsdebug.txt

   Check all your files etc. If it appears that the problem is
   ephemeral restart the script with 'dvdshrink --restart'

   End of command output
   ---------------------------------------

INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
/dev/dvd: pre-formatting blank DVD+RW...
:-( Failed to change write speed: 2770->3324
```

any help would be great. thanks!

---

### Post by soul_rebel on 2006-08-02
are you part of the cdrom group?
"groups"
is the command to know it

---

### Post by soul_rebel on 2006-08-02
double post, sorry

---

