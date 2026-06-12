---
title: "Help... Package problems!?"
date: 2009-03-05
forum: General Help
---

### Post by smain on 2009-03-05
Hi all...

Something has gone terribly wrong so whenever I try to install something from synaptic, I get the following message (Here I installed Torus Trooper xP):

```

debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
Selecting previously deselected package torus-trooper-data.
(Reading database ... 132036 files and directories currently installed.)
Unpacking torus-trooper-data (from .../torus-trooper-data_0.22.dfsg1-3_all.deb) ...
Selecting previously deselected package torus-trooper.
Unpacking torus-trooper (from .../torus-trooper_0.22.dfsg1-3_i386.deb) ...
Processing triggers for menu ...
Processing triggers for man-db ...
Setting up linux-headers-2.6.27-13-generic (2.6.27-13.29) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.27-13-generic

 *  nvidia (177.82)...
nvidia (177.82): Already installed on this kernel.
   ...done.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.27-13-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.27-13-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.27-13-generic; however:
  Package linux-headers-2.6.27-13-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Setting up torus-trooper-data (0.22.dfsg1-3) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          Setting up torus-trooper (0.22.dfsg1-3) ...

Processing triggers for menu ...
Errors were encountered while processing:
 linux-headers-2.6.27-13-generic
 linux-headers-generic
Running prelink, please wait...

Not all changes and updates succeeded. For further details of the the failure, please expand the 'terminal' panel below.

```I think it might have to do with that I in a HDD-saving frenzy removed most of the /var/cache/ folder, Because here I had to add some folders just to get synaptic to work again... Please someone one has gone wrong?

---

### Post by ajgreeny on 2009-03-05
Is it all apt applications, eg apt-get as well as synaptic?  If you can still use apt-get try ```
sudo apt-get install --reinstall apt
``` which may make a new* /var/cache/apt/archives* for you.

---

### Post by smain on 2009-03-06
Hmm it seems that I am able to install programs... Both through apt and synaptic... BUT there is still the error message about the linux-headers... I tried using

```

sudo apt-get install --reinstall linux-headers-generic

```And got the following:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  blt python-tk tcl8.4 tcl8.5 tk8.4 tk8.5
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-headers-2.6.27-13-generic (2.6.27-13.29) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.27-13-generic          
 *  nvidia (177.82)...                                                          nvidia (177.82): Already installed on this kernel.
                                                                         [ OK ]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.27-13-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.27-13-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.27-13-generic; however:
  Package linux-headers-2.6.27-13-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 linux-headers-2.6.27-13-generic
 linux-headers-generic
Running prelink, please wait...
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Also tried to reinstall the apt... didn't work

---

### Post by ajgreeny on 2009-03-06
Have a look in the status bar of synaptic to see if there are any broken packages mentioned.  If so go to *Edit > Fix Broken Packages,* and let it do that.  This may sort out your problem.

---

### Post by smain on 2009-03-06
Nope... no broken packages...

---

### Post by smain on 2009-03-06
I'm not exactly sure how but I have now solved my problem :popcorn:

I discovered that a lot of important packages (like linux-generic, etc.) Were uninstalled! Not exactly sure how that happened, or how the system even managed to work?_?

Anyway, I reinstalled them, and also some of the dependencies which had been updated...

One reboot later my laptop now works like a charm again :D...

---

