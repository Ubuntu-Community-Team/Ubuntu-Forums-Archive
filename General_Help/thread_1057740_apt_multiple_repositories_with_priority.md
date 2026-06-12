---
title: "apt multiple repositories with priority?"
date: 2009-02-02
forum: General Help
---

### Post by Mouth on 2009-02-02
My ISP provides a mirror of ubuntu, which I can reconfigure my sources.list to use the ISP repository instead. Since this local ISP mirror is free (does not contribute to monthly download quota), I much prefer to use it.

But, this repository is only available inside the ISP network and IP range. Thus, if I am not connected to the internet from my home ISP connection, then 'apt-get update' attempts fail to connect to the repository.

Is it possible to have multiple repositories defined, with a priority assignment? Thus, if I am at home and apt can connect to my local ISP's repo mirror then it will use that, but if I am not at home and it cannot connect then it will fall-back to another repo?

Example ...

deb [ftp://ftp.netspace.net.au/pub/ubuntu/](ftp://ftp.netspace.net.au/pub/ubuntu/) intrepid main restricted 10
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) intrepid main restricted 20

Where the 10|20 at the end of each line denotes the usage priority. Thus use the 10 priority first (my ISP mirror) and if that fails then use the 20 priority line.

I search the forums and used google, but could find nothing. I did find references to apt priority for package versions, but this didn't seem teh same/appropriate to me.

Thanks.

---

### Post by Mouth on 2009-02-03
Bump. Nothing available at all to achieve this? If not, perhaps I should brainstorm it?

---

### Post by binbash on 2009-02-03
Read the second post : [https://www.linuxquestions.org/questions/debian-26/multiple-apt-repositories-269143/](https://www.linuxquestions.org/questions/debian-26/multiple-apt-repositories-269143/)

Or 

[http://linux.derkeiler.com/Mailing-Lists/Debian/2003-12/3765.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2003-12/3765.html)

but i didn't try it.It is a little old :)

---

### Post by Mouth on 2009-02-03
> **binbash said:**
> Read the second post : [https://www.linuxquestions.org/questions/debian-26/multiple-apt-repositories-269143/](https://www.linuxquestions.org/questions/debian-26/multiple-apt-repositories-269143/)

Or 

[http://linux.derkeiler.com/Mailing-Lists/Debian/2003-12/3765.html](http://linux.derkeiler.com/Mailing-Lists/Debian/2003-12/3765.html)

but i didn't try it.It is a little old :)


Thanks, but all of those only deal with pinning/prioritising repo's on the basis of package versions, and which version you want to keep/ignore. They don't deal/assist with multiple repo's where those repo's have the exact same packages and versions, and which repo you want to prioritise for downloading upgrades.

---

### Post by albinootje on 2009-02-03
> **Mouth said:**
> Thanks, but all of those only deal with pinning/prioritising repo's on the basis of package versions

I think the easiest solution for you is to use two different copies of /etc/apt/sources.list and use (copy) the correct one when needed.
You can even make some fancy shellscript which periodically looks up your ip-address and then copies the correct sources.list to /etc/apt/

---

### Post by jars99 on 2009-10-29
Please correct me if I'm wrong - but I believe you can have multiple repositories in your sources.list file, and then Ubuntu prioritizes them in a top down manner.  

For Example - I have a 100Mb uplink to my ISP, and a 10Mb uplink to everything else.  My ISP is an ubuntu mirror, so I have it first in the list, and the default ubuntu repository second, like this:

deb [ftp://mirrors.xmission.com/ubuntu/](ftp://mirrors.xmission.com/ubuntu/) jaunty main restricted universe multiverse
deb [ftp://mirrors.xmission.com/ubuntu/](ftp://mirrors.xmission.com/ubuntu/) jaunty-updates main restricted universe multiverse
deb [ftp://mirrors.xmission.com/ubuntu/](ftp://mirrors.xmission.com/ubuntu/) jaunty-security main restricted universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security main restricted universe multiverse

It seems to work for me

---

