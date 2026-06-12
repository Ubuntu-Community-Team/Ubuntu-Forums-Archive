---
title: "linux-headers-2.6.28-16-generic  installation returns error code 2"
date: 2009-12-05
forum: Desktop Environments
---

### Post by ionFreeman on 2009-12-05
My wife brought me her laptop, which claimed it had crashed, started a maintenance shell, and would really like to run fsck. I ran fsck, and just accepted the default changes it wanted to make -- there were maybe three hundred of them.

So, Ubuntu (Jaunty) restarted, but I thought this would be a good time to upgrade to Karmic. Update-manager won't run.
```
ubuntu:~$ sudo update-manager -d
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 29, in <module>
    import gtk
  File "/var/lib/python-support/python2.6/gtk-2.0/gtk/__init__.py", line 38, in <module>
    import gobject as _gobject
  File "/var/lib/python-support/python2.6/gtk-2.0/gobject/__init__.py", line 33, in <module>
    from glib import spawn_async, idle_add, timeout_add, timeout_add_seconds, \
  File "/var/lib/python-support/python2.6/gtk-2.0/glib/__init__.py", line 30, in <module>
    from glib._glib import *
ImportError: No module named _glib

```

I reinstalled update-manager, update-manager-core, glib and some other packages with synaptic, but this did not help.

So, I ran apt-get
```
ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up linux-image-2.6.28-16-generic (2.6.28-16.57) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-16-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.28-16.55 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.28-16.55 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-14-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 3, in <module>
    from NvidiaDetector.nvidiadetector import NvidiaDetection, NoDatadirError
  File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 25, in <module>
    import sys, logging
ImportError: No module named logging
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28-16-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.28-16-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up linux-headers-2.6.28-16-generic (2.6.28-16.57) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 3, in <module>
    from NvidiaDetector.nvidiadetector import NvidiaDetection, NoDatadirError
  File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 25, in <module>
    import sys, logging
ImportError: No module named logging
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.28-16-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.28-16-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.28-16-generic
 linux-headers-2.6.28-16-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ionFreeman on 2009-12-06
I get the below when I run apt-get dist-upgrade. Is locating the python logging module going to solve all of my problems, or would one suspect there's a deeper issue at play here?

```
ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up linux-image-2.6.28-16-generic (2.6.28-16.57) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-16-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.28-16.55 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.28-16.55 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-17-generic
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-14-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 3, in <module>
    from NvidiaDetector.nvidiadetector import NvidiaDetection, NoDatadirError
  File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 25, in <module>
    import sys, logging
ImportError: No module named logging
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28-16-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.28-16-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up linux-image-2.6.28-17-generic (2.6.28-17.58) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-17-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-17-generic
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-14-generic
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 3, in <module>
    from NvidiaDetector.nvidiadetector import NvidiaDetection, NoDatadirError
  File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 25, in <module>
    import sys, logging
ImportError: No module named logging
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28-17-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.28-17-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-17-generic:
 linux-restricted-modules-2.6.28-17-generic depends on linux-image-2.6.28-17-generic; however:
  Package linux-image-2.6.28-17-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-17-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.28-17-generic; however:
  Package linux-image-2.6.28-17-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpNo apport report written because the error message indicates its a followup error from a previous failure.
                            No apport report written because MaxReports is reached already
          No apport report written because MaxReports is reached already
                                                                        No apport report written because MaxReports is reached already
                                                      E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

