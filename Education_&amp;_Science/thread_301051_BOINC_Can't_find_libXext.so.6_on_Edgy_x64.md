---
title: "BOINC Can't find libXext.so.6 on Edgy x64"
date: 2006-11-16
forum: Education &amp; Science
---

### Post by jsteve54302 on 2006-11-16
I've been ](*,) with BOINC on Edgy X64.  The projects refuse to run on x64 platforms <rant> and the are scientists????!! </rant>, and the x86 BIONC manager i downloaded from BOINC on the advice of another thread can't find the libXext.so.6 file.
<output>
john@john-desktop:~/dnload/boinc/BOINC$ ./boincmgr
./boincmgr: error while loading shared libraries: libXext.so.6: cannot open shared object file: No such file or directory
john@john-desktop:~/dnload/boinc/BOINC$ 
</output>

I've checked /lib, and the file is there...  I've even tried copying it to the bouncmgr folder; bouncmgr still refuses to see it, and wont even give me an idea of where it expects it.
  Is there any way to get this working?

TIA,

---

### Post by jsteve54302 on 2006-11-19
Never mind...  To paraphrase a recent poster, I've killed a Gnome over a CUPS remote print server matter, so thoroughly that it was much faster just to reinstall with the x86-generic dist than try to resurrect it, so the x64 issue is gone and I've got BOINC up and running now.  However, a complete, step-by-step HOW-TO on BOINC-x32 running under Ubuntu-x64 (no, these are **not** real packages!) might be in order anyway, if such a beast can exist.  I haven't found one that worked for me yet.  IMHO, the x32 dists seem more robust, and more broadly supported by software, than the x64's anyway...  Oh well...

---

### Post by sheenaramone on 2007-01-12
I got the 32 bit BOINC to run from the home folder with Edgy64 by doing this in a terminal.

"sudo apt-get install ia32-libs"

it downloaded and installed some stuff and I did a reboot and BOINC works!  I ran across that in a Team Phoenix Rising forum ([http://forums.teamphoenixrising.net/showthread.php?p=361923](http://forums.teamphoenixrising.net/showthread.php?p=361923) )and I wondered if that would solve my problem and it did!

I was getting messages about "file or command not found" when I would try to start BOINC.

---

