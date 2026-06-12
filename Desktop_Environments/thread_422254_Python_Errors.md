---
title: "Python Errors"
date: 2007-04-25
forum: Desktop Environments
---

### Post by taladan on 2007-04-25
I'm currently running Kubuntu Feisty.  After my upgrade, I'm getting a few errors when I try to install via adept or aptitude when it touches python.  I've tried sudo apt-get install --reinstall python and it still spits the errors at me (even when I did that)   Following is the output of one of the errors.  Any help with this would be greatly appreciated.

```
swift@grendel:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up python-pygame (1.7.1release-4.1) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 878, in run
    pkg = DebPackage('package', self.args[0], oldstyle=False)
  File "/usr/bin/pycentral", line 291, in __init__
    self.read_pyfiles()
  File "/usr/bin/pycentral", line 314, in read_pyfiles
    import subprocess
  File "/usr/lib/python2.4/subprocess.py", line 379, in <module>
    import pickle
  File "/usr/lib/python2.4/pickle.py", line 36, in <module>
    import warnings
  File "/usr/lib/python2.4/warnings.py", line 258, in <module>
    simplefilter("ignore", category=OverflowWarning, append=1)
NameError: name 'OverflowWarning' is not defined
dpkg: error processing python-pygame (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-pygame
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Taladan

---

### Post by dannyboy79 on 2007-04-25
sudo mv /usr/bin/pycentral /tmp

sudo apt-get -f update

sudo apt-get -f upgrade

---

### Post by taladan on 2007-04-25
That looks like it worked...Thank you for the timely fix!

Can you tell me exactly what it is that caused that?

Tal

---

### Post by dannyboy79 on 2007-04-25
i can't say, I found the fix using the search command within the forums. since I don't know what it does you should move it back now

sudo mv /tmp /usr/bin/pycentral

also, I found another solution in case this arise's again. [http://ubuntuforums.org/showthread.php?t=422849](http://ubuntuforums.org/showthread.php?t=422849)

---

### Post by durand on 2007-05-26
Thanks for that solution but only some of the packages seemed to install...I still have the problem with the packages "python2.4" and "python2.4-minimal"

EDIT: fixd it by deleting python2.4-minimal.postinst from /var/lib/dpkg/info though i still have those damn python errors when running some packages :(

---

