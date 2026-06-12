---
title: "ia32-libs and aurora engine"
date: 2011-02-24
forum: Desktop Environments
---

### Post by notesetter on 2011-02-24
I'm posting this here partly to make folks aware of a problem I've identified and partly because I don't know how to file a bug report (actually, I could figure out the bug report bit, but I don't want to file the wrong bug report, if that makes sense).

I've spotted a problem - and a solution - relating to the ia32-libs and 32-bit applications running on a 64-bit version of Ubuntu. It's somewhat related to this [bug]("https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/190227"), which has already been solved.

So, I installed the artwork and themes from [Ubuntu Satanic Edition]("http://ubuntusatanic.org/installation.php"). The problem is that certain non-64-bit applications which make use of the ia32-libs don't display correctly (the buttons and other theme elements are all fouled up). This is due to the fact that the Satanic themes are based on the Aurora engine.

Specifically, applications complain thusly: ```
(transcribe:8148): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/engines/libaurora.so: wrong ELF class: ELFCLASS64
```

So I investigated and found that there was no 32-bit version of ```
libaurora.so
``` where 32-bit gtk-2 applications running on a 64-bit Linux would expect to find it, which is /usr/lib32/gtk-2.0/2.10.0/engines

So I transferred a copy of one from a 32-bit installation on a different machine and everything behaves as expected.

So the question is this: Where does the bug report belong? Is this an ia32-libs bug or an Aurora engine bug? Who would be responsible for ensuring that a 32-bit version of libaurora.so is included on 64-bit systems which have both the Aurora engine and ia32-libs installed?

Feel free to direct me. I'll file the bug report.

Thanks.

---

### Post by parker13 on 2011-02-25
How did you install the Ubuntu SE themes? From the SE repositories? If so, the aurora engine package should have been installed also.


Garry.

---

### Post by notesetter on 2011-02-25
Hi Garry,

I followed the instruction on the [installation page]("http://ubuntusatanic.org/installation.php") and clicked the 4:3 link that prompted apturl to fetch and install the package named ubuntu-satanic.

I've done this on two machines: one running 32-bit Linux Mint 9 (based on Ubuntu 10.04) and one running 64-bit Ubuntu 10.04. Apparently, the ubuntu-satanic package doesn't install a 32-bit version of libaurora.so, which is required by 32-bit applications making use of ia32-libs to work in a 64-bit environment and using the aurora theme engine.

Does that make sense? I'm not a technical person, but I think that's what the deal is.

David

---

### Post by parker13 on 2011-02-28
I've just retested this and the gtk2-engines-aurora package is installed as part of the ubuntu-satanic package:

```

sudo apt-get install ubuntu-satanic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gtk2-engines-aurora satanic-gnome-themes satanic-wallpapers
The following NEW packages will be installed
  gtk2-engines-aurora satanic-gnome-themes satanic-wallpapers ubuntu-satanic
0 upgraded, 4 newly installed, 0 to remove and 46 not upgraded.
Need to get 17.7MB/17.8MB of archives.
After this operation, 18.4MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

...and the .so file is part of the gtk2-engines-aurora package:
```

dpkg -L gtk2-engines-aurora | grep libaurora.so
/gtk-2.0/2.10.0/engines/libaurora.so

```

That's on 32-bit Maverick. So I'm a bit baffled as to what happened. All I can suggest is try installing the ubuntu-satanic meta package again and see if it also installs the gtk2-engines-aurora package. Maybe do it from the command line (as above) and send me the output if you still have problems.

Sorry about this!

---

