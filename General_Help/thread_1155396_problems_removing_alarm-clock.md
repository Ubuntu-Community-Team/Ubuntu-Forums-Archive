---
title: "problems removing alarm-clock"
date: 2009-05-10
forum: General Help
---

### Post by benzs_s on 2009-05-10
I'm trying to get rid of alarm-clock because it's just rubbish and freezes the whole system every time it starts, but I get this output in terminal:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  alarm-clock*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1835kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing alarm-clock (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 alarm-clock
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

And if I attempt a reinstall:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  alarm-clock
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/595kB of archives.
After this operation, 184kB of additional disk space will be used.
Selecting previously deselected package alarm-clock.
(Reading database ... 136733 files and directories currently installed.)
Preparing to replace alarm-clock 0.9.17-1~getdeb1 (using .../alarm-clock_0.9.18-3ubuntu0.1_all.deb) ...
dpkg (subprocess): unable to execute old pre-removal script: Exec format error
dpkg: warning - old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2190, in <module>
    main()
  File "/usr/bin/pycentral", line 2184, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1639, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 377, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 408, in read_pyfiles
    self.pkgconfig.set('pycentral', 'include-links', '0')
  File "/usr/lib/python2.6/ConfigParser.py", line 669, in set
    ConfigParser.set(self, section, option, value)
  File "/usr/lib/python2.6/ConfigParser.py", line 377, in set
    raise NoSectionError(section)
ConfigParser.NoSectionError: No section: 'pycentral'
dpkg: error processing /var/cache/apt/archives/alarm-clock_0.9.18-3ubuntu0.1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/alarm-clock_0.9.18-3ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I honestly don't understand what's going on. Any ideas?

---

### Post by lovinglinux on 2009-05-11
Try "System >> Administration >> Synaptic Package Manager >>Edit >>Fix Broken Packages"

BTW, alarm-clock also froze on my system, but I didn't have any troubles removing it.

---

### Post by dcstar on 2009-05-11
> **benzs_s said:**
> I'm trying to get rid of alarm-clock because it's just rubbish and freezes the whole system every time it starts, but I get this output in terminal:

```

.........
Errors were encountered while processing:
 **/var/cache/apt/archives/alarm-clock_0.9.18-3ubuntu0.1_all.deb**
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I honestly don't understand what's going on. Any ideas?

Manually delete that file and try the reinstall again.

---

### Post by benzs_s on 2009-05-11
Thanks for the replies, guys.

lovinglinux: Doing that just resulted in a similar output to the first code I pasted

dcstar: I looked, and the .deb wasn't there! 

So... I looked in the directories alarm-clock is supposed to be in and there were 0 byte size files. Just removed the alarm-clock entry from /var/lib/dpkg/status, reinstalled then purged. I *think* that completely removed it.

Cheers for your help anyway :)

---

