---
title: "Howto fix broken Eiciel ACL editor in Gnome"
date: 2009-05-25
forum: General Help
---

### Post by cmost on 2009-05-25
Many people, especially those who manage multiple users on their computer, like to have the same fine grained control over user access to files and folders as they do in Windows (with NTFS.)  Eiciel used to provide this level of control by adding a nice 'Access Control Lists' tab in the right-click properties dialog in Gnome.  Right-clicking any file or folder would allow the system administrator to manage individual user and group rights to any file and folder on the system with ease.  Some time ago, this feature was lost as Eiciel became broken in Debian and the problematic package made its way into Ubuntu and was never fixed.  Consequently, Ubuntu users must use the standalone Eiciel client (found under Applications --> System Tools --> Eiciel) or resort to the command line ACL editing tools to manage access rights.  Both of these options are very cumbersome.

Here's how to get the 'Access Control List' tab back in the Gnome's folder / file properties dialog:

1.  First, you have to ensure your system is setup to utilize Access Control Lists (ACLs hereafter) to begin with.
     a.  Open synaptic and search for ACL; install the acl package.  Do NOT install the Eiciel package.  If Eiciel is already installed on your system, completely remove it!
     b.  As root, edit /etc/fstab.  Add acl to the partitions on which you'd like to have fine grained user / group permissions control.  See the following example:

UUID=8ad8e3cd-1ecf-41b6-ac5c-c011fa0b24cf /     ext4 relatime,errors=remount-ro,acl     0       1
# /home was on /dev/sda3 during installation
UUID=9757c91c-bdda-42e9-850d-435fb04fc2b7 /home     ext4    relatime,acl     0       2

Save the modified /etc/fstab file.

2.  Get the fixed Eiciel DEB package from Debian Sid's repository.  Go here:  [http://ftp.us.debian.org/debian/pool/main/e/eiciel/](http://ftp.us.debian.org/debian/pool/main/e/eiciel/)

Get version 0.9.6.1-3 for your architecture (386, amd64, etc.)  Save the file somewhere in your home directory

3.  Install the new version by changing to the directory where you saved it and issuing this command as root:  sudo dpkg -i *.deb; or, simply double-click the file and let Gdebi install it graphically.

4.  Restart the computer.  Now, when you right-click any file or folder you should have an 'Access Control List' tab in which you can manage user / group permissions with ease.

Enjoy!

---

### Post by BryanPearson on 2009-07-03
I am delighted to find out there is a fix for this.

I am less delighted than I might have been before tonight, though.
I am currently working with 8.10 and performed a file copy operation using Nautilus, MC (Midnight Commander), and the cp command from the command line.  Not one produced the same results when copying files and directories having default ACL entries.  I am going to look at it some more, and try to find a bug report (I can't be the first to see this!) but if I can't work this out I will post the problem in another thread.

I am trying to replace a Windows FTP site with one using Ubuntu and pureFTPd.  Individual user directories are trivial to support with Windows, but without ACL working, Linux hasn't a prayer of supporting our current setup.

---

### Post by MonkeyCookie on 2009-09-01
Yay! Thank you.  I had this working in a previous version of Ubuntu, and I was unable to figure out why it wasn't working in Jaunty (9.04). I hope they get that Eiciel package fixed because that Access Control List tab is a very nice thing to have.

---

### Post by cmost on 2009-09-02
> **BryanPearson said:**
> I am delighted to find out there is a fix for this.

I am less delighted than I might have been before tonight, though.
I am currently working with 8.10 and performed a file copy operation using Nautilus, MC (Midnight Commander), and the cp command from the command line.  Not one produced the same results when copying files and directories having default ACL entries.  I am going to look at it some more, and try to find a bug report (I can't be the first to see this!) but if I can't work this out I will post the problem in another thread.

I am trying to replace a Windows FTP site with one using Ubuntu and pureFTPd.  Individual user directories are trivial to support with Windows, but without ACL working, Linux hasn't a prayer of supporting our current setup.

You have to be careful.  Some Linux tools do NOT preserve ACL information when copying or backing up files!!  An important but easily overlooked aspect of introducing new features like EAs and ACLs is backup. Standard tools like GNU tar and GNU cpio do not include EA or ACL support. The ustar and cpio archive formats on which these tools are based do allow certain extensions, but no standards for storing EAs or ACLs have yet been defined.

The current version of POSIX.1 defines a new utility called pax, which stands for portable archive interchange. The pax utility supports both the ustar and cpio archive formats in addition to the new pax archive format. This new format is based on ustar and is, to a large degree, compatible with ustar. Pax introduces a mechanism called extended headers. Extended headers consist of a list of attributes very similar to EAs. They are used to store things that cannot be represented in ustar headers, such as sub-second resolution file timestamps, or file sizes of 8 Gib or more.

The pax archive format is a good match for storing EAs and ACLs. As neither EAs nor ACLs are part of any POSIX standard, no specific format for EAs or ACLs to use in extended headers has been defined. The specification leaves room for vendor-specific attributes tagged with the vendor name, so even if no agreement can be reached soon on the EA or ACL formats to be used, the vendor-specific extensions can at least be distinguished and implementations may support more than one extension.

A benefit of the pax format is that most pax archives can also be restored with tar implementations. To tar, extended headers look like files of an unknown type. The information stored in the extended headers will be lost, but files and directories will be extracted correctly. This will not work for pax archives that contain files 8 GiB or more in size; this is the maximum file size in tar archives.

The following solutions exist for backing up (and later restoring) EAs and ACLs:

    * Jörg Schilling's implementation of pax and tar called star includes support for POSIX.1e ACLs and a few others. The resulting archives are portable among systems that implement various versions of POSIX ACLs, including FreeBSD, Irix, HP-UX, Compaq/HP Tru64, Linux, Solaris. A patch that implements Linux EA support in star exists as well. Star is available from [ftp://ftp.berlios.de/pub/star/](ftp://ftp.berlios.de/pub/star/).

    * On the XFS file system, the xfsdump and xfsrestore utilities can be used. However, the backup format is file-system-specific, so this approach is not recommended.

    * Finally, the getfattr and getfacl utilities can dump ACLs and EAs to text files, which the setfattr and setfacl utilities are able to restore. This works reasonably well for restoring complete backups, but it is impractical for restoring individual files. 

Application Support for ACLs:

Today, the most basic tools that are needed to operate a system with EAs and ACLs are available: there is EA and ACL support in the basic file utilities (ls, cp, and mv), there are utilities for manipulating EAs and ACLs from the command line, and there are solutions for backing up and restoring a system that uses those features. Still, there are many applications that are lacking support. Although for many of them this is irrelevant, there are some classes of applications for which this leads to problems. This includes file managers, editors, and file system synchronization tools.

File managers usually can copy and move files and allow permissions to be changed. UNIX kernels have no functions for copying files or for moving files across file system boundaries. Therefore, these operations are implemented by reading from the source file and copying the data to the destination file. The kernel has no way of telling which sequences of operations are file copies or moves and which are something else, so it cannot preserve EAs and ACLs automatically. This means that applications must take care of preserving EAs and ACLs themselves as needed.

Front-ends that allow manipulation of permissions usually allow manipulation of the standard POSIX.1 permissions, but none are known yet that allow manipulation of ACLs. It is quite likely that for the foreseeable future, ACL editing support will not become available except with the command line utilities.

Some editors suffer from the file copying problem as well. There are two ways of safely modifying a file. One is to create a copy of the original file and then to modify the original file. The other is to rename the original file and then to create a new file that includes the modifications in the original file's place. The latter is equivalent to copying files as far as EAs and ACLs are concerned. The option used also has additional consequences for files that are symlinks and for files with a link count greater than one. Emacs and vi, the most popular editors on UNIX-like systems, both can be configured to use either method.

When preserving permissions, it is important that as much information is preserved as possible. Although this seems obvious, correctly implementing this is not trivial. There are a number of complications that make that operation prone to implementation errors. This is especially true if the source and destination files reside on different file systems, only one of which has ACL support. To take this additional burden from programmers, the current version of libacl includes functions for copying EAs and ACLs between files [8].

It would also be nice to have EA and ACL support in popular utilities like scp and rsync. Unfortunately, utilities that transfer files between different systems have a much harder time handling incompatibilities. Only some UNIX-like systems support the POSIX.1e ACL library functions and other systems have their own operating system interfaces. Even worse, the semantics of ACLs differs widely among UNIX systems alone, not to speak of non-UNIX systems. The semantics and system interfaces for EAs unfortunately are different among various systems as well.

---

### Post by Ralph L on 2009-09-09
Cmost

You say that cp supports ACL.  Yet when I use cp it does not copy the ACL permissions to the new file even on the same disk.  Is there a special cp parameter that must be used with cp to make it copy permissions?

Ralph

---

### Post by mattydee on 2009-11-08
Thanks for this! 

BTW: You don't need to restart the computer, just nautilus. 
```
nautilus -q 
```will kill it, and it will then be restarted by gnome.

---

