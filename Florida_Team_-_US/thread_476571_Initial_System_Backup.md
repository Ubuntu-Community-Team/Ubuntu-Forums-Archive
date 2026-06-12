---
title: "Initial System Backup"
date: 2007-06-17
forum: Florida Team - US
---

### Post by satorisan on 2007-06-17
My system is stable.::D
I have made several configuration changes and added several new apps.
One of the new apps is Webmin. I would like to use it for my initial system backup.
It has been difficult to find documentation on what should be included in this backup.
I would also like to do this backup to the CD burner on my system.
If there is anyone who can provide assistance, I would be very grateful.

---

### Post by feravolo on 2007-06-17
There is a nice article about the Linux Files System in Issue One of the Ubuntu e-magazine:

[http://fullcirclemagazine.org](http://fullcirclemagazine.org)

In order to help develop your backup strategy you should get to know where everything is stored, for example to backup the user files on your system make a copy of /home. One nice thing about Linux is all the configuration files for your system are stored as text files and you can edit them with a simple text editor. Also make sure that you copy all the hidden files, which begin with the "dot", from the shell you can see them with the ls -la command or select "View" and "Show Hidden Files" from Nautilus/GNOME.

Here, you will find descriptions of the major top level directories for any type of Linux:

[COLOR="Red"]**/bin**[/COLOR]

All of the essential user programs are contained in the /bin directory, these files represent the bare minimum set of tools required to use a Linux system.

Tools like the shell and the file system commands (ls, cp, mkdir, cat ) are stored here. The /bin directory usually doesn't receive modification after installation, except if they are updated in a major release of the operating system.

Many of these programs work the same way they did back in the 70's in the earliest versions of UNIX. You may view the contents of the /bin directory using the following list structure command: ls -la /bin

[COLOR="Red"]**/boot**[/COLOR]

Files that are used by the Boot Loader (GRUB), including the kernel files that are required to start Ubuntu. This is another directory also receives little modification after an installation, except when a new version of the kernel is released. Storing the kernel files in the /boot directory instead of the root allows for dual-booting. Remember if you want to dual-boot with a version or multi-boot versions of windows, install all of the windows versions first starting with the oldest (i. e. 98SE, NT4, 2000, XP, 2003/SP1, Vista, Longhorn-Beta).

[COLOR="Red"]**/dev**[/COLOR]

Again, remember everything in Linux is a file, even hardware devices like serial ports, hard disks, and scanners. In order for you to be able to access these devices, a special file called a device node has to be present. All device nodes are stored in the /dev directory.

[COLOR="Red"]**/etc**[/COLOR]

Linux system configuration files are stored in the /etc directory. For example, the X Windows configuration file, the user database, and systems startup scripts all reside under the /etc directory.

[COLOR="Red"]**/home**[/COLOR]

Linux is a true multiuser operating system, every user on the system is given an account and a unique home directory (/home/their-name) for personal files. User home directories contain the files that are located on user's desktop and other personal files in their home folder. If you plan to have a lot of users on your system /home should be assigned to it's own hard disk drive or drive partition.
[B]
[COLOR="Red"]/lib[/B][/COLOR]

Required Ubuntu operating systems libraries are found in the /lib directory. These include the C programming language library, the dynamic loader, other systems libraries, and kernel modules.

[COLOR="Red"]**/mnt**[/COLOR]

Directory containing the temporary mount points for working on hard disks or removable drives.

[COLOR="Red"]**/opt**[/COLOR]

Optional software packages can be installed here to make them easy to remove later, you are free to add anything you want to /opt.
[COLOR="Red"]
**/proc**[/COLOR]

Various pieces of information that the kernel wants you to know are accessed via files in the /proc directory. You can also send information to the kernel through some of these files. For example type: cat /proc/cpuinfo, and you will see information about your system displayed for you.

[COLOR="Red"]**/root**[/COLOR]

Linux's system administrator ( a. k. a. the super user) logs in as the root, therefore in order to maintain order the super user's home directory is kept in /root separate from the other users( /home). which allows you to keep the user directories under /home on a different physical piece of hardware then the super user's home directory.

[COLOR="Red"]**/sbin**[/COLOR]

Essential programs that are run by root and during the system bootup process are kept here in /sbin. Only the super user can run programs in this directory. Ubuntu allows any user to act as the super user using the super user do (sudo) command or using the root terminal under GNOME.

[COLOR="Red"]**/tmp**[/COLOR]

The temporary storage location. All users have read and write access to this directory.
[COLOR="Red"]
**/usr**[/COLOR]

Slash usr (/usr) is the big directory on a Ubuntu/ Linux system, this is where applications are installed. For example: source code, executable code, documentation, the kernel source code, and the X Window system.

In other words this is directory branch that you will most likely find the programs that you have installed.

[COLOR="Red"]**/var**[/COLOR]

Another big directory branch which includes System log files, cache data, and program lock files are stored here. This is the directory for frequently-changing data.

---

### Post by dantrevino on 2007-06-18
The type of backup you need is really dependent on what pain you are willing to do during a restore.

For most simple backups, i recommend sbackup.  Its very straightforward and works.

AptOnCD will backup your installed packages.

So, if you're willing to re-install a full ubuntu (relatively painless), a combination of the above will be fairly easy.

[http://onlyubuntu.blogspot.com/2007/03/backup-and-restore-ubuntu-system-using.html](http://onlyubuntu.blogspot.com/2007/03/backup-and-restore-ubuntu-system-using.html)

---

