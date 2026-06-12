---
title: "NTFS and Jackalope"
date: 2009-05-13
forum: General Help
---

### Post by jcobban on 2009-05-13
I have encountered a couple of behaviors that I do not entirely understand with respect to support for NTFS by Nautilus in 9.04.
[LIST=1]
[*]"Cannot move to Trash" message when deleting
[*]"Do you want to run "filename.html", or display its contents?" on double click of HTML files.
[/LIST]
The first issue is resolved when I change the mount options in /etc/fstab to:

relatime,errors=remount-ro,umask=000,uid=1000,gid=1000

Note that I have to use umask=000, rather than the 007 suggested by some documents, because I am sharing the web files directory between the Apache server on Windoze and the copy on Linux.  When I specified umask=007 the Linux Apache server did not have authority to read that directory.

Why does Nautilus make an issue of the fact that the HTML, TXT, CSV, etc. files are flagged as executeable when it does not do so for .DOC, .XLS, and .ODT?  I do not see much point in being able to execute files from an NTFS file system although I know that .EXE files are handled by passing them to WINE.  Can I resolve this second issue by setting umask=111, or are there undesirable side effects, aside from needing to explicitly invoke WINE to run a .EXE?

---

### Post by albert ozzy on 2009-05-13
the 2nd problem doesn't have anything to do with your filesystem. I may say you accidentally run the command  chmod +x on the folder you keep your html's? Cos it's a common mistake while configuring Apache. Changing a file's permission (chmod) may have cause it to be executable.

---

### Post by jcobban on 2009-05-14
> **albert ozzy said:**
> the 2nd problem doesn't have anything to do with your filesystem. I may say you accidentally run the command  chmod +x on the folder you keep your html's? Cos it's a common mistake while configuring Apache. Changing a file's permission (chmod) may have cause it to be executable.

Because the New Technology File System (NTFS) was designed by Micro$oft and Micro$oft likes to pretend that the only operating system in the world is Windoze, NTFS does not support specifying UNIX file access modes.  That is there is no spot in the NTFS data structures to store the umask, uid, and gid.  This is also true of FAT although that is because FAT was designed by IBM back in the 1970s before UNIX became popular outside of academia.  As a result the NTFS filesystem implementation requires specifying as a mount option the umask, uid, and gid which apply to every file in the entire filesystem.  You cannot issue chmod or any other command relating to the UNIX file access system against a file in the NTFS filesystem.

So the 'x' option is specified for every file in my NTFS filesystem, and I can only turn it off globally.

I would appear that Nautilus has been configured with a list of extensions for which it ignores the 'x' option.  This would appear to be an "inclusive" list rather than an "exclusive" list.  In my opinion the only files from an NTFS file system that Nautilus should attempt to execute are those with the .EXE, and .BAT options, which should be executed by handing them over to WINE (or equivalent alternative service).  There should not normally be any UNIX executeables or scripts stored in an NTFS filesystem, although there could be on a FAT filesystem since some media, for example USB drives, currently only use FAT filesystems.

I would welcome further discussion of this.

---

### Post by albert ozzy on 2009-05-14
> Because the New Technology File System (NTFS) was designed by Micro$oft and Micro$oft likes to pretend that the only operating system in the world is Windoze, NTFS does not support specifying UNIX file access modes.

Exactly. NTFS does not support UNIX file access modes and has very useless and numerous permission modes but you can still chmod it by mounting the partition and using the umask option. But umask is the reverse of a file system permission. I mean it describes the restrictions.       The formatting is identical to the format of chmod command.       In other words, 0 allows all permissions, 2 denies write access, and 7 denies any access. For this reason i said it's a common mistake to chmod wrong.

Anyway thanks for your NTFS and FAT review :D

---

### Post by AlexsAntidote on 2009-05-14
For what it's worth, I learned an awful lot from your discussion guys. Thank you.

---

