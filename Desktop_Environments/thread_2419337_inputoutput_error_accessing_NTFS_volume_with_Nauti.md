---
title: "input/output error accessing NTFS volume with Nautilus"
date: 2019-05-20
forum: Desktop Environments
---

### Post by s_raiguel on 2019-05-20
This desktop hosts three independently bootable drives, with 18.04 Bionic and Suse 15.0 on SSD's and  Windows 10 on a dynamic (platter) drive.  Recently, after mounting the Windows drive in Bionic, I notice that some directories on the W10 drive appeared to be inaccessible via Nautilus, which would give an error message "Error when getting information for file /media/username/Win10/WINDOWS/somefile.exe: somefile.exe input/output error". 

Multiple attempts to access the directory will give various files as the one generating the error. If I repeatedly press F5 to refresh the list of files, Nautilus will eventually go ahead and read the directory in about one of four or five such attempts. There is no error accessing the directory from the command line. The Suse system, when booted, mounts accesses the same drive/directory without errors, although the "mount" command shows that, with either operating system, the fuseblk mount is identical.  Running ChkDsk in Windows shows no problems with the W10 drive, nor does the SMART information using gnome-disks indicate any problem. 

Since this issue has shown up only recently, it suggests a possible bug in the way the current version of Nautilus reads NTFS volumes.

---

### Post by TheFu on 2019-05-21
Did you file a bug report with supporting data against nautilus?  Google "ubuntu bug report" to find out how.

Do other GUI file managers like thunar or caja have the issue?  It might be with gvfs or gio libraries, not nautilus. I think all three share the gvfs and/or gio code.

I wasn't aware that dynamic Windows storage was officially supported by the NTFS driver. Could easily be a different version between the different Linuxen. Have you checked the ntfs driver version being used on the working and non-working systems?

---

