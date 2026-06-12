---
title: "/usr/share/doc/kde/HTML/en/kubuntu/' is not a directory: No such file or directory"
date: 2009-07-30
forum: Desktop Environments
---

### Post by pmlxuser on 2009-07-30
did a kubuntu-desktop install, everything went fine only the installtion did not complete
it sput out some thing like

Setting up kubuntu-docs (9.04.2) ...                                           
ln: target `/usr/share/doc/kde/HTML/en/kubuntu/' is not a directory: No such file or directory                                                                  
dpkg: error processing kubuntu-docs (--configure):                              
 subprocess post-installation script returned error exit status 1   

tried to fix by runing            

sudo apt-get --reinstall install kubuntu-docs

but i got this

```

sudo apt-get --reinstall install kubuntu-docs
Reading package lists... Done                                            
Building dependency tree                                                 
Reading state information... Done                                        
The following packages were automatically installed and are no longer required:
  python-nautilus gnome-themes-ubuntu libgdict-1.0-6                           
Use 'apt-get autoremove' to remove them.                                       
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.  
1 not fully installed or removed.                                              
After this operation, 0B of additional disk space will be used.                
Do you want to continue [Y/n]? y                                               
Setting up kubuntu-docs (9.04.2) ...                                           
ln: target `/usr/share/doc/kde/HTML/en/kubuntu/' is not a directory: No such file or directory                                                                  
dpkg: error processing kubuntu-docs (--configure):                              
 subprocess post-installation script returned error exit status 1               
Errors were encountered while processing:                                       
 kubuntu-docs                                                                   
E: Sub-process /usr/bin/dpkg returned an error code (1) 

```

the problem now is that i have a system that is half way. the desktop has a tiny bit showing the plasma thingy and the rest is black.

help

---

### Post by majorhabib on 2009-08-09
I have the same problem except that KDE is working fine.

---

### Post by majorhabib on 2009-08-09
Ok, I have found a solution.

Download the patch 
[http://launchpadlibrarian.net/29922642/fix_kubuntu_docs.patch]("http://launchpadlibrarian.net/29922642/fix_kubuntu_docs.patch")

1) Run "sudo apt-get install kubuntu-desktop"
2) Apply the patch: download "fix_kubuntu_docs.patch" attached and run "sudo patch -p0 < fix_kubuntu_docs.patch"
3) Run "sudo apt-get install kubuntu-docs"

It worked for me.

---

### Post by oneguynick on 2009-08-10
> **majorhabib said:**
> Ok, I have found a solution.

Download the patch 
[http://launchpadlibrarian.net/29922642/fix_kubuntu_docs.patch]("http://launchpadlibrarian.net/29922642/fix_kubuntu_docs.patch")

1) Run "sudo apt-get install kubuntu-desktop"
2) Apply the patch: download "fix_kubuntu_docs.patch" attached and run "sudo patch -p0 < fix_kubuntu_docs.patch"
3) Run "sudo apt-get install kubuntu-docs"

It worked for me.

Just a "me too" post to say it worked. Thanks

---

### Post by Firefishe on 2009-08-23
> **majorhabib said:**
> Ok, I have found a solution.

Download the patch 
[http://launchpadlibrarian.net/29922642/fix_kubuntu_docs.patch]("http://launchpadlibrarian.net/29922642/fix_kubuntu_docs.patch")

1) Run "sudo apt-get install kubuntu-desktop"
2) Apply the patch: download "fix_kubuntu_docs.patch" attached and run "sudo patch -p0 < fix_kubuntu_docs.patch"
3) Run "sudo apt-get install kubuntu-docs"

It worked for me.

And it worked for the Firefishe, as well!  Thanks, majorhabib! :-)

Just a thought to let you know this patch worked great!  Considering this is on a friend's computer, this eliminates the problems a strange error for a linux newbie can cause.

Great Job!

Warm Regards,
Firefishe

---

### Post by jpmorelli on 2009-08-31
It worked for me too !!! Thanks !!! :)

---

### Post by varunmagical on 2009-08-31
Thanks!

---

### Post by gurth4ng on 2009-09-10
worked great, thx a lot!!

---

### Post by kellemes on 2009-09-17
Works fine indeed.

---

### Post by phicloray on 2009-09-24
Thanks :)

---

### Post by pixelot on 2010-01-05
Thanks, worked for me!

:guitar:

---

