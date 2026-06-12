---
title: "Beryl installed but beryl-manager not working"
date: 2007-03-29
forum: Desktop Effects &amp; Customization
---

### Post by ndefontenay on 2007-03-29
Hi all,

I've installed Beryl without any problem from the repository but I can't have it to work.
I got no errors of any sort, yet when I type beryl-manager on command line it says the command does not exists.

Here is what I got:

```
sudo apt-get install aquamarine
Reading package lists... Done
Building dependency tree
Reading state information... Done
aquamarine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Clearly it has been done fine.

Well, no...

```
bash: beryl-manager: command not found
```

So i tried to look for it to run it from the installation folder.

```
/home/nicolas/.kde/Autostart/beryl-manager
```

The line above hsa been added by me in my autostart to get it running on startup... I got nothing else.

Finally, i typed beryl in the command line and I got this:

```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
4236459 screens detected.
Currently we cannot guarantee that Beryl will work correctly with multiple X screens.
Using the --no-context-share command line option can help.
Please report any success to the beryl developer mailing list. The list can be found at lists.beryl-project.org
```

At least there's some light but if someone could enlighten me on what I should do to get it solved and have beryl running.

It would be great.

Thanks in advance Nico

---

### Post by SBFC on 2007-03-29
I'm confused, you say you installed beryl-manager yet the snippet you posted...

```
sudo apt-get install aquamarine
Reading package lists... Done
Building dependency tree
Reading state information... Done
aquamarine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

...doesn't pertain to beryl-manager. Do you actually have the beryl-manager package installed?

```
aptitude show beryl-manager
```

should resemble

```
oblivion@nippon:~$ aptitude show beryl-manager
Package: beryl-manager
[COLOR="Red"]State: installed[/COLOR]
Automatically installed: no
Version: 0.2.1-0ubuntu1
Priority: optional
Section: universe/x11
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 610k
Depends: libatk1.0-0 (>= 1.13.1), libc6 (>= 2.5-0ubuntu1), libcairo2 (>= 1.4.0),
         libfontconfig1 (>= 2.4.0), libglib2.0-0 (>= 2.12.9), libgtk2.0-0 (>=
         2.10.3), libpango1.0-0 (>= 1.16.1), libx11-6, libxcursor1 (> 1.1.2),
         libxext6, libxfixes3 (>= 1:4.0.1), libxi6, libxinerama1, libxrandr2 (>=
         2:1.2.0), libxrender1
Description: Tray application launcher tool - Beryl Project
 The Beryl Project brings 3D desktop visual effects that improve usability of
 the X Window System and provide increased productivity though plugins and
 themes contributed by the community giving a rich desktop experience. 
 
 This package contains a tray application tool to launch beryl, start different
 window decorators or window managers. The tool can also fallback to a window
 manager if beryl crashes.

```

---

### Post by ndefontenay on 2007-03-30
Hi.

Thanks for the answer

I thought it was part of the things to be installed following the command

```
sudo apt-get install aquamarine
```

What should I do to get it and what is the difference with beryl?

I'm not at home right now. I'm surfing from a coffee shop.

I'll try that when I'm back and let you know the answer.
I'm pretty sure it's not installed because the command doesn't exist.

---

