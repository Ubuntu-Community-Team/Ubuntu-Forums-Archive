---
title: "7-zip and compression"
date: 2009-03-15
forum: General Help
---

### Post by FraggedLocust on 2009-03-15
I remember I once archived 4-5 DVD isos (25GB) as a solid archive to just under 4GB using WinRAR. 7-zip touts a high compression rate and I've seen evidence proving this. How can I achieve the same results using a few volumes of 700GB (~5GB) with 7-Zip? I don't really mind increasing time to compress, but from the options it looks like you need at least 1GB of memory to run the optimal compression options.

---

### Post by snova on 2009-03-15
Hmm... well, assuming you have the p7zip-full package installed, there should be documentation at

**/usr/share/doc/p7zip-full/DOCS/MANUAL/index.htm**

Whereas most of the fun options are detailed at

**/usr/share/doc/p7zip-full/DOCS/MANUAL/switches/method.htm**

Scroll down to the LZMA section. Each option here is preceeded by '-m' on the command line.

For example, I usually compress with;

```
7z a filename.7z -mx=9 *[files]*
```

You could add **-ms=on** to create solid archives.

LZMA can use as much memory as you want to throw at it. Try increasing the dictionary size (-md=128m ?).

Also, RAR is available for Ubuntu, in the **rar** package:

> 
Description: Archiver for .rar files
 This is the RAR archiver from Eugene Roshal. It supports multiple volume
 archives and damage protection. It can also create SFX-archives. There are
 versions which run on DOS, Windows (3.1x,95,NT), FreeBSD, BSDI.
 .
 This program is shareware and you must register it after 40 days of use.

It's in multiverse.

---

### Post by mb_webguy on 2009-03-15
File Roller (the Archive Manager) will let you create 7z archives, but uses the standard compression level, and doesn't give you an option to change it.  The following terminal command should give you the best compression using 7z, but it will take a bit longer than otherwise.```
7z a -t7z -m0=lzma -mx=9 -mfb=64 -md=32m -ms=on */path/to/archive* */path/to/file_or_directory*
```

---

