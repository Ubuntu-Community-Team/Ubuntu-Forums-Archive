---
title: "apt-get upgrade -&gt; python does not match the python default version"
date: 2009-04-30
forum: General Help
---

### Post by ksenux on 2009-04-30
Hi!

**PLEASE HELP!**

Ubuntu 9.04,  2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux

I can't fix problem , during the 
update apt-get update & & apt-get upgrade
I get the following error:

Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
16 not fully installed or removed.
Need to get 0B/1201kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? (Reading database ... 148875 files and directories currently installed.) 
Preparing to replace update-manager-core 1:0.111.7 (using .../update-manager-core_1%3a0.111.7_amd64.deb) ... 
Traceback (most recent call last): 
  File "/usr/bin/pycentral", line 2190, in <module> 
    main() 
  File "/usr/bin/pycentral", line 2184, in main 
    rv = action.run(global_options) 
  File "/usr/bin/pycentral", line 1638, in run 
    runtimes = get_installed_runtimes(with_unsupported=True) 
  File "/usr/bin/pycentral", line 276, in get_installed_runtimes 
    default_version = pyversions.default_version(version_only=True) 
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version 
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default 
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6 
dpkg: warning - old pre-removal script returned error exit status 1 
dpkg - trying script from the new package instead ... 
Traceback (most recent call last): 
  File "/usr/bin/pycentral", line 2190, in <module> 
    main() 
  File "/usr/bin/pycentral", line 2184, in main 
    rv = action.run(global_options) 
  File "/usr/bin/pycentral", line 1638, in run 
    runtimes = get_installed_runtimes(with_unsupported=True) 
  File "/usr/bin/pycentral", line 276, in get_installed_runtimes 
    default_version = pyversions.default_version(version_only=True) 
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version 
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default 
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6 
dpkg: error processing /var/cache/apt/archives/update-manager-core_1%3a0.111.7_amd64.deb (--unpack): 
 subprocess new pre-removal script returned error exit status 1 
Traceback (most recent call last): 
  File "/usr/bin/pycentral", line 2190, in <module> 
    main() 
  File "/usr/bin/pycentral", line 2184, in main 
    rv = action.run(global_options) 
  File "/usr/bin/pycentral", line 1472, in run 
    runtimes = get_installed_runtimes() 
  File "/usr/bin/pycentral", line 276, in get_installed_runtimes 
    default_version = pyversions.default_version(version_only=True) 
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version 
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default 
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6 
dpkg: error while cleaning up: 
 subprocess post-installation script returned error exit status 1 
Preparing to replace python-problem-report 1.0-0ubuntu5 (using .../python-problem-report_1.0-0ubuntu5_all.deb) ... 
Traceback (most recent call last): 
  File "/usr/bin/pycentral", line 2190, in <module> 
    main() 
  File "/usr/bin/pycentral", line 2184, in main 
    rv = action.run(global_options) 
  File "/usr/bin/pycentral", line 1638, in run 
    runtimes = get_installed_runtimes(with_unsupported=True) 
  File "/usr/bin/pycentral", line 276, in get_installed_runtimes 
    default_version = pyversions.default_version(version_only=True) 
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version 
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default 
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6 
dpkg: warning - old pre-removal script returned error exit status 1 
dpkg - trying script from the new package instead ... 
Traceback (most recent call last): 
  File "/usr/bin/pycentral", line 2190, in <module> 
    main() 
  File "/usr/bin/pycentral", line 2184, in main 
    rv = action.run(global_options) 
  File "/usr/bin/pycentral", line 1638, in run 
    runtimes = get_installed_runtimes(with_unsupported=True) 
  File "/usr/bin/pycentral", line 276, in get_installed_runtimes 
    default_version = pyversions.default_version(version_only=True) 
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version 
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default 
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6 
dpkg: error processing /var/cache/apt/archives/python-problem-report_1.0-0ubuntu5_all.deb (--unpack): 
 subprocess new pre-removal script returned error exit status 1 
Traceback (most recent call last): 
  File "/usr/bin/pycentral", line 2190, in <module> 
    main() 
  File "/usr/bin/pycentral", line 2184, in main 
    rv = action.run(global_options) 
  File "/usr/bin/pycentral", line 1472, in run 
    runtimes = get_installed_runtimes() 
  File "/usr/bin/pycentral", line 276, in get_installed_runtimes 
    default_version = pyversions.default_version(version_only=True) 
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version 
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default 
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6 
dpkg: error while cleaning up: 
 subprocess post-installation script returned error exit status 1 
Preparing to replace python-apport 1.0-0ubuntu5 (using .../python-apport_1.0-0ubuntu5_all.deb) ... 
Traceback (most recent call last): 
  File "/usr/bin/pycentral", line 2190, in <module> 
    main() 
  File "/usr/bin/pycentral", line 2184, in main 
    rv = action.run(global_options) 
  File "/usr/bin/pycentral", line 1638, in run 
    runtimes = get_installed_runtimes(with_unsupported=True) 
  File "/usr/bin/pycentral", line 276, in get_installed_runtimes 
    default_version = pyversions.default_version(version_only=True) 
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version 
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default 
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6 
dpkg: warning - old pre-removal script returned error exit status 1 
dpkg - trying script from the new package instead ... 
Traceback (most recent call last): 
  File "/usr/bin/pycentral", line 2190, in <module> 
    main() 
  File "/usr/bin/pycentral", line 2184, in main 
    rv = action.run(global_options) 
  File "/usr/bin/pycentral", line 1638, in run 
    runtimes = get_installed_runtimes(with_unsupported=True) 
  File "/usr/bin/pycentral", line 276, in get_installed_runtimes 
    default_version = pyversions.default_version(version_only=True) 
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version 
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default 
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6 
dpkg: error processing /var/cache/apt/archives/python-apport_1.0-0ubuntu5_all.deb (--unpack): 
 subprocess new pre-removal script returned error exit status 1 
Traceback (most recent call last): 
  File "/usr/bin/pycentral", line 2190, in <module> 
    main() 
  File "/usr/bin/pycentral", line 2184, in main 
    rv = action.run(global_options) 
  File "/usr/bin/pycentral", line 1472, in run 
    runtimes = get_installed_runtimes() 
  File "/usr/bin/pycentral", line 276, in get_installed_runtimes 
    default_version = pyversions.default_version(version_only=True) 
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version 
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default 
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6 
dpkg: error while cleaning up: 
 subprocess post-installation script returned error exit status 1 
Preparing to replace apport 1.0-0ubuntu5 (using .../apport_1.0-0ubuntu5_all.deb) ... 
Traceback (most recent call last): 
  File "/usr/bin/pycentral", line 2190, in <module> 
    main() 
  File "/usr/bin/pycentral", line 2184, in main 
    rv = action.run(global_options) 
  File "/usr/bin/pycentral", line 1638, in run 
    runtimes = get_installed_runtimes(with_unsupported=True) 
  File "/usr/bin/pycentral", line 276, in get_installed_runtimes 
    default_version = pyversions.default_version(version_only=True) 
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version 
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default 
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6 
dpkg: warning - old pre-removal script returned error exit status 1 
dpkg - trying script from the new package instead ... 
Traceback (most recent call last): 
  File "/usr/bin/pycentral", line 2190, in <module> 
    main() 
  File "/usr/bin/pycentral", line 2184, in main 
    rv = action.run(global_options) 
  File "/usr/bin/pycentral", line 1638, in run 
    runtimes = get_installed_runtimes(with_unsupported=True) 
  File "/usr/bin/pycentral", line 276, in get_installed_runtimes 
    default_version = pyversions.default_version(version_only=True) 
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version 
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default 
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6 
dpkg: error processing /var/cache/apt/archives/apport_1.0-0ubuntu5_all.deb (--unpack): 
 subprocess new pre-removal script returned error exit status 1 
Traceback (most recent call last): 
  File "/usr/bin/pycentral", line 2190, in <module> 
    main() 
  File "/usr/bin/pycentral", line 2184, in main 
    rv = action.run(global_options) 
  File "/usr/bin/pycentral", line 1472, in run 
    runtimes = get_installed_runtimes() 
  File "/usr/bin/pycentral", line 276, in get_installed_runtimes 
    default_version = pyversions.default_version(version_only=True) 
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version 
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default 
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6 
dpkg: error while cleaning up: 
 subprocess post-installation script returned error exit status 1 
Preparing to replace update-manager 1:0.111.7 (using .../update-manager_1%3a0.111.7_all.deb) ... 
Traceback (most recent call last): 
  File "/usr/bin/pycentral", line 2190, in <module> 
    main() 
  File "/usr/bin/pycentral", line 2184, in main 
    rv = action.run(global_options) 
  File "/usr/bin/pycentral", line 1638, in run 
    runtimes = get_installed_runtimes(with_unsupported=True) 
  File "/usr/bin/pycentral", line 276, in get_installed_runtimes 
    default_version = pyversions.default_version(version_only=True) 
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version 
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default 
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6 
dpkg: warning - old pre-removal script returned error exit status 1 
dpkg - trying script from the new package instead ... 
Traceback (most recent call last): 
  File "/usr/bin/pycentral", line 2190, in <module> 
    main() 
  File "/usr/bin/pycentral", line 2184, in main 
    rv = action.run(global_options) 
  File "/usr/bin/pycentral", line 1638, in run 
    runtimes = get_installed_runtimes(with_unsupported=True) 
  File "/usr/bin/pycentral", line 276, in get_installed_runtimes 
    default_version = pyversions.default_version(version_only=True) 
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version 
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default 
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6 
dpkg: error processing /var/cache/apt/archives/update-manager_1%3a0.111.7_all.deb (--unpack): 
 subprocess new pre-removal script returned error exit status 1 
Traceback (most recent call last): 
  File "/usr/bin/pycentral", line 2190, in <module> 
    main() 
  File "/usr/bin/pycentral", line 2184, in main 
    rv = action.run(global_options) 
  File "/usr/bin/pycentral", line 1472, in run 
    runtimes = get_installed_runtimes() 
  File "/usr/bin/pycentral", line 276, in get_installed_runtimes 
    default_version = pyversions.default_version(version_only=True) 
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version 
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default 
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6 
dpkg: error while cleaning up: 
 subprocess post-installation script returned error exit status 1 
Errors were encountered while processing: 
 /var/cache/apt/archives/update-manager-core_1%3a0.111.7_amd64.deb 
 /var/cache/apt/archives/python-problem-report_1.0-0ubuntu5_all.deb 
 /var/cache/apt/archives/python-apport_1.0-0ubuntu5_all.deb 
 /var/cache/apt/archives/apport_1.0-0ubuntu5_all.deb 
 /var/cache/apt/archives/update-manager_1%3a0.111.7_all.deb 

**&#1057;hange link to python2.5 in /usr/bin and version in python_defaults not resolves this problem.**

Please help !!! :confused:

---

### Post by adisk on 2009-07-24
I have same trouble.

---

### Post by Soul-Sing on 2009-07-24
```
sudo rm /usr/bin/python && sudo ln -s python<your-version-number> /usr/bin/python
```

---

### Post by eudxm on 2010-08-09
I had the same problem... It worked!

---

### Post by josteinl on 2011-02-22
Got similar error and solution, but on:

Linux 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS

Running:

```
sudo apt-get upgrade

<... snip....>

Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1653, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6
dpkg: error processing /var/cache/apt/archives/python-imaging_1.1.7-1ubuntu0.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1477, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
<...snip...>
Processing triggers for software-center ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 2300, in <module>
    main()
  File "/usr/bin/pycentral", line 2294, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 1477, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 278, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 172, in default_version
    raise ValueError, "/usr/bin/python does not match the python default version. It must be reset to point to %s" % debian_default
ValueError: /usr/bin/python does not match the python default version. It must be reset to point to python2.6
dpkg: error processing software-center (--unpack):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/python-imaging_1.1.7-1ubuntu0.1_i386.deb
 software-center
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Looking at /usr/bin:

```
/usr/bin$ ls -la python*
lrwxrwxrwx 1 root root      24 2010-08-04 20:03 python -> /etc/alternatives/python
lrwxrwxrwx 1 root root       9 2010-06-04 09:33 python2 -> python2.6
lrwxrwxrwx 1 root root      31 2010-08-04 07:49 python2.5 -> /usr/local/python2.5/bin/python
-rwxr-xr-x 1 root root 2288240 2010-04-16 16:06 python2.6
-rwxr-xr-x 1 root root    1452 2010-04-16 15:59 python2.6-config
/usr/bin$

```Ran:

```
cd /usr/bin
sudo rm /usr/bin/python && sudo ln -s python2.6 /usr/bin/python

```Result:

```
/usr/bin$ ls -l python*
lrwxrwxrwx 1 root root       9 2011-02-22 09:50 python -> python2.6
lrwxrwxrwx 1 root root       9 2010-06-04 09:33 python2 -> python2.6
lrwxrwxrwx 1 root root      31 2010-08-04 07:49 python2.5 -> /usr/local/python2.5/bin/python
-rwxr-xr-x 1 root root 2288240 2010-04-16 16:06 python2.6
-rwxr-xr-x 1 root root    1452 2010-04-16 15:59 python2.6-config
/usr/bin$

```Then ran successfully:

```
sudo apt-get upgrade

```

---

