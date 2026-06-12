---
title: "apt-get install unsuccessful [7.04]"
date: 2008-12-19
forum: General Help
---

### Post by -RooneY- on 2008-12-19
Hi,

I am on Ubuntu 7.04.

I have been trying to install softwares through the repository. I tried a number of different Applications but I am getting exceedingly high no. of failed attempts. 

Most common errors are :
"Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz](http://in.archive.ubuntu.com/ubuntu/dists/feisty/universe/source/Sources.gz)  404 Not Found"

The url shown in this error doesn't even exist in terms of folder hiearchy.
I am also getting similar errors if I am trying to install packages through 
Synaptic.

Is it because I am on an older version ?

I also tried "sudo apt-get update" but got the same error there as well.

ANy help would be deeply appreciated,

Regards
Rooney

---

### Post by bluefrog on 2008-12-19
can you browse the internet with your linux computer?

change your repositories to main server in synaptic or vi command line if you prefer (get rid of in. )

---

### Post by plucky on 2008-12-19
> I am on Ubuntu 7.04.



Feisty 7.04 reached it end of life in October this year and so the normal  repos are closed and there will be no further updates.

You can change your sources.list to point to [http://old-releases.ubuntu.com](http://old-releases.ubuntu.com) or install a current version.


Good Luck

---

