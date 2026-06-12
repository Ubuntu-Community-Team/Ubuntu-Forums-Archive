---
title: "speeding up startup with readahead"
date: 2005-07-14
forum: Desktop Environments
---

### Post by flying_icarus on 2005-07-14
Hello everyone! ;)

I've been optimising the services for faster install (rather, turning them off), and I noticed this readahead script (usually gives the message "Reading desktop files" when booting).

man,info, locate, even google failed to provide much detail about it, other than that it's reading files entered in it's config file while the boot process is waiting for non-disk related services (for instance waiting for an IP adress). Those files are thus cached for faster startup of programs which need them.

So, I did some stracing and came up with a lot of files KDE reads when starting up, pasted them in there, and it does seem that KDE is starting a bit faster.  \\:D/ 

Has anyone been experimenting with this, or perhaps even knows of a documentation page for readahead? :)

---

### Post by Triton on 2005-07-15
Post your findings and stats please.   :)

---

### Post by flying_icarus on 2005-07-15
Ok, after tinkering with a stopwatch and restarting six times, here are the results.

Startup time with readahead = 46 sec.
Startup time w/o readahead = 51 sec.

The posted results are the fastest times between 3 runs for each setup (to minimise the influence of the varying delay of getting an IP adress), between the start of kernel loading and the time the desktop in KDE opens up (for this I enabled autlogin in KDM)

It seems that there is some benefit from readahead, as 5 seconds is too big to be user error in timing with a stop watch. ;) A different hardware/services setup may yield more or less, I don't know. Perhaps a machine with more RAM would gain more.

For comparison purposes (if someone is interested), my harware is an AMD XP 2000+, 512 MB RAM, MSI nfoce2 motherboard with ATI 9800XT, two optical drives and a Maxtor 160GB ATA hard drive with 8 MB cache.

The kernel is vanilla 2.6.12.2 and the system is prelinked, and a lot of unneccessary (for desktop use) services are disabled, but the extras are squid proxy and firestarter firewall.

If someone is interested, I can write a short guide how to do this readahead thing, and maybe we can compare numbers. ;)

---

### Post by dangerous666 on 2005-09-03
[QUOTE=flying_icarus]Ok, after tinkering with a stopwatch and restarting six times, here are the results.

Startup time with readahead = 46 sec.
Startup time w/o readahead = 51 sec.

The posted results are the fastest times between 3 runs for each setup (to minimise the influence of the varying delay of getting an IP adress), between the start of kernel loading and the time the desktop in KDE opens up (for this I enabled autlogin in KDM)

It seems that there is some benefit from readahead, as 5 seconds is too big to be user error in timing with a stop watch. ;) A different hardware/services setup may yield more or less, I don't know. Perhaps a machine with more RAM would gain more.

For comparison purposes (if someone is interested), my harware is an AMD XP 2000+, 512 MB RAM, MSI nfoce2 motherboard with ATI 9800XT, two optical drives and a Maxtor 160GB ATA hard drive with 8 MB cache.

The kernel is vanilla 2.6.12.2 and the system is prelinked, and a lot of unneccessary (for desktop use) services are disabled, but the extras are squid proxy and firestarter firewall.

If someone is interested, I can write a short guide how to do this readahead thing, and maybe we can compare numbers. ;)[/QUOTE]

I'm Interested! 
Share your experiences.

---

### Post by kLy on 2005-09-08
Hey!

Has anyone found anything on this yet? Googling gets me nothing. Now the /etc/readahead lists a bunch of files. Does it put entries in automatically? Otherwise, what would be a good way to populate the list with what I actually run at startup and not the default? I sure as hell am not going to manally guess each file I use at startup and manually enter hundreds of files into the config :)

Has anyone found any info?

Thanks!

---

