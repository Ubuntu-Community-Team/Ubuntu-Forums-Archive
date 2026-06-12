---
title: "how do I install a sane backend"
date: 2009-03-26
forum: General Help
---

### Post by squrl on 2009-03-26
I have a canoscan 600 scanner that requires a sane backend called libsane-canon.a. I have the package. Can someone tell me what to do with it or how to install it, activate it or what???  I'm running 8.04 hardy.

Thanks

---

### Post by bwhite82 on 2009-03-26
This driver is already in the libsane package. Which can be installed via Synaptic (search for libsane) or on the command line:
> 
sudo apt-get install libsane

---

### Post by squrl on 2009-03-26
There are a multitude of different backends for sane. This particular one is named libsane-canon.a How do I install it?

---

### Post by Thelasko on 2009-03-26
It's [part of libsane]("http://packages.ubuntu.com/hardy/i386/libsane/filelist") and should be installed by default.  I'm guessing you are barking up the wrong tree in your troubleshooting.

What seems to be the problem?

---

### Post by squrl on 2009-03-26
The scanner is not found. I am told it would be with the canon.a backend. Not barking up the wrong tree. I'm lost in the wrong forest. Thanks

---

### Post by Thelasko on 2009-03-26
I occasionally have trouble getting sane to detect my old HP.  I usually have to unplug it and plug it in again.  I think it's an issue with the scanning assembly not returning to the home position properly.

---

### Post by desertdog on 2009-03-28
This scanner is supported by the canon backend. libsane-canon.a is one of the files that this backend installs, not the name of the backend.

The man page for this backend can be found at [http://www.sane-project.org/man/sane-canon.5.html](http://www.sane-project.org/man/sane-canon.5.html).

Hook up your scanner and type $sane-find-scanner in a terminal. It should show your scanner. Then try $sudo scanimage -L. Then $scanimage -L.

If $sudo scanimage -L works but $scanimage -L doesn't, then you have a permission problem and need to add your user name to the scanner group (System/Administration/Users and Groups).

This is a scsi scanner and I have only set up usb scanners.

---

