---
title: "Can't remove pkg or install new ones"
date: 2006-08-18
forum: Desktop Environments
---

### Post by nwgray on 2006-08-18
Good morning everyone,
   In my various install/remove fests, I installed the Suse rpm for Novell using alien. I then removed it using apt-get --install -remove. I'm sure that I have broken something because now I get this in Synaptic whenever I update or install anything  ](*,) :

E: novelclient: subprocess post-removal script returned error exit status 127

and this is in the terminal window for Synaptic:

Removing novel client ...
dpkg: Error processing novelclient ( --remove):
 sub-process post removal script returned error exit status 127
Errors were encountered while processing:
novelclient
E: sub-process /usr/bin/dpkg returned error code (1)
A package failed to install. Trying to recover:

After I close the terminal window, it shows my packages are still marked for installation. I have no idea how to fix this.

thought?

Thx

---

### Post by givré on 2006-08-18
```
sudo apt-get install -f
```
should solve the situation.
alian don't always work very well :cool:

---

### Post by nwgray on 2006-08-18
Thanks for the help. I tried that command and here's the result:

sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  novelclient
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 10.8MB disk space will be freed.
Do you want to continue [Y/n]? y
Could not exec dpkg!
E: Sub-process /usr/bin/dpkg returned an error code (100)


I think I'm gonna have to reinstall the file and try again but sourceforge is having issues right now. 

Any other thoughts? Where is this script getting referenced?

Thx

---

