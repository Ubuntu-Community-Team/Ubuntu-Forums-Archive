---
title: "doc-base causing apt-get problems - won't configure"
date: 2009-04-16
forum: General Help
---

### Post by nmsmith on 2009-04-16
I am having problems with doc-base not configuring itself properly. For some reason I have doc-base 0.8.16ubuntu1, even though the apparent version for hardy is 0.8.7ubuntu1. This may be partly the cause.

This is flagging up errors whenever I try to use aptitude.

I get:

```
nick@cloanthus:~$ sudo dpkg --configure doc-base
Setting up doc-base (0.8.16ubuntu1) ...
Invalid argument: --install-changed
Usage:
     install-docs [options] -i,--install | -r,--remove | -c,--check file [ file ... ]

     install-docs [options] -I,--install-all | -R,--remove-all

     install-docs [options] -s,--status docid [ docid ... ]

     install-docs -h | --help

dpkg: error processing doc-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 doc-base
nick@cloanthus:~$
```

I don't know what the post-installation script is which uses the --install-changed switch, but similarly:

```
nick@cloanthus:~$ install-docs --install-changed
Invalid argument: --install-changed
Usage:
     install-docs [options] -i,--install | -r,--remove | -c,--check file [ file ... ]

     install-docs [options] -I,--install-all | -R,--remove-all

     install-docs [options] -s,--status docid [ docid ... ]

     install-docs -h | --help

nick@cloanthus:~$
```

This is odd because [this page]("http://packages.debian.org/changelogs/pool/main/d/doc-base/doc-base_0.9.1/changelog#versionversion0.8.12") suggests that the --install-changed command came in with the 8.12 version.

I should add that I have no idea which version of the file I *should* have, nor whether that is really the cause of my issue.

Can anyone help?

---

### Post by cariboo on 2009-04-16
I would suugest you use Synaptic to remove the broken package. Go to Edit-->Fix Broken Packages, then open a terminal and type:

```
sudo apt-get clean
```

to clear the archived packages, then just to make sure there are no extra dependencies hanging around in the same terminal type:

```
sudo apt-get autoremove
```

Then reinstall the package.

Jim

---

### Post by nmsmith on 2009-04-17
Thanks.

Synaptic ran the 'fix broken packages' command without complaint.

Then:

```
[COLOR="Red"]nick@cloanthus:~$ sudo apt-get clean[/COLOR]
[sudo] password for nick: 
[COLOR="Red"]nick@cloanthus:~$ sudo apt-get autoremove[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up doc-base (0.8.16ubuntu1) ...
Invalid argument: --install-changed
Usage:
     install-docs [options] -i,--install | -r,--remove | -c,--check file [ file ... ]

     install-docs [options] -I,--install-all | -R,--remove-all

     install-docs [options] -s,--status docid [ docid ... ]

     install-docs -h | --help

dpkg: error processing doc-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 doc-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
[COLOR="Red"]nick@cloanthus:~$ sudo aptitude reinstall doc-base[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Building tag database... Done      
The following packages will be REINSTALLED:
  doc-base 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up doc-base (0.8.16ubuntu1) ...
Invalid argument: --install-changed
Usage:
     install-docs [options] -i,--install | -r,--remove | -c,--check file [ file ... ]

     install-docs [options] -I,--install-all | -R,--remove-all

     install-docs [options] -s,--status docid [ docid ... ]

     install-docs -h | --help

dpkg: error processing doc-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 doc-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Building tag database... Done      
[COLOR="Red"]nick@cloanthus:~$[/COLOR]


```

I can't completely remove doc-base, as both synaptic and aptitude want to remove ubuntu-desktop too. Is it safe to try this, or will I be booted out of my X session?

Interestingly synaptic at least thought that the installed version of doc-base should be 0.8.16ubuntu1

Thanks again for the suggestions: it seemed promising at first.

---

