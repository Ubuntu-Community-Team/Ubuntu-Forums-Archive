---
title: "Find files and display file size"
date: 2009-02-03
forum: General Help
---

### Post by supanatral on 2009-02-03
Our company still uses office 2000, so believe it or not, if the .pst file (the database for the email) goes above 2GB, it crashes! I have all the remote computers mounted in /mnt/* so now I just want to find any file that has a file extension of *.pst and display the file size. is it possible?

I tried to use the find command and it works but it doesn't display the file size.

---

### Post by johnl on 2009-02-03
I'm sure there's a better way to do it, but this is what I would do:

```

find /mnt -type f -name "*.pst" -print0 | xargs -0 ls -sh

```

The find command finds all regular files matching .pst
The ls command prints the files along with their human readable size.

The -print0 and xargs -0 prevent the command from bugging out if there are spaces in the file names.

---

### Post by supanatral on 2009-02-03
PERFECT! thanks!

I know I'm pushing it now but is there also a way to then only find pst files that have been modified within the last 24 hours lets say?

---

### Post by johnl on 2009-02-03
Sure.  Check out the man page for 'find', it has all sorts of nifty options.  It looks like what you want is '-atime -1' which means file was last accessed less than one day ago.

---

