---
title: "Folders &amp; Locations"
date: 2008-12-28
forum: General Help
---

### Post by OinkOink2 on 2008-12-28
Hi guys,

I was just wondering, is there a tute on Ubuntu/Linux folders & locations? If not can someone tell me what folders[LIST] [*]bin [*]etc [*]var [*]usr [*]etc [/LIST] are for?

Coming from using Windows for like 8 years I need to learn the difference in file structure because this will stop me aimlessly wondering to irrelevant folder locations when searching for things etc...

What's the equivalent of Windows' program files?

Thanks.

---

### Post by OinkOink2 on 2008-12-28
Edit...

---

### Post by kaibob on 2008-12-28
Take a look at:

[https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview)

---

### Post by theozzlives on 2008-12-28
/bin contains programs and commands
/etc contains configuration data
/dev holds device names
/boot contains componants needed for the boot process
/home contains user data
/lib contains common libraries used by applications
/root home directory for the root user
/sbin commands required for system administration
/tmp temporary files
/usr contains read only material
/var holds varible data

a rough explanation

---

### Post by kidders on 2008-12-29
Hi there,

[LIST]
[*]/bin - Basic system utilities. There is never a good reason to change anything in /bin unless you're a developer.
[*]/etc - System-wide config files. You can play with this directory if you like, but don't delete or alter the permissions on any of the files.
[*]/var - Very frequently modified files go here. Don't alter anything in here (unless you're certain of the impact your changes will have), but you can freely create new files if you want.
[*]/usr - This is typically a very large directory, containing (among other things) directory structures very similar to /.
[/LIST]

> **OinkOink2 said:**
> Coming from using Windows for like 8 years I need to learn the difference in file structureBasically, files are organised according to their purpose, not the application that installed them. Almost all OSs (Windows being a notable exception) structure their filesystems this way. For example ...
[LIST]
[*]A mail server would queue messages in /var. Similarly, a database server would store its raw data files there. This allows the admin to mount a filesystem at /var that's been specifically optimised for the task, without penalising the rest of the system.
[*]Confining system settings to /etc is good for security, and makes backing up or cloning system configurations nice & easy. (User-specific config files are normally kept in /home, using file/directory names that start with a dot.)
[*]Most of the reasons for keeping the files stored in /boot together are incompatible with Ubuntu, or simply don't exist any more.
[*]Many directory names (eg /usr/share/doc) speak for themselves.
[/LIST]

> **OinkOink2 said:**
> What's the equivalent of Windows' program files?There isn't one. Mac OS superimposes a rough equivalent on top of the conventional Unix filesystem hierarchy, but Linux doesn't. In Linux, installing an application tends to scatter stuff all over the place. For example, I installed apcupsd (a UPS manager for servers) on a machine of mine today. It put its manual into /usr/share/man, documentation into /usr/share/doc, configuration files into /etc/apcupsd, startup scripts into /etc/init.d, executable binaries into /sbin (rather than /usr/sbin, which would have been more usual), and set up a directory structure in /var to help it with process management.

Many Windows users find that sort of thing patently ridiculous, but you'll get the hang of it quickly enough.

By contrast, if I had built & installed apcupsd myself for some reason (rather than just typing **sudo apt-get install apcupsd**), I would expect most of those files to have gone into /usr/local or /opt. There are very good reasons for all this, but I can imagine a Windows user finding it a bit weird.

Anyhow, I'm sure there's been an awful lot written on this subject. My best suggestion is to give [this]("http://www.google.ie/search?q=bin+etc+var+usr") a try.

---

### Post by Sef on 2008-12-29
Been merged, so unlocked.

---

### Post by OinkOink2 on 2008-12-30
Cheers guys.

And yes Kidders, it does seem weird. Not nonsensical however, it's just the process of getting to grips with it.

---

