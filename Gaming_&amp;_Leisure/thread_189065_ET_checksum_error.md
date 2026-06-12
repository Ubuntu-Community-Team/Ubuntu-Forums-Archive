---
title: "ET checksum error"
date: 2006-06-04
forum: Gaming &amp; Leisure
---

### Post by RotoGrip on 2006-06-04
Here is the output. should i try to redownload it. I am trying the Loki installer.

Verifying archive integrity...Error in MD5 checksums: 697975de8d2ad45d2473f772ec82317c is different from 53cef31a75ca1f83746892f7cddcddf2

---

### Post by ZylGadis on 2006-06-04
Just install it using its own .run file, and it should be fine.

---

### Post by B0rsuk on 2006-06-05
The problem is that W:ET is being extracted to your /tmp directory before it's installed. Most probably your /tmp directory (partition?) is not big enough. Of course you can temporarily reconfigure your system to have /tmp elsewhere, but there are more subtle ways:

> 
b0rsuk@dziupla:/home2/instalki$ **./et-linux-2.55.x86.run --help**
Makeself version 2.1.1
 1) Getting help or info about ./et-linux-2.55.x86.run :
  ./et-linux-2.55.x86.run --help   Print this message
  ./et-linux-2.55.x86.run --info   Print embedded info : title, default target directory, embedded script ...
  ./et-linux-2.55.x86.run --lsm    Print embedded lsm entry (or no LSM)
  ./et-linux-2.55.x86.run --list   Print the list of files in the archive
  ./et-linux-2.55.x86.run --check  Checks integrity of the archive

 2) Running ./et-linux-2.55.x86.run :
  ./et-linux-2.55.x86.run [options] [--] [additional arguments to embedded script]
  with following options (in that order)
  --confirm             Ask before running embedded script
  --keep                Do not erase target directory after running
                        the embedded script
  --nox11               Do not spawn an xterm
  --nochown             Do not give the extracted files to the current user
 ** --target NewDirectory Extract in NewDirectory**
  --                    Following arguments will be passed to the embedded script


It will take care of it.

---

