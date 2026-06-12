---
title: "Howto: USB Repository"
date: 2009-01-20
forum: General Help
---

### Post by aidave on 2009-01-20
**Create an Offline Repository**

Sometimes you have a machine without internet, and to get that internet, you need to build a driver, and to do that, need to upgrade to the latest patches or kernel.  This is a quick-n-dirty way to do that.

To build a repository onto a USB stick.  Use your main Linux computer first.

```

	sudo apt-get install debmirror

```

Get the key for the repo.

```

	gpg --no-default-keyring --keyring /home/.../trustedkeys.gpg --import /usr/share/keyrings/ubuntu-archive-keyring.gpg

```

Download the repository.  This can take many hours and will be ~7.5 GB of downloads.

```

	sudo debmirror -a i386 --no-source -s main -h cc.archive.ubuntu.com -d hardy,hardy-updates,hardy-security -r /ubuntu --progress -e http mirror

```

Copy the repository onto USB:

```

	sudo cp -R mirror /media/usb/mirror

```

Now move that stick to the offline computer.

```

	sudo mkdir /media/usbrepo
	sudo mount /media/usbrepo /dev/sdx
	sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
	sudo vim /etc/apt/sources.list

```

Replace all the contents of "/etc/apt/sources.list" with just this:

```

	deb file:///media/usbrepo/mirror hardy main
	deb file:///media/usbrepo/mirror hardy-updates main
	deb file:///media/usbrepo/mirror hardy-security main

```

You should now have an up-to-date offline repository:

```

	sudo apt-get update

```

Upgrade to the latest versions:

```

	sudo apt-get upgrade

```

---

### Post by a2z on 2009-10-13
Suppose you already have all your deb packages on the usb.
The i386 is the processor? Would this be replaced with x86-64?
Would "Hardy" be changed to Karmic?
When using sudo apt-get install debmirror I get:
E: "Couldn't find package debmirror 
Erg, I just tried substituting the above for what you have given and have come up empty. Any further help with this subject?
I have tried remidies from [another thread]("http://ubuntuforums.org/showthread.php?t=1284107") with no success either.
I can't get "Add Source" button to activate when adding a source in the Source list Software Sources.
Thanks a bunch,

a2z

---

### Post by adaallen on 2009-10-13
I'm having difficulty following these instructions...

For openers, what does --keyring /home/.../trustedkeys.gpg in 
gpg --no-default-keyring --keyring /home/.../trustedkeys.gpg --import /usr/share/keyrings/ubuntu-archive-keyring.gpg
mean. That is an invalid path AFAIK, and the command fails thusly

gpg: keyblock resource `/home/.../trustedkeys.gpg': file open error
gpg: no writable keyring found: eof
gpg: error reading `/usr/share/keyrings/ubuntu-archive-keyring.gpg': general error
gpg: import from `/usr/share/keyrings/ubuntu-archive-keyring.gpg' failed: general error
gpg: Total number processed: 0

It should be said that /usr/share/keyrings/ubuntu-archive-keyring.gpg does exist and is readable.

I'm running on 8.10 interpid ibix, and I just want to take a look at the source code for
ifconfig.c, and hoiping that this will lead me there...

---

