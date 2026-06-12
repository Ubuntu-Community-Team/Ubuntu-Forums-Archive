---
title: "Installing tetex or tetex-live"
date: 2007-08-16
forum: Desktop Environments
---

### Post by elahrairah on 2007-08-16
Has anyone successfully installed teTex (or something equivalent) on Feisty?

 I am trying to install teTex or teTex live, but I get the same error with either.  

I installed the packages:

```
 
#sudo apt-get install tetex-base
#sudo apt-get install tetex-bin
#sudo apt-get install tetex-extra

```

On the last, I get errors:

```

Creating missing formats.
Running fmtutil-sys. This may take some time... tcfmgr: config file `tcfmgr.map' (usually in $TEXMFMAIN/texconfig) not found.
fmtutil: config file `fmtutil.cnf' not found.

fmtutil-sys failed. Output has been stored in:
  /tmp/tetex.format_creation.Nri14346/fmtutil-sys.log
Please include this file if you report a bug.
dpkg: error processing tetex-extra (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 tetex-extra
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

well, I do not know why it can't find this file, (tcfmgr.map) since:
```

# ls $TEXMFMAIN/texconfig
g  generic  README  tcfmgr  tcfmgr.map  v  x

```

If I try to run pdftex I get the same error about not being able to fine tcfmgr.map.

I see this error a lot with googling, but no real solutions. Anyone get teTex installed sucessfully?

Thanks!
Megan

---

### Post by mannheim on 2007-08-17
Sorry, this is isn't much help, but I tried installing tetex on a fresh install of feisty and did not have the problem you had. I just did "sudo apt-get install tetex-base tetex-bin" and then I installed tetex-extra like this:

```
user@vmware-linux:~$ sudo apt-get install tetex-extra
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Recommended packages:
  latex-beamer latex-xcolor lmodern pgf preview-latex-style texinfo
The following NEW packages will be installed:
  tetex-extra
0 upgraded, 1 newly installed, 0 to remove and 50 not upgraded.
Need to get 10.8MB of archives.
After unpacking 43.4MB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com feisty/main tetex-extra 3.0.dfsg.3-4 [10.8MB]
Fetched 10.8MB in 2s (4195kB/s)       
Selecting previously deselected package tetex-extra.
(Reading database ... 102470 files and directories currently installed.)
Unpacking tetex-extra (from .../tetex-extra_3.0.dfsg.3-4_all.deb) ...
Setting up tetex-extra (3.0.dfsg.3-4) ...
Removing unchanged obsolete conffiles ... done
no
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFMAIN... 
mktexlsr: Updating /var/lib/texmf/ls-R-TEXMFDIST-TETEX... 
mktexlsr: Updating /var/lib/texmf/ls-R... 
mktexlsr: Done.
Creating missing formats.
Running fmtutil-sys. This may take some time... done.
Running updmap-sys. This may take some time... done.


user@vmware-linux:~$

```

My only thought is: in your description of what you did, you give "#" as the command prompt, which sometimes suggests you were running as root (in addition to using sudo). Maybe that's not what you meant. Anyway, some of the tetex scripts are a bit fussy about who runs them, and maybe there's a bug whereby using sudo in addition to being root caused a problem.

---

