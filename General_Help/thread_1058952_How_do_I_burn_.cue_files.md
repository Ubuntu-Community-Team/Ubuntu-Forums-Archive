---
title: "How do I burn .cue files?"
date: 2009-02-03
forum: General Help
---

### Post by Trixilver on 2009-02-03
I'm trying to burn some bin/cue images to discs and everything I've tried so far has given me errors saying the cue file is invalid. Does Ubuntu support cue files or do I have to download a package to be able to burn them?

---

### Post by taurus on 2009-02-03
Maybe there is something wrong with your cue file because I use k3b to burn it and don't have any problem with it.  One thing you should remember is lower letter is not the same as upper case letter in Unix so check your cue file.  Perhaps you have the name of the file in upper case in the cue file!

---

### Post by gimcrack on 2009-02-03
CDRDAO is an open source CD-R/W burning program.

Its project page is here: [http://sourceforge.net/projects/cdrdao/](http://sourceforge.net/projects/cdrdao/)
For Win32 users, the specific file to download is here: cdrdao-1.1.5.bin.x86.win32.zip

WinZip or a similar program will be required to decompress it.

CDRDAO itself is a command line program and many people may be understandably uncomfortable with using it.  There is an excellent Win32 GUI for CDRDAO named XDuplicator.   This can be downloaded here: [http://users.forthnet.gr/ath/axatis/XDuplicator/](http://users.forthnet.gr/ath/axatis/XDuplicator/)

Addendum (4-Sep-2002, 20-Dec-2002): VCDEasy now also contains a GUI for CDRDAO and so can function as a reasonably good CUE/BIN image burner as well.  One of the common issues that seem to occur with CDRDAO functioning properly under Win32 is the absence of an adequate ASPI layer.  This can easily be addressed by download and installing ForceASPI from [http://www.doom9.org](http://www.doom9.org) (highly recommended!)  After installing the drivers with ForceASPI, REBOOT immediately.
XDuplicator should be installed in the same folder as CDRDAO.

To burn the CUE/BIN image, load XDuplicator.  Some settings may need to be changed under the "Settings" tag.

   1. Click on the Write tag
   2. Click on Open
   3. Navigate to the CUE file and open it by double-clicking
   4. Insert the recordable media into the CD recorder and click on Go!

---

