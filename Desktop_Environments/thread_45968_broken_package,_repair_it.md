---
title: "broken package, repair it"
date: 2005-07-02
forum: Desktop Environments
---

### Post by kylenewton on 2005-07-02
Alright, I installed tuxracer before installing my nvidia drivers (GeForce 4 MX 440). It was slow, I quit the program. Looking around, I find files to manually install. I try, fail (I have a good idea how to do it now). So I go install nvidia drivers through kynaptic. I then 'repair' tuxracer 0.61-2 and the extras. It hung up.

Now I try to remove tuxracer and anything to do with it, and it's broken. I have to 'repair broken packages' and it never does.

Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 7292 package `tuxracer-extras':
 missing version

that's the error I get. And I can't install any packages, it seems, until I get this cleared up. How might I get around clearing this up?

I have the backports and multiverse/universe set up in my repositories, if it's useful for you to know.

---

### Post by Xian on 2005-07-02
Please post the output of the following command in a terminal:
```
$ sudo apt-get -f install
```

---

### Post by kylenewton on 2005-07-02
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  tuxracer-data
Recommended packages:
  tuxracer
The following NEW packages will be installed:
  tuxracer-data
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/7359kB of archives.
After unpacking 12.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/status' near line 7292 package `tuxracer-extras':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)


Thanks for the response, btw.

---

### Post by Xian on 2005-07-02
Let's hope your backup status file isn't corrupted.
That will make this an easy fix.

Open the status-old file (which is the backup to status) using the command below issued from a terminal, and then when it has been loaded in the text editor just save it as /var/lib/dpkg/status, which will then write over the present status file.
```
$ sudo gedit /var/lib/dpkg/status-old
```

---

### Post by kylenewton on 2005-07-02
Thanks!

After resaving, I ran

> sudo apt-get -f install

Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

So I'm assuming all is good. Thanks again.

---

### Post by paintedrealms on 2008-05-28
I got the following output:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gimp-help-common gimp-help-en
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up openoffice.org-writer2latex (0.5-6) ...
Adding extension /usr/lib/openoffice/share/extension/install/writer2latex.uno.pkg...
unopkg failed.
dpkg: error processing openoffice.org-writer2latex (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-writer2latex; however:
  Package openoffice.org-writer2latex is not configured yet.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org-writer2latex
 openoffice.org
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

