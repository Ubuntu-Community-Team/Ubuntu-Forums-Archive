---
title: "Error: Couldn't load plugin 'decoration'"
date: 2007-08-13
forum: Desktop Effects &amp; Customization
---

### Post by Sikarian on 2007-08-13
I tried getting Compiz working but im running into some issues.

It's finally all installed however when I compiz --replace

I get 


/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'decoration'

/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'video'

and I've got no window border.

If I try doing emerald --replace I get a message saying libdecoration.so.0 is not a proper ELF file...if I remove libdecoration.so.0 I get a message saying doesnt exist.  I've tried completely removing and reinstall compiz and emerald and still nothing.


Any ideas?

I had seen something once that said libdecoration.so.0 was not an ELF file and had invalid magic bytes at the end.


I've got no clue.

---

### Post by Happy_Man on 2007-08-13
Are you compiling from source?

---

### Post by Sikarian on 2007-08-13
Nope, I am installing through apt-get/synaptic.

---

### Post by Sikarian on 2007-08-13
Even Beryl will not load correctly.



 emerald: error while loading shared libraries: libdecoration.so.0: cannot open shared object file: No such file or directory

With the backed up version in there (I had deleted it, hoping it might remake it) I get


gtk-window-decorator: error while loading shared libraries: /usr/lib/libdecoration.so.0: invalid ELF header



Whatever the problem is, it lies with that file.  Is there a way to simply replace it?


EDIT:  I tried going into Synaptic and doing a Reinstall on libdecoration, and I get

E: /var/cache/apt/archives/libdecoration0_1%3a0.5.1+git20070730~3v1ubuntu0_i386.deb: subprocess dpkg-deb --control returned error exit status 2

---

### Post by Sikarian on 2007-08-13
So, trying to remove libdecoration gives me



The following packages will be REMOVED:
  libdecoration0
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 127kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 122831 files and directories currently installed.)
Removing libdecoration0 ...
dpkg (subprocess): unable to execute post-removal script: Exec format error
dpkg: error processing libdecoration0 (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 libdecoration0
E: Sub-process /usr/bin/dpkg returned an error code (1)

Which is not being friendly at all.  All the other compiz/beryl packages removed without complaints except this one.

---

### Post by Sikarian on 2007-08-13
Nevermind then, I solved it.  I had to go into /var/lib/dpkg/info and remove the libdecoration0.list,  .md5sums, postinst, etc and reinstall it.

---

