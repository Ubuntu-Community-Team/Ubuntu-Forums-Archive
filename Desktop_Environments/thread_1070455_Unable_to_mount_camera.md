---
title: "Unable to mount camera"
date: 2009-02-15
forum: Desktop Environments
---

### Post by psi36 on 2009-02-15
When I plug in my digital camera, I get this error:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=103431&stc=1&d=1234697644[/IMG]

```
$ dmesg|tail
...
[ 2113.324089] usb 2-1: new full speed USB device using uhci_hcd and address 2
[ 2113.484403] usb 2-1: configuration #1 chosen from 1 choice

```

---

### Post by khelben1979 on 2009-02-15
Look in [this]("https://www.linuxquestions.org/questions/slackware-14/gphoto2-cant-detect-canon-powershot-a95-387602/") thread.

---

### Post by psi36 on 2009-02-15
There's a lot of different stuff they suggest in the linuxquestions thread. But half of it comes down to mounting the camera, which won't work since this camera only supports PTP.

I tried gphoto2:```
~$ gphoto2 --list-files
                                                                               
*** Error ***              
PTP I/O error

*** Error ***              
An error occurred in the io-library ('Unspecified error'): No error description available
*** Error (-1: 'Unspecified error') ***       

For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug --debug-logfile=my-logfile.txt --list-files

Please make sure there is sufficient quoting around the arguments.
```

I tried gphotofs, I see the camera under computer:///, but when I click it I get the error again:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=103436&stc=1&d=1234706142[/IMG]

Always the same error: Error (-1: 'Unspecified error') which says absolutely nothing...

I've included the log i got from " env LANG=C gphoto2 --debug --debug-logfile=gphoto2-logfile.txt --list-files", just in case anyone can get any info out of that that might be helpful to resolving this...

---

