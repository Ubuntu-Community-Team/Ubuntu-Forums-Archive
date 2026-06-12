---
title: "[SOLVED] Help! apt-get is stuck!"
date: 2009-01-05
forum: General Help
---

### Post by Kissell on 2009-01-05
Anytime I use "apt-get" I get these errors about "1 not fully installed or removed".

I can still use "apt-get" to install and uninstall stuff, but this is getting annoying, so I thought I'd ask...  

How do I get these errors to clear up and go away without reinstalling the OS?

I try the -f force option, but it won't force it to go away by forcing remove or install.


> 
user@server:~/# sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up deluge-torrent (1.0.7-0ubuntu3~hardy1) ...
/usr/sbin/update-python-modules:125: DeprecationWarning: raising a string exception is deprecated
  raise "Trying to overwrite %s which is already provided by %s"%(os.path.join(dir,file),otherdir)
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 340, in <module>
    process_extensions(basedir,install_modules)
  File "/usr/sbin/update-python-modules", line 173, in process_extensions
    process(verdir,func([vers]))
  File "/usr/sbin/update-python-modules", line 160, in process
    func(basedir, dir, file)
  File "/usr/sbin/update-python-modules", line 125, in install_modules_func
    raise "Trying to overwrite %s which is already provided by %s"%(os.path.join(dir,file),otherdir)
Trying to overwrite deluge/plugins/flexRSS-0.1.egg which is already provided by /usr/share/python-support/deluge-torrent
dpkg: error processing deluge-torrent (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 deluge-torrent
E: Sub-process /usr/bin/dpkg returned an error code (1)



---

### Post by x22 on 2009-01-05
two ideas:
1. "apt-get -f install" where "-f" means "fix missing" see the apt-get manpage
2. "dpkg --remove <offending package>" followed by reinstallation if you want it

---

### Post by Kissell on 2009-01-05
"apt-get install -f" does not work.
> apt-get install -f

but "dpkg --remove deluge-torrent" works great!
> dpkg --remove deluge-torrent

However, everytime I reinstall deluge-torrent I get into the same mess I was in, even if I use an older or newer .deb that is in the repository.

hmm...  I HAVE to have deluge-torrent...  so I guess that means I have to live with this minor annoyance.  It's just that everytime I use apt-get it appears there is an error with what I was trying to install... and it freaks me out until I remember apt-get complains about deluge-torrent... 

But other than this text messages when using apt-get, everything works fine...  so I guess its not really a "problem".

---

### Post by code_u11 on 2009-01-05
could you post the output of these commands?```
sudo apt-get check
sudo apt-get purge deluge-torrent
sudo rm /var/cache/apt/archives/deluge-torrent*.deb
sudo apt-get install deluge-torrent
```

---

### Post by Kissell on 2009-01-05
No luck, after doing those four commands I'm back to where I was before doing them.  

sudo apt-get check
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done


sudo apt-get purge deluge-torrent
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboost-thread1.34.1 libboost-date-time1.34.1 libboost-iostreams1.34.1 python-setuptools python-pkg-resources
  libboost-filesystem1.34.1 libboost-python1.34.1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  deluge-torrent*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 13.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 165299 files and directories currently installed.)
Removing deluge-torrent ...
Purging configuration files for deluge-torrent ...
dpkg - warning: while removing deluge-torrent, directory `/usr/lib/python-support/deluge-torrent/python2.5/deluge' not empty so not removed.
dpkg - warning: while removing deluge-torrent, directory `/usr/lib/python-support/deluge-torrent/python2.5' not empty so not removed.
dpkg - warning: while removing deluge-torrent, directory `/usr/lib/python-support/deluge-torrent' not empty so not removed.
dpkg - warning: while removing deluge-torrent, directory `/usr/share/python-support/deluge-torrent/deluge/plugins' not empty so not removed.
dpkg - warning: while removing deluge-torrent, directory `/usr/share/python-support/deluge-torrent/deluge' not empty so not removed.
dpkg - warning: while removing deluge-torrent, directory `/usr/share/python-support/deluge-torrent' not empty so not removed.


sudo rm /var/cache/apt/archives/deluge-torrent*.deb
> user@server:~$  

sudo apt-get install deluge-torrent
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  deluge-torrent-common python-json
The following NEW packages will be installed:
  deluge-torrent deluge-torrent-common python-json
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 3247kB/3258kB of archives.
After this operation, 12.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  deluge-torrent-common deluge-torrent
Install these packages without verification [y/N]? y
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main deluge-torrent-common 1.0.7-0ubuntu3~hardy1 [126kB]
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main deluge-torrent 1.0.7-0ubuntu3~hardy1 [3121kB]
Fetched 3247kB in 4s (666kB/s)           
Selecting previously deselected package deluge-torrent-common.
(Reading database ... 164430 files and directories currently installed.)
Unpacking deluge-torrent-common (from .../deluge-torrent-common_1.0.7-0ubuntu3~hardy1_all.deb) ...
Selecting previously deselected package python-json.
Unpacking python-json (from .../python-json_3.4-2_all.deb) ...
Selecting previously deselected package deluge-torrent.
Unpacking deluge-torrent (from .../deluge-torrent_1.0.7-0ubuntu3~hardy1_i386.deb) ...
Setting up deluge-torrent-common (1.0.7-0ubuntu3~hardy1) ...

Setting up python-json (3.4-2) ...

Setting up deluge-torrent (1.0.7-0ubuntu3~hardy1) ...
/usr/sbin/update-python-modules:125: DeprecationWarning: raising a string exception is deprecated
  raise "Trying to overwrite %s which is already provided by %s"%(os.path.join(dir,file),otherdir)
Traceback (most recent call last):
  File "/usr/sbin/update-python-modules", line 340, in <module>
    process_extensions(basedir,install_modules)
  File "/usr/sbin/update-python-modules", line 173, in process_extensions
    process(verdir,func([vers]))
  File "/usr/sbin/update-python-modules", line 160, in process
    func(basedir, dir, file)
  File "/usr/sbin/update-python-modules", line 125, in install_modules_func
    raise "Trying to overwrite %s which is already provided by %s"%(os.path.join(dir,file),otherdir)
Trying to overwrite deluge/plugins/flexRSS-0.1.egg which is already provided by /usr/share/python-support/deluge-torrent
dpkg: error processing deluge-torrent (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 deluge-torrent
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by Kissell on 2009-01-05
Ah, this worked...  after uninstall deluge and doing your "rm" command I added this "rm" command, since it was complaining about this path...  

> sudo rm -R /usr/lib/python-support/deluge-torrent

now it's clean and I've been able to cleanly reinstall it...  

not sure why it was hung up on files in that folder...  I was running it with sudo, so it should have been able to get the rights necessary to make any changes it needed.

---

