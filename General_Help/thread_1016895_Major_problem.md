---
title: "Major problem"
date: 2008-12-20
forum: General Help
---

### Post by Marine1 on 2008-12-20
I'm relatively new to Linux, and I am having major problems.

Whenever I try to update anything, I get a series of messages that tells me that I have unmet dependencies on the machine.  I used to have 10 broken packages, now I have one.  However, I still can't get it to work right.

Recently, the Add/Remove programs program stopped working as well.


I've included some screenshots of what's going on when I try to fix it... 

Please help!

Thank you in advance.

---

### Post by Marine1 on 2008-12-20
Here's some more of the screenshots.

Again, thanks for the help.

---

### Post by heyho on 2008-12-20
Have you tried sudo apt-get update, followed by sudo apt-get upgrade?

---

### Post by Carl Hamlin on 2008-12-20
-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

As a troubleshooting step, try this:

1. Execute a terminal emulation instance.
2. In the terminal, type "sudo apt-get clean" without the quotation marks. This will remove all the downloaded archival packages for the software you've installed via the repository, while keeping the installations intact. You'll need to give your password.
3. In the terminal, type "sudo apt-get update" without the quotation marks. This will simultaneously fully update every repository listing you've made available on your machine. You'll need to give your password.
4. In the terminal, type "sudo apt-get upgrade" without the quotation marks. This will simultaneously upgrade *all* the installed repository-sourced software on your machine to the latest versions available in the repository. You'll need to give your password and answer a few intuitive questions.

When you're done with all this, see if the problem you've been having updating software via add/remove programs still exists and we'll go from there.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklNPxYACgkQyLm4ydrABvfoMQCgzRvkXLgt5q9fP92zI8DWNYdA
hHMAoIo2ULehxIRjqMjpaC05M7I8Gh5G
=siiq
-----END PGP SIGNATURE-----

---

### Post by cariboo on 2008-12-20
THe first thing you should do is free up some disk space. To do this, in a terminal type:

```
sudo apt-get autoclean
```

this should remove all the archived packages stored in /var/cache/apt/archives. Just to be sure also in the same terminal type:

```
sudo apt-get clean
```

The next thing to do is to fix the broken packages, go to System-->Administration-->Synaptic Package Manager-->Edit-->Fix Broken Packages. Usually all you have to do is to completely remove the broken package and you should be OK. After fixing the broken package, clcick the reload button and refresh the repositories. You should now be able to install the updates.

Edit: You beat me to it.

Jim

---

### Post by Marine1 on 2008-12-20
> **heyho said:**
> Have you tried sudo apt-get update, followed by sudo apt-get upgrade?

Yep.  I did.  Here's what I got... this is at the end of trying to receive the upgrade... 

Confusing...

---

### Post by Marine1 on 2008-12-20
Any more suggestions?

---

### Post by Carl Hamlin on 2008-12-20
> **Marine1 said:**
> Any more suggestions?

-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

What happened when you tried to fix broken packages using the package manager?

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklNgGoACgkQyLm4ydrABvd1kgCfVPBLjOb7toZBDrQ7oETv4X2Y
4JAAoMZVJs7jZ0h541VnmzuYMRuJCdBV
=06lZ
-----END PGP SIGNATURE-----

---

### Post by Marine1 on 2008-12-20
> **Carl Hamlin said:**
> 
What happened when you tried to fix broken packages using the package manager?



I got an error.

Here's what I've been getting.

> 
E: linux-ubuntu-modules-2.6.24-16-generic: subprocess post-removal script returned error exit status 1
E: linux-ubuntu-modules-2.6.24-16-server: subprocess post-removal script returned error exit status 1
E: linux-ubuntu-modules-2.6.24-16-virtual: subprocess post-removal script returned error exit status 1


---

### Post by Carl Hamlin on 2008-12-20
-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

Eep.

Is this the first installation of Ubuntu on this hardware?

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklNjXcACgkQyLm4ydrABveEOgCfRYdI5lnkpo02B4qrtYHEraYg
fqYAn147mbfFjm1vj+rfxuWRjgs1ettM
=znEC
-----END PGP SIGNATURE-----

---

### Post by Marine1 on 2008-12-20
> **Carl Hamlin said:**
> -----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

Eep.

Is this the first installation of Ubuntu on this hardware?

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklNjXcACgkQyLm4ydrABveEOgCfRYdI5lnkpo02B4qrtYHEraYg
fqYAn147mbfFjm1vj+rfxuWRjgs1ettM
=znEC
-----END PGP SIGNATURE-----


Yep.  I have it located on an external hard drive hooked up to a Dell XPS 420 (huh huh... he said 420) with Vista Ultimate on it... but the other internal hard drive isn't active while Ubuntu is running as the OS.

---

### Post by albinootje on 2008-12-20
> **Marine1 said:**
> I got an error.

Here's what I've been getting.

And which kernel are you using ?
```

uname -a
ls /boot

```

---

### Post by Marine1 on 2008-12-20
```
aaron@aaron-desktop:~$ uname -a
Linux aaron-desktop 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux
aaron@aaron-desktop:~$ ls /boot
abi-2.6.24-16-386                 initrd.img-2.6.24-21-generic.bak
abi-2.6.24-19-generic             lost+found
abi-2.6.24-21-generic             memtest86+.bin
config-2.6.24-16-386              System.map-2.6.24-16-386
config-2.6.24-19-generic          System.map-2.6.24-19-generic
config-2.6.24-21-generic          System.map-2.6.24-21-generic
grub                              vmlinuz-2.6.24-16-386
initrd.img-2.6.24-19-generic      vmlinuz-2.6.24-19-generic
initrd.img-2.6.24-19-generic.bak  vmlinuz-2.6.24-21-generic
initrd.img-2.6.24-21-generic
aaron@aaron-desktop:~$


```

That's what I got in response.

---

### Post by albinootje on 2008-12-20
> **Marine1 said:**
> ```
aaron@aaron-desktop:~$ uname -a
Linux aaron-desktop 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686 GNU/Linux
aaron@aaron-desktop:~$ ls /boot
abi-2.6.24-16-386                 initrd.img-2.6.24-21-generic.bak
abi-2.6.24-19-generic             lost+found
abi-2.6.24-21-generic             memtest86+.bin
config-2.6.24-16-386              System.map-2.6.24-16-386
config-2.6.24-19-generic          System.map-2.6.24-19-generic
config-2.6.24-21-generic          System.map-2.6.24-21-generic
grub                              vmlinuz-2.6.24-16-386
initrd.img-2.6.24-19-generic      vmlinuz-2.6.24-19-generic
initrd.img-2.6.24-19-generic.bak  vmlinuz-2.6.24-21-generic
initrd.img-2.6.24-21-generic
aaron@aaron-desktop:~$


```

That's what I got in response.

Thanks. In the meantime I noticed that your screenshots show that you don't have enough diskspace in /boot
Can you please try the following in a terminal:
```

sudo apt-get remove --purge linux-image-2.6.24-16-generic linux-image-2.6.24-19-generic ; sudo apt-get -f install

```
And post possible errors.

---

### Post by Marine1 on 2008-12-20
Here's what happened when I put that through the console.

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail                                                                                                able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc                                                                                                ess using it?
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail                                                                                                able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc                                                                                                ess using it?

```

There is something whack going on here.

I'm gonna restart the computer soon... shut down SATA 0 (the Windows hard drive) and see if that helps... but that's the only thing I can think of.

Would that even help?

---

### Post by albinootje on 2008-12-20
> **Marine1 said:**
> 

There is something whack going on here.

I'm gonna restart the computer soon... shut down SATA 0 (the Windows hard drive) and see if that helps... but that's the only thing I can think of.

Would that even help?

Rebooting would help in this case, but so will logging out of your Ubuntu desktop, since now Synaptic or some other dpkg or apt-get related program is "blocking" this.
But the Windows disk doesn't have anything to do with this.

---

### Post by Marine1 on 2008-12-20
> **albinootje said:**
> Rebooting would help in this case, but so will logging out of your Ubuntu desktop, since now Synaptic or some other dpkg or apt-get related program is "blocking" this.
But the Windows disk doesn't have anything to do with this.

Hm... how am I supposed to fix it if I'm not on my desktop though?  That's probably a noob question.

---

### Post by albinootje on 2008-12-20
> **Marine1 said:**
> Hm... how am I supposed to fix it if I'm not on my desktop though?  That's probably a noob question.

After a reboot, boot into Ubuntu, and please try those (last suggested) commands again.

---

### Post by Marine1 on 2008-12-20
Did that, used the Linux Console option on Konsole, and here's what I got.
> linux-image-2.6.24-19-generic ; sudo apt-get -f install
[sudo] password for aaron:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package linux-image-2.6.24-16-generic is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-image-2.6.24-19-generic* linux-restricted-modules-2.6.24-19-generic*
  linux-ubuntu-modules-2.6.24-16-generic linux-ubuntu-modules-2.6.24-16-server
  linux-ubuntu-modules-2.6.24-16-virtual
  linux-ubuntu-modules-2.6.24-19-generic*
0 upgraded, 0 newly installed, 6 to remove and 74 not upgraded.
7 not fully installed or removed.
After this operation, 163MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 136066 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-16-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-16-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Cannot find /lib/modules/2.6.24-16-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-16-generic (--remove):
 subprocess post-removal script returned error exit status 1
Removing linux-ubuntu-modules-2.6.24-16-server ...
FATAL: Could not open '/boot/System.map-2.6.24-16-server': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-16-server
Cannot find /lib/modules/2.6.24-16-server
update-initramfs: failed for /boot/initrd.img-2.6.24-16-server
dpkg: error processing linux-ubuntu-modules-2.6.24-16-server (--remove):
 subprocess post-removal script returned error exit status 1
Removing linux-ubuntu-modules-2.6.24-16-virtual ...
FATAL: Could not open '/boot/System.map-2.6.24-16-virtual': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-16-virtual
Cannot find /lib/modules/2.6.24-16-virtual
update-initramfs: failed for /boot/initrd.img-2.6.24-16-virtual
dpkg: error processing linux-ubuntu-modules-2.6.24-16-virtual (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-16-generic
 linux-ubuntu-modules-2.6.24-16-server
 linux-ubuntu-modules-2.6.24-16-virtual
E: Sub-process /usr/bin/dpkg returned an error code (1)
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.24-16-generic linux-ubuntu-modules-2.6.24-16-server
  linux-ubuntu-modules-2.6.24-16-virtual
0 upgraded, 0 newly installed, 3 to remove and 74 not upgraded.
7 not fully installed or removed.
After this operation, 36.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 136066 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.24-16-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-16-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Cannot find /lib/modules/2.6.24-16-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-16-generic (--remove):
 subprocess post-removal script returned error exit status 1
Removing linux-ubuntu-modules-2.6.24-16-server ...
FATAL: Could not open '/boot/System.map-2.6.24-16-server': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-16-server
Cannot find /lib/modules/2.6.24-16-server
update-initramfs: failed for /boot/initrd.img-2.6.24-16-server
dpkg: error processing linux-ubuntu-modules-2.6.24-16-server (--remove):
 subprocess post-removal script returned error exit status 1
Removing linux-ubuntu-modules-2.6.24-16-virtual ...
FATAL: Could not open '/boot/System.map-2.6.24-16-virtual': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-16-virtual
Cannot find /lib/modules/2.6.24-16-virtual
update-initramfs: failed for /boot/initrd.img-2.6.24-16-virtual
dpkg: error processing linux-ubuntu-modules-2.6.24-16-virtual (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-16-generic
 linux-ubuntu-modules-2.6.24-16-server
 linux-ubuntu-modules-2.6.24-16-virtual
E: Sub-process /usr/bin/dpkg returned an error code (1)
aaron@aaron-desktop:~$


---

### Post by albinootje on 2008-12-20
Okay, can you do this :

```

sudo dpkg -P --force-all linux-image-2.6.24-19-generic linux-restricted-modules-2.6.24-19-generic linux-ubuntu-modules-2.6.24-16-generic linux-ubuntu-modules-2.6.24-16-server linux-ubuntu-modules-2.6.24-16-virtual
linux-ubuntu-modules-2.6.24-19-generic

```

---

### Post by albinootje on 2008-12-20
And if that won't help, please try this :

```

cd /boot
sudo > initrd.img-2.6.24-19-generic
sudo > initrd.img-2.6.24-19-generic.bak
sudo > vmlinuz-2.6.24-16-386
sudo > vmlinuz-2.6.24-19-generic

```

And after that try sudo apt-get -f install again.

The idea is to make space in /boot, but still leave the filenames there in order to let dpkg or apt-get complain less.
Your current kernel files, 2.6.24-21, should not be touched.

---

### Post by Marine1 on 2008-12-20
Output for that:

> 
nux-restricted-modules-2.6.24-19-generic linux-ubuntu-modules-2.6.24-16-generic linux-ubuntu-modules-2.6.24-16-server linux-ubuntu-modules-2.6.24-16-virtual
[sudo] password for aaron:
(Reading database ... 136066 files and directories currently installed.)
Removing linux-restricted-modules-2.6.24-19-generic ...
Purging configuration files for linux-restricted-modules-2.6.24-19-generic ...
Removing linux-ubuntu-modules-2.6.24-16-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-16-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Cannot find /lib/modules/2.6.24-16-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-16-generic (--purge):
 subprocess post-removal script returned error exit status 1
Removing linux-ubuntu-modules-2.6.24-16-server ...
FATAL: Could not open '/boot/System.map-2.6.24-16-server': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-16-server
Cannot find /lib/modules/2.6.24-16-server
update-initramfs: failed for /boot/initrd.img-2.6.24-16-server
dpkg: error processing linux-ubuntu-modules-2.6.24-16-server (--purge):
 subprocess post-removal script returned error exit status 1
Removing linux-ubuntu-modules-2.6.24-16-virtual ...
FATAL: Could not open '/boot/System.map-2.6.24-16-virtual': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-16-virtual
Cannot find /lib/modules/2.6.24-16-virtual
update-initramfs: failed for /boot/initrd.img-2.6.24-16-virtual
dpkg: error processing linux-ubuntu-modules-2.6.24-16-virtual (--purge):
 subprocess post-removal script returned error exit status 1
dpkg: linux-image-2.6.24-19-generic: dependency problems, but removing anyway as you request:
 linux-ubuntu-modules-2.6.24-19-generic depends on linux-image-2.6.24-19-generic.
Removing linux-image-2.6.24-19-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /vmlinuz-2.6.24-16-386
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-2.6.24-19-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-21-generic
Found kernel: /vmlinuz-2.6.24-16-386
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

rmdir: failed to remove `/lib/modules/2.6.24-19-generic': Directory not empty
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-16-generic
 linux-ubuntu-modules-2.6.24-16-server
 linux-ubuntu-modules-2.6.24-16-virtual


---

### Post by Marine1 on 2008-12-20
Here's the output on your second suggestion.

> aaron@aaron-desktop:~$ cd /boot
aaron@aaron-desktop:/boot$ sudo > initrd.img-2.6.24-19-generic
bash: initrd.img-2.6.24-19-generic: Permission denied
aaron@aaron-desktop:/boot$ sudo > initrd.img-2.6.24-19-generic.bak
bash: initrd.img-2.6.24-19-generic.bak: Permission denied
aaron@aaron-desktop:/boot$ sudo > vmlinuz-2.6.24-16-386
bash: vmlinuz-2.6.24-16-386: Permission denied
aaron@aaron-desktop:/boot$ sudo > vmlinuz-2.6.24-19-generic
bash: vmlinuz-2.6.24-19-generic: Permission denied
aaron@aaron-desktop:/boot$
aaron@aaron-desktop:/boot$ sudo > initrd.img-2.6.24-19-generic
bash: initrd.img-2.6.24-19-generic: Permission denied
aaron@aaron-desktop:/boot$      

---

### Post by albinootje on 2008-12-20
Okay, looks a bit better.
What gives :
```

df -h
sudo mkdir -p /lib/modules/2.6.24-16-generic
sudo touch /boot/System.map-2.6.24-16-server
sudo mkdir -p /lib/modules/2.6.24-16-server
sudo touch /boot/System.map-2.6.24-16-virtual
sudo mkdir -p /lib/modules/2.6.24-16-virtual
sudo apt-get -f install
sudo apt-get autoremove

```

---

### Post by albinootje on 2008-12-20
> **Marine1 said:**
> Here's the output on your second suggestion.

Excuse me, that was wrong :(
Please try this to make more space :
```

cd /boot
sudo su
> initrd.img-2.6.24-19-generic
> initrd.img-2.6.24-19-generic.bak
> vmlinuz-2.6.24-16-386
> vmlinuz-2.6.24-19-generic
exit

```

---

### Post by Marine1 on 2008-12-20
Here's the response to the two things you sent me to put in.

> aaron@aaron-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb3             462G  4.7G  434G   2% /
varrun                1.5G  216K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G   88K  1.5G   1% /dev
devshm                1.5G   12K  1.5G   1% /dev/shm
lrm                   1.5G   39M  1.5G   3% /lib/modules/2.6.24-21-generic/volatile
/dev/sdb2              46M   26M   18M  60% /boot
gvfs-fuse-daemon      462G  4.7G  434G   2% /home/aaron/.gvfs
aaron@aaron-desktop:~$ sudo mkdir -p /lib/modules/2.6.24-16-generic
[sudo] password for aaron:
aaron@aaron-desktop:~$ mkdir -p /lib/modules/2.6.24-16-generic
aaron@aaron-desktop:~$ cd /boot
aaron@aaron-desktop:/boot$ sudo su
root@aaron-desktop:/boot# > initrd.img-2.6.24-19-generic
root@aaron-desktop:/boot# > initrd.img-2.6.24-19-generic.bak
root@aaron-desktop:/boot# > vmlinuz-2.6.24-16-386
root@aaron-desktop:/boot# > vmlinuz-2.6.24-19-generic
root@aaron-desktop:/boot# exit
exit
aaron@aaron-desktop:/boot$


---

### Post by albinootje on 2008-12-20
And what does :
```

sudo dpkg -P --force-all linux-image-2.6.24-19-generic linux-restricted-modules-2.6.24-19-generic linux-ubuntu-modules-2.6.24-16-generic linux-ubuntu-modules-2.6.24-16-server linux-ubuntu-modules-2.6.24-16-virtual
linux-ubuntu-modules-2.6.24-19-generic

sudo apt-get -f install

sudo apt-get autoremove

```
give now ?

---

### Post by Marine1 on 2008-12-20
Sorry... I actually restarted my computer because I gained some ability to update.

When I ran the updates though, here's what I got.  An error box popped up saying this:

> E: /var/cache/apt/archives/linux-image-2.6.24-22-generic_2.6.24-22.45_i386.deb: failed in buffer_write(fd) (10, ret=-1)

It again told me I had dependency problems.

I don't know how to get the whole set of terminal output from the "Changes Applied" window, so I can't give you that.

---

### Post by albinootje on 2008-12-20
> **Marine1 said:**
> Sorry... I actually restarted my computer because I gained some ability to update.
When I ran the updates though, here's what I got.  An error box popped up saying this:
It again told me I had dependency problems.

Hmm, okay, thanks for the information.

This weird error is not about one of your older kernels.

I think you might want to consider backing up your /home (and perhaps some /etc settings), and do a fresh install, and then restore /home again.
Because it's getting pretty complicated to solve this problem. :(

---

### Post by Marine1 on 2008-12-20
Eh.  You're probably right.  I'm gonna have to figure out how to install it onto this external HDD though... that will not be fun.

---

### Post by albinootje on 2008-12-20
> **Marine1 said:**
> Eh.  You're probably right.  I'm gonna have to figure out how to install it onto this external HDD though... that will not be fun.

You mean backing up /home to the external disk ?
Or do you want to install Ubuntu an the external disk ?

You can back up your /home like this, assuming the external disk is mounted at /media/disk-1/ :
```

sudo tar czvf /media/disk-1/home.tar.gz /home/

```

Just copying files to a FAT32 formatted disk would lose the permissions/ownership of the files.
And remember that FAT32 has the [...] 4 Gb file-size limit!

---

### Post by Marine1 on 2008-12-20
I installed it onto the external disk.  It took a few tries to get it right.  I'm not looking forward to starting from scratch.  Is there any way to just reset the operating system back to its original condition WITHOUT re- installing it?

---

### Post by albinootje on 2008-12-20
> **Marine1 said:**
> I installed it onto the external disk.  It took a few tries to get it right.  I'm not looking forward to starting from scratch.  Is there any way to just reset the operating system back to its original condition WITHOUT re- installing it?

Okay, can you try the following please ? (Assuming that you have internet-connection).
```

sudo apt-get clean
sudo apt-get -f install

```
And post the possible errors.

---

