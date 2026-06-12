---
title: "Where in the filesystem are programs stored?"
date: 2009-02-12
forum: General Help
---

### Post by cmwslw on 2009-02-12
I need to install Eclipse Gandymede right now, which is not included in the synaptic manager. I have to use a .tar.gz file, and I can install it fine, but I was wondering *where* a program like that is supposed to go. I realize you can put it anywhere, but I'd like all my programs to share a similar location. Right now I've been using /usr/lib/, but I'm pretty sure that's not the right place.

Thanks in advance,
Cory Walker

---

### Post by jrusso2 on 2009-02-12
Depends on the program some are in /usr/bin, some would be in usr/share and others might be in /opt what re read your post I would put eclipse in /opt since its optional software.

---

### Post by cmwslw on 2009-02-12
Thank you. That clears up some confusion.

---

### Post by pirate_tux on 2009-02-12
If the program is intended to be used also by other computers on a local network, install it to /opt.

If the program is intended to be used only by your computer, install it to /usr/local.

If you had take the time to read something about the linux filesystem structure, you wouldn't have this kind of doubts...

---

### Post by jrusso2 on 2009-02-12
> **pirate_tux said:**
> If the program is intended to be used also by other computers on a local network, install it to /opt.

If the program is intended to be used only by your computer, install it to /usr/local.

If you had take the time to read something about the linux filesystem structure, you wouldn't have this kind of doubts...

I don't know where you got that idea from but its never been right.

/opt is for optional

[http://www.pathname.com/fhs/pub/fhs-2.3.html#OPTADDONAPPLICATIONSOFTWAREPACKAGES](http://www.pathname.com/fhs/pub/fhs-2.3.html#OPTADDONAPPLICATIONSOFTWAREPACKAGES)


/opt is reserved for the installation of add-on application software packages.

A package to be installed in /opt must locate its static files in a separate /opt/<package> or /opt/<provider> directory tree, where <package> is a name that describes the software package and <provider> is the provider's LANANA registered name.

Every thing I post gets argued by all these twenty year old male geeks.  I am about to give up on helping on the forum and let them take over.

---

### Post by Slim Odds on 2009-02-12
> **jrusso2 said:**
> Every thing I post gets argued by all these twenty year old male geeks.  I am about to give up on helping on the forum and let them take over.

Very bad idea indeed... :)

---

### Post by pirate_tux on 2009-02-12
> **jrusso2 said:**
> I don't know where you got that idea from but its never been right.

/opt is for optional

[http://www.pathname.com/fhs/pub/fhs-2.3.html#OPTADDONAPPLICATIONSOFTWAREPACKAGES](http://www.pathname.com/fhs/pub/fhs-2.3.html#OPTADDONAPPLICATIONSOFTWAREPACKAGES)


/opt is reserved for the installation of add-on application software packages.

A package to be installed in /opt must locate its static files in a separate /opt/<package> or /opt/<provider> directory tree, where <package> is a name that describes the software package and <provider> is the provider's LANANA registered name.

Every thing I post gets argued by all these twenty year old male geeks.  I am about to give up on helping on the forum and let them take over.

You are wrong.
Read de documentation about the Linux File System Structure.

---

### Post by jrusso2 on 2009-02-12
Speak of the devil.  Well I am out of here good luck with the forum and helping everyone pirate tux.

I am going to spend time with people that appreciate the help.

Not going to sit here and argue constantly with a bunch of twenty year old males about nonsense esp stuff that has been long established like /opt.

See you all.

---

### Post by dcstar on 2009-02-12
> **pirate_tux said:**
> You are wrong......


Dontcha just lurve these religious debates?      :rolleyes:

The great thing about "standards" (and especially "recommendations") is that people interpret them in different ways and choose one over another.

I find that /opt isn't used that much these days for user installs - especially with Ubuntu packages - but it isn't a big deal if it is (as long as the stuff is in /opt or the /usr tree).

That's the point - it **isn't** a big deal.

What I get very crabby about is users putting data in the /usr tree - or another system folder because the name is convenient - now that **is** a big deal.

---

### Post by pirate_tux on 2009-02-13
> **jrusso2 said:**
> Speak of the devil.  Well I am out of here good luck with the forum and helping everyone pirate tux.

I am going to spend time with people that appreciate the help.

Not going to sit here and argue constantly with a bunch of twenty year old males about nonsense esp stuff that has been long established like /opt.

See you all.

You should learn the Linux Directory Structure.

Among other articles, I think you should read this:

[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

«< /usr/local >

This is where you install apps and other files for use on the local machine. If your machine is a part of a network, the /usr directory may physically be on another machine and can be shared by many networked Linux workstations. On this kind of a network, the /usr/local directory contains only stuff that is not supposed to be used on many machines and is intended for use at the local machine only.

Most likely your machine isn't a part of a network like this, but it doesn't mean that /usr/local is useless. If you find interesting apps that aren't officially a part of your distro, you should install them in /usr/local. For example, if the app would normally go to /usr/bin but it isn't a part of your distro, you should install it in /usr/local/bin instead. When you keep your own programs away from the programs that are included in your distro, you'll avoid confusion and keep things nice and clean.»»

Now read my lips: «the /usr/local directory contains only stuff that is not supposed to be used on many machines and is intended for use at the local machine only.»

If you experience problems understanding this, please feel free to ask for help.

/opt, on the contrary, is for programs intended to be used by other computers on the local network.

---

### Post by lykwydchykyn on 2009-02-13
> **pirate_tux said:**
> You are wrong.
Read de documentation about the Linux File System Structure.

uh, dude, do you realize what she posted was copied directly from the official documentation?

Maybe you need to do some reading:

[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

---

### Post by mb_webguy on 2009-02-13
Maybe that's just too much for him to absorb all at once.  Here's the summarized version from Wikipedia:```

**_Directory_		_Description_**
/			Primary hierarchy root and root directory of the entire file system hierarchy.

/bin/			Essential command binaries that need to be available in single user mode; for all users, e.g., cat, ls, cp.

/boot/			Boot loader files, e.g., kernels, initrd; often a separate partition.

/dev/			Essential devices, e.g., /dev/null.

/etc/			Host-specific system-wide configuration files (the name comes from et cetera).

   /etc/opt/		Configuration files for /opt/.

   /etc/X11/		Configuration files for the X Window System, version 11.

   /etc/sgml/		Configuration files for SGML.

   /etc/xml/		Configuration files for XML.

/home/			Users' home directories, containing saved files, personal settings, etc.; often a separate partition.

/lib/			Libraries essential for the binaries in /bin/ and /sbin/.

/media/			Mount points for removable media such as CD-ROMs (appeared in FHS-2.3).

/mnt/			Temporarily mounted filesystems.

**/opt/			Optional application software packages.**

/proc/			Virtual filesystem documenting kernel and process status as text files, e.g., uptime, network.

/root/			Home directory for the root user.

/sbin/			Essential system binaries, e.g., init, route, ifup.

/srv/			Site-specific data which is served by the system.

/tmp/			Temporary files (see also /var/tmp). Often not preserved between system reboots.

**/usr/			Secondary hierarchy for user data; contains the majority of (multi-)user utilities and applications.**

   /usr/bin/		Non-essential command binaries (not needed in single user mode); for all users.

   /usr/include/	Standard include files.

   /usr/lib/		Libraries for the binaries in /usr/bin/ and /usr/sbin/.

   /usr/sbin/		Non-essential system binaries, e.g., daemons for various network-services.

   /usr/share/		Architecture-independent (shared) data.

   /usr/src/		Source code, e.g., the kernel source code with its header files.

   /usr/X11R6/		X Window System, Version 11, Release 6.

   **/usr/local/		Tertiary hierarchy for local data, specific to this host. Typically has further subdirectories, e.g., bin/, lib/, share/.**

/var/			Variable files, such as logs, spool files, and temporary e-mail files.

   /var/lib/		State information. Persistent data modified by programs as they run, e.g., databases, packaging system metadata, etc.

   /var/lock/		Lock files. Files keeping track of resources currently in use.

   /var/log/		Log files. Various logs.

   /var/mail/		Users' mailboxes.

   /var/run/		Information about the running system since last boot, e.g., currently logged-in users and running daemons.

   /var/spool/		Spool for tasks waiting to be processed, e.g., print queues and unread mail.

   /var/spool/mail/	Deprecated location for users' mailboxes.

   /var/tmp/	Temporary files to be preserved between reboots.
```

---

