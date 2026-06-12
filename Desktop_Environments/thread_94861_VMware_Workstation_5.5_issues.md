---
title: "VMware Workstation 5.5 issues"
date: 2005-11-25
forum: Desktop Environments
---

### Post by LinuxWiz83 on 2005-11-25
Anyones know how to run VMware in cc environment or know a good how-to site on rebuilding the linux kernel? Oh i am running linux kernel 2.6.12-10 and thank you ahead of time.

CONTACT INFORMATION
If you have any questions about this EULA, or if you want to
contact VMware for any reason, please direct all correspondence
to: VMware, Inc., 3145 Porter Drive, Palo Alto, CA 94304, United
States of America or email [email]info@vmware.com[/email].

VMware is a registered trademark of VMware, Inc. in the United
States and/or various jurisdictions.

Do you accept? (yes/no) yes

Thank you.

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

Your kernel was built with "gcc" version "3.4.5", while you are trying to use
"/usr/bin/gcc" version "4.0.2". This configuration is not supported and VMware
Workstation cannot work in such configuration. Please either recompile your
kernel with "/usr/bin/gcc" version "4.0.2", or restart /usr/bin/vmware-config.pl
with CC environment variable pointing to the "gcc" version "3.4.5".

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

---

### Post by MartinG on 2005-11-25
This should help:

[http://www.ubuntuforums.org/showthread.php?t=77040](http://www.ubuntuforums.org/showthread.php?t=77040)

Don't ignore #3 in the thread! And if you don't already have them you need the headers for your kernel.

---

### Post by LinuxWiz83 on 2005-11-25
It works now and thanks for telling me about that thread.

---

