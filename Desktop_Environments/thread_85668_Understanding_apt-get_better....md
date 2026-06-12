---
title: "Understanding apt-get better..."
date: 2005-11-03
forum: Desktop Environments
---

### Post by DocFox on 2005-11-03
I was mucking around with some setting in pybliographer (bibtex reference manager) and now it doesnt work...

        > ben@nutmeg:~$ pybliographic &
        [1] 9762
        ben@nutmeg:~$ Traceback (most recent call last):
          File "/usr/bin/pybliographer", line 155, in ?
            Config.load_user ()
          File "/usr/share/pybliographer/Pyblio/Config.py", line 337, in
        load_user
            set (item, changed [item])
          File "/usr/share/pybliographer/Pyblio/Config.py", line 152, in
        set
            ConfigItems [key].set (value)
          File "/usr/share/pybliographer/Pyblio/Config.py", line 49, in
        set
            raise ValueError, \
        ValueError: value of `medline/mapping' should be of type
        Dictionary (String, String)

I deleted all the configuration files in my HOME directory and in
usr/local/pybliographer, and also ran:
        > 
        apt-get --purge remove pybliographer
        apt-get clean

Then:
> 
        ben@nutmeg:~$ sudo apt-get install pybliographer
        Reading package lists... Done
        Building dependency tree... Done
        The following NEW packages will be installed:
          pybliographer
        0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
        Need to get 461kB of archives.
        After unpacking 2007kB of additional disk space will be used.
        Get:1 [http://il.archive.ubuntu.com](http://il.archive.ubuntu.com) breezy/universe pybliographer
        1.2.5-1ubuntu1 [461kB]
        Fetched 461kB in 7s (65.5kB/s)
        
        Preconfiguring packages ...
       ** Selecting previously deselected package pybliographer.**
        (Reading database ... 111151 files and directories currently
        installed.)
        Unpacking pybliographer
        (from .../pybliographer_1.2.5-1ubuntu1_all.deb) ...
        Setting up pybliographer (1.2.5-1ubuntu1) ...

The error returns.

Is it possible that ubuntu is reusing previously selected package, with some faulty config files that I screwed up  alive and well?

If anyone has any ideas how i can do  totally clean pybliographer install, i'd be very grateful.

My thanks in advance to anyone who can help me out.
Ben Fox

---

### Post by adwait on 2005-11-03
No, when it says Selecting previous deslected package, it simply means that it is installing a new package which was present in the repositories but not installed on your system.

---

### Post by queenorych on 2005-11-03
setting are generally stored in your home directory in .(program name).  So check for .pybliographer in your home directory.  Also check the gnome registry, its what gconf.  It may have some setting there.  Also check for any pybliographer lists or help.

---

### Post by DocFox on 2005-11-03
cleaned out all the pybliographer stuff already, which makes the whole thing all the more confusing.

[INDENT]sudo find / -depth -name pyb* -ok rm{} \;[/INDENT]

ben

---

