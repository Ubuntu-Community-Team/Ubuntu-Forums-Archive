---
title: "Discussion - https://help.ubuntu.com/community/TransferVideosFromTIVOToUbuntuOrAndroi"
date: 2012-06-29
forum: Documentation and Community Wiki Discussions
---

### Post by Elfy on 2012-06-29
Please use this thread for discussion regarding

[https://help.ubuntu.com/community/TransferVideosFromTIVOToUbuntuOrAndroidUsingKmttg](https://help.ubuntu.com/community/TransferVideosFromTIVOToUbuntuOrAndroidUsingKmttg)

Support threads should be posted in normal forums.

Thank you.

---

### Post by Bill Roberts on 2015-07-26
I am not familiar with wine, so I don't know what this is supposed to do: echo 'wine "$0".exe "$@"' &gt; comskip

It fails, the result is:

[1] 5601
wine "$0".exe "$@"
gt: error: neither tool nor script specified; option -help lists possible tools
[1]+  Done                    echo 'wine "$0".exe "$@"'
comskip: command not found

Can anyone help?

---

### Post by jimav on 2016-01-05
> **Bill Roberts said:**
> ... I don't know what this is supposed to do: echo 'wine "$0".exe "$@"' &gt; comskip
It fails...


There is a transcription bug in the instructions, the "& g t ;" before the word "comskip" is supopsed to be ">" (greater-than sign), which redirects the echo output to the file "comskip".   This creates a shell script which will launch wine on the Windows executable (in detail: The shell replaces $0 with the path to the script, which is named "comskip", and so "$0".exe expands into comskip.exe which is then executed by the wine program).

---

### Post by jimav on 2016-01-05
As of January 2016 these instructions (at [https://help.ubuntu.com/community/TransferVideosFromTIVOToUbuntuOrAndroidUsingKmttg](https://help.ubuntu.com/community/TransferVideosFromTIVOToUbuntuOrAndroidUsingKmttg)) are obsolete.  The general information is still vald, but** the details no longer work** (kmttg now requires Oracle Java 1.8.0_40, projects have moved from google to sourceforge, and newer software versions are available).

A working comprehensive kmttg installer script for Ubuntu 15.10 is available at [http://abhweb.org/downloads/kmttg_aio_installer.sh](http://abhweb.org/downloads/kmttg_aio_installer.sh)

---

