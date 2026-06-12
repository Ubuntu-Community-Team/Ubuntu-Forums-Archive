---
title: "Ubuntu freezes at random times"
date: 2007-06-24
forum: Dell  Ubuntu Support
---

### Post by Inturnets on 2007-06-24
I just installed Ubuntu on a Windows Vista machine with dual boot. It was all working fine, but then I noticed every once in a while the system would freeze. This occurs every 5minutes or so, and it's usually when I open a new program. At first I thought it was Firefox, so I got Opera, and Ubuntu still freezes up on me. Usually the freeze lets me move my mouse, the last freeze I just had about 3 minutes ago made my mouse disappear, but all of the ones before that still let me move my mouse around, just everything was frozen. Any help on this please?

---

### Post by HermanAB on 2007-06-24
It may be due to a bad email program checking for email.  Kmail tends to cause that. I fix it by running kmail with nice.

Otherwise, you may have either a bad processor or bad memory. Look for cpuburn and memtest86 with google.

Cheers,

Herman

---

### Post by Inturnets on 2007-06-24
I'll check out those two things you told me about. But I've also noticed that when I don't start up Beryl, Ubuntu doesn't crash. So does that mean it's a memory problem? I know I have like 2gb ram, and Windows Vista works fine, without any problems.

---

### Post by neptho on 2007-06-24
> **Inturnets said:**
> I'll check out those two things you told me about. But I've also noticed that when I don't start up Beryl, Ubuntu doesn't crash. So does that mean it's a memory problem? I know I have like 2gb ram, and Windows Vista works fine, without any problems.

Beryl is not ready for release.  It is BETA software, and can (does) cause many issues.  Don't use it.  Fall back to Metacity until it's stable.  :)

---

### Post by Inturnets on 2007-06-24
Heheh, I looked through my Synaptic Package Manager and it says Metacity is installed. Yet, I can't find it anywhere, I'm a newb to Ubuntu, or any version of Linux for that matter. Oh, and I've tried typing "metacity" in the terminal, and it gave me a bunch of info, which I really didn't understand.

Here's what the terminal says when I typed "metacity"

Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

---

### Post by logos34 on 2007-06-24
It's the default window manager for Gnome.  KDE uses KWindows.

> 
xxx@xxx-desktop:~$ metacity --version
metacity 2.16.3Copyright (C) 2001-2002 Havoc Pennington, Red Hat, Inc., and others
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

xxx@xxx-desktop:~$ apt-cache show metacity
Package: metacity
Priority: optional
Section: x11
Installed-Size: 764
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Original-Maintainer: Akira TAGOH <tagoh@debian.org>
Architecture: i386
Version: 1:2.16.3-0ubuntu2
Provides: x-window-manager
Depends: libatk1.0-0 (>= 1.12.1), libc6 (>= 2.4-1), libgconf2-4 (>= 2.13.5), libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.10.3), libice6, libmetacity0 (>= 1:2.15.21), libpango1.0-0 (>= 1.14.5), libsm6, libstartup-notification0 (>= 0.8-1), libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxinerama1, libxrandr2, libxrender1, metacity-common (= 1:2.16.3-0ubuntu2)
Suggests: gnome-control-center (>= 1:2.5.4)
Filename: pool/main/m/metacity/metacity_2.16.3-0ubuntu2_i386.deb
Size: 394594
MD5sum: b41811cd69fdd0a1ed2bebd02b169c8d
SHA1: b39d6121205e2ada4db27f80f36f74a0edf520b9
SHA256: ed22bbc48b0bb6637174fbad35e2b13f0298be1f076ef7d6d93652afe4b48635
Description: A lightweight GTK2 based Window Manager
 Metacity is a small window manager, using gtk2 to do everything.
 .
 As the author says, metacity is a "Boring window manager for the adult in
 you. Many window managers are like Marshmallow Froot Loops; Metacity is
 like Cheerios."
 .
 This package contains the core binaries.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
Task: ubuntu-desktop, edubuntu-desktop


---

### Post by Inturnets on 2007-06-24
Thanks, but what I really need is the information on how to actually change the options, etc. Like I think I have it set as my default Window manager now, but I can't find any "options" area of some sort, or even commands for options.

---

### Post by whistle on 2007-06-24
Wow. I had this problem too, and when I reboot a terminal popped up saying ```
Message from syslogd@x at Sun Jun 24 21:08:37 2007 ...
x kernel: [   91.316000] Uhhuh. NMI received for unknown reason b0 on CPU 0.

Message from syslogd@x at Sun Jun 24 21:08:37 2007 ...
x kernel: [   91.316000] **You have some hardware problem, likely on the PCI bus.**

Message from syslogd@x at Sun Jun 24 21:08:37 2007 ...
x kernel: [   91.316000] Dazed and confused, but trying to continue
```

Interesting...

Oh yeah, to answer your question... you should have a red diamond in your panel, right click that and click on select window manager.

---

### Post by logos34 on 2007-06-24
Unless you have faulty memory (memtest86), it can't be the RAM because 2GB is enough to handle just about any number of open windows and processes.  Maybe the processor is locking up--it could be that a bunch of cpu-intensive tasks are trying to run at the same time.  Whatever it is, it's more than likely related to Beryl--it takes a lot of sys resources to run that thing (which is why I don't and besides it can screw up other things as well).  The only time I get sys slowdown (lockup once) is when prelink starts up on schedule in the middle of something.

So if you haven't run memtest, do so by rebooting and choosing it from the grub menu. At the very least you'll rule it out.

After you run Beryl and have that problem, you might want to check the following files in /var/log/ for clues as to what is happening: messages, syslog, debug, user.log.  Someone with expertise will have to decipher these for you.

---

### Post by Inturnets on 2007-06-25
> **whistle said:**
> Wow. I had this problem too, and when I reboot a terminal popped up saying ```
Message from syslogd@x at Sun Jun 24 21:08:37 2007 ...
x kernel: [   91.316000] Uhhuh. NMI received for unknown reason b0 on CPU 0.

Message from syslogd@x at Sun Jun 24 21:08:37 2007 ...
x kernel: [   91.316000] **You have some hardware problem, likely on the PCI bus.**

Message from syslogd@x at Sun Jun 24 21:08:37 2007 ...
x kernel: [   91.316000] Dazed and confused, but trying to continue
```

Interesting...

Oh yeah, to answer your question... you should have a red diamond in your panel, right click that and click on select window manager.

The red diamond is for Beryl, I'm talking about for metacity.

Like I said before, when I type "metacity" in a terminal, I get

Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

So, I tried typing "metacity --replace" without the quotes, and all of the Windows on the screen flash, which means I'm guessing it worked? Now what?

---

### Post by Beatbreaker on 2007-06-28
> **Inturnets said:**
> The red diamond is for Beryl, I'm talking about for metacity.

Like I said before, when I type "metacity" in a terminal, I get

Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

So, I tried typing "metacity --replace" without the quotes, and all of the Windows on the screen flash, which means I'm guessing it worked? Now what?

interesting, i'm getting exactly problem, getting crashes all over the place - it even crashed with memtest.. I tried Metacity and got the same error:

> Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.


so what should i do next? I'll try the "metacity--replace" also and see where it takes me

---

### Post by jordon on 2007-06-29
I'm having this same issue too, and I can only assume it's because of Beryl. Whenever the computer freezes, something like this shows up in the system log.

Jun 29 13:49:22 dell kernel: [10175.844000] NVRM: Xid (0001:00): 6, PE0000 0374 00000000 000038ec 00000000 00000001
Jun 29 13:49:22 dell kernel: [10175.860000] NVRM: Xid (0001:00): 29,  L1 -> L0

I'm assuming it also has to do with the fact that my Dell laptop has nVidia graphics (hence the "NVRM"), but I'm not really sure.

---

