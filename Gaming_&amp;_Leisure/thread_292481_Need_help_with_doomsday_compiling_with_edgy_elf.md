---
title: "Need help with doomsday compiling with edgy elf"
date: 2006-11-03
forum: Gaming &amp; Leisure
---

### Post by GregLH on 2006-11-03
I decided to update to edgy elf and decided to download doomsday. I need help compiling it, So far this is what I get before I get an error on the terminal.
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

```
Tried everything and can't get it to work. :| I'm thinking that I am missing a file but not really sure. Any suggestions?

---

### Post by Yagisan on 2006-11-04
> **GregLH said:**
> I decided to update to edgy elf and decided to download doomsday. I need help compiling it, So far this is what I get before I get an error on the terminal.
```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

```
Tried everything and can't get it to work. :| I'm thinking that I am missing a file but not really sure. Any suggestions?

Please, just use the repo found in my sig. Its in the E-Yagi Consulting link.

---

### Post by GregLH on 2006-11-04
Yeah, but there is a problem with the packet manager, ```
W: GPG error: http://eyagi.bpa.nu breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0027CEFA4B6E7209
``` So I can't download the needed "libopenal0" to make doomsday engine work.

---

### Post by Yagisan on 2006-11-05
> **GregLH said:**
> Yeah, but there is a problem with the packet manager, ```
W: GPG error: http://eyagi.bpa.nu breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0027CEFA4B6E7209
``` So I can't download the needed "libopenal0" to make doomsday engine work.

just change "breezy" to "edgy" in the sources list - and follow the key instructions on the page.

---

