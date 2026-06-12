---
title: "clamav says linux-restricted.. files are &quot;Broken. Executable&quot;"
date: 2009-04-01
forum: General Help
---

### Post by ecowan on 2009-04-01
I have just installed and run freshclam, clamav and klamav. Klamav tells me that 
/lib/linux-restricted-modules/2.6.24-16-generic/fglrx/libfglrx_ip.a.GCC4 and ...-23 
and /lib/modules/2.6.24-23-generic/volatile/fglrx.ko are "Broken. Executable"

That sounds very scary. How can I fix them? I expect that if I let clamav quarantine these it will kill my system.

My system is working fairly well, with only a few minor quirks and the occasional freeze-up.

Any help, please. Thanks. -Erny

---

### Post by markharding557 on 2009-04-01
that seems very strange usually apt-get or synaptic gui tells you if a package is broken

---

### Post by mb_webguy on 2009-04-02
"Broken.Executable" is a generic warning that ClamAV could not parse the structure of the executable.  It doesn't mean the file is a virus, it just means ClamAV couldn't correctly parse the file.  The "Broken.Executable" message generally refers to Windows [Portable Exectuables]("http://en.wikipedia.org/wiki/Portable_Executable") that have a malformed header, and so it really doesn't surprise me much that you'd get false positives like that when scanning a Linux filesystem.  

Remember, ClamAV, like all anti-virus software, is primarily concerned with Windows viruses, since less than [30 Linux viruses]("https://help.ubuntu.com/community/Linuxvirus") have ever been identified, as opposed to [461 currently active Windows viruses]("http://www.wildlist.org/WildList/200902.htm") out of over 100,000 known.  Linux binaries are going to pop fairly often as false positives.

---

### Post by dcstar on 2009-04-02
> **ecowan said:**
> I have just installed and run freshclam, clamav and klamav. Klamav tells me that 
/lib/linux-restricted-modules/2.6.24-16-generic/fglrx/libfglrx_ip.a.GCC4 and ...-23 
and /lib/modules/2.6.24-23-generic/volatile/fglrx.ko are "Broken. Executable"
........

"Broken" usually means a missing link target, nothing to be concerned about.

---

### Post by ecowan on 2009-04-02
Thanks for the assurances. That's the imprssion I got from reading the clam documentation.

I do get 'broken package' from apt-get from time to time. Is it because of these files?

I worry that these 'corrupt' files are related to the kernel. And that, other than some phishing emails, they are the only 'corrupt' files found.

Can I uninstall the linux-restricted-modules-2.6.24-16-generic package? The presence of a ...23... copy suggests that I'm running 2.6.24-23.

Is there any way to repair the  ...23.... files, other than a re-install?

Thanks. - Erny

---

### Post by xenophed on 2009-04-02
why do people have virus software scan linux when all known viruses are for windows

---

### Post by ecowan on 2009-04-02
Because I _have_ been hit with a virus while running linux, although it was not Ubuntu but Xandros.

---

### Post by acidblue on 2009-04-02
> **xenophed said:**
> why do people have virus software scan linux when all known viruses are for windows

Someone using a winblows box might access a unix/linix mail-server and download or upload a virus and spread it to others on the network.
So ClamAv scans the email server so this doesn't happen.

---

### Post by EricNMiller on 2009-04-16
Last week after a virus scan, ClamAV warned that there were several ClamAV files that are broken executables on my system.

They are:

split.clam-wwpack.exeaa
split.clam-nsis.exeaa
split.clam-petite.exeaa
split.clam-upx.exeaa
split.clam.ea05.exeaa
split.clam.ea06.exeaa
split.clam-mew.exeaa

and split.clam.arjaa has an Input/Output error.  The GUI has never worked since I installed ClamAV on my system last month, but it does scan the hard drives for viruses.  It doesn't scan my email as it downloads from the server as the AVG 8.5 anti-virus does on my windoz machine.

Would it be best to remove ClamAV and reinstall?

Any help would be much appreciated.

---

### Post by winst0n on 2009-08-21
So the first scan took 2 or 3 days
21265 warnings.
Every time I try to install / run windows it acts up.
Avast gave me the names:
 win32:vitro
win32:Neeris-B[Wrm]
HTML:IFrame-EV[Trj]
Klam came up with ... { MANY } IFrame.HTML infections.
Some of them I went into the directories and erased the entire directories.

I've got 3 of these I am hesitating to delete:
libfglrx_ip.a.GCC4

If it is reasonable that Klam has misidentified these I will leave them alone.
The module has been updated twice (2.6.24-16, 2.6.24-23, 2.6.24-24).

Is there a linux tool to verify MBR, BOOT & PARTITION sectors?
Does Klam do it?
I'm not quite up to speed on looking at the raw data.
 I have a couple of thumb drives that may have been effected.
I also use the floppy drive so I have the old floppy BOOT sector worry too.

Has anyone ever heard of a reason for a "USB" folder that does not correspond to an actual flash drive?
What I have COULD be legitamate but I am concerned that virus activity either independently, or packaged with my Windows distribution may be the cause.

[FONT=Courier New][SIZE=4][SIZE=3]winston@ubuntu-9-04:/media$ ls
cdrom   disk    floppy   ntfsdisk    USB\040DISK
cdrom0  disk-1  floppy0  RED\0402GB  WHITE-DT-8G

winston@ubuntu-9-04:/media$ cd USB\ DISK
bash: cd: USB DISK: No such file or directory
winston@ubuntu-9-04:/media$ cd USB*
winston@ubuntu-9-04:/media/USB\040DISK$ ls
boot.bin      DOCS  $OEM$       syslinux.cfg  VALUEADD      WIN51IP
boot.catalog  I386  README.HTM  ubnfilel.txt  vesamenu.c32  win51ip.SP3
cmpnents      OEM   SUPPORT     ubnpathl.txt  WIN51
winston@ubuntu-9-04:/media/USB\040DISK$ cd \$OEM\$
winston@ubuntu-9-04:/media/USB\040DISK/$OEM$$ ls
$$  $Docs
winston@ubuntu-9-04:/media/USB\040DISK/$OEM$$ cd \$\$
winston@ubuntu-9-04:/media/USB\040DISK/$OEM$/$$$ ls
OEMDIR  Resources  system32  Web
winston@ubuntu-9-04:/media/USB\040DISK/$OEM$/$$$[/SIZE] 

[/SIZE][/FONT]And why is the weird "040" used it doesn't work to type it verbatim and it doesn't seem to work as a space.
I think it is supposed to be a space.
[http://msdn.microsoft.com/en-us/library/4edbef7e(VS.71).aspx]("http://msdn.microsoft.com/en-us/library/4edbef7e%28VS.71%29.aspx")
I'll rename my red one anyway.
Should I erase the "fake" one.
Should I find a different Windows distribution?

---

