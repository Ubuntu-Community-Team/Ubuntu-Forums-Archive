---
title: "OpenManage 7.1"
date: 2013-05-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dwpsco on 2013-05-09
I have Ubuntu Server 13.04 installed on (7) PowerEdge 1850s.
I am trying to install Dell's OpenManage 7.1.
I followed the instructions @ [http://linux.dell.com/repo/community/deb/latest/](http://linux.dell.com/repo/community/deb/latest/) and created a file ‘/etc/apt/sources.list.d/dell.sources.list’ that contains a single line:
"echo 'deb [http://linux.dell.com/repo/community/deb/latest](http://linux.dell.com/repo/community/deb/latest) /' | sudo tee -a /etc/apt/sources.list.d/linux.dell.com.sources.list"
When I run ‘sudo apt-get update’ I get the Error:
"E: Type 'echo' is not known on line 1 in source list /etc/apt/sources.list.d/dell.sources.list"
"E: The list of sources could not be read."
 
So I took out the 'echo' and got the Error:
"E: Type ''deb' is not known on line 1 in source list /etc/apt/sources.list.d/dell.sources.list"
"E: The list of sources could not be read."
SO tried… eh Skip, I tried many variations, all a bust.
Anyone able to help me with this?
I am new to Ubuntu so be gentle ;)

---

### Post by dwpsco on 2013-05-09
Oh and I tried "deb "[http://linux.dell.com/repo/community/deb/latest](http://linux.dell.com/repo/community/deb/latest) /" | sudo tee -a /etc/apt/sources.list.d/linux.dell.com.sources.list"
 
Then When I run &#8216;sudo apt-get update&#8217; I get:
Err [http://linux.dell.com](http://linux.dell.com) /'/| amd64 Packages
  404  Not Found
Err [http://linux.dell.com](http://linux.dell.com) /'/sudo amd64 Packages
  404  Not Found
Err [http://linux.dell.com](http://linux.dell.com) /'/tee amd64 Packages
  404  Not Found
Err [http://linux.dell.com](http://linux.dell.com) /'/-a amd64 Packages
  404  Not Found
Err [http://linux.dell.com](http://linux.dell.com) /'//etc/apt/sources.list.d/linux.dell.com.sources.list amd64 Packages
  404  Not Found
Err [http://linux.dell.com](http://linux.dell.com) /'/| i386 Packages
  404  Not Found
Err [http://linux.dell.com](http://linux.dell.com) /'/sudo i386 Packages
  404  Not Found
Err [http://linux.dell.com](http://linux.dell.com) /'/tee i386 Packages
  404  Not Found
Err [http://linux.dell.com](http://linux.dell.com) /'/-a i386 Packages
  404  Not Found
Err [http://linux.dell.com](http://linux.dell.com) /'//etc/apt/sources.list.d/linux.dell.com.sources.list i386 Packages
  404  Not Found
W: Failed to fetch [http://linux.dell.com/repo/community/deb/latest](http://linux.dell.com/repo/community/deb/latest) /dists/|/sudo/binary-amd64/Packages  404  Not Found
 
W: Failed to fetch [http://linux.dell.com/repo/community/deb/latest](http://linux.dell.com/repo/community/deb/latest) /dists/|/tee/binary-amd64/Packages  404  Not Found
 
W: Failed to fetch [http://linux.dell.com/repo/community/deb/latest](http://linux.dell.com/repo/community/deb/latest) /dists/|/-a/binary-amd64/Packages  404  Not Found
 
W: Failed to fetch [http://linux.dell.com/repo/community/deb/latest](http://linux.dell.com/repo/community/deb/latest) /dists/|//etc/apt/sources.list.d/linux.dell.com.sources.list/binary-amd64/Packages  404  Not Found
 
W: Failed to fetch [http://linux.dell.com/repo/community/deb/latest](http://linux.dell.com/repo/community/deb/latest) /dists/|/sudo/binary-i386/Packages  404  Not Found
 
W: Failed to fetch [http://linux.dell.com/repo/community/deb/latest](http://linux.dell.com/repo/community/deb/latest) /dists/|/tee/binary-i386/Packages  404  Not Found
 
W: Failed to fetch [http://linux.dell.com/repo/community/deb/latest](http://linux.dell.com/repo/community/deb/latest) /dists/|/-a/binary-i386/Packages  404  Not Found
 
W: Failed to fetch [http://linux.dell.com/repo/community/deb/latest](http://linux.dell.com/repo/community/deb/latest) /dists/|//etc/apt/sources.list.d/linux.dell.com.sources.list/binary-i386/Packages  404  Not Found

---

### Post by tgalati4 on 2013-05-09
These look like old instructions and may not work in 13.04.  You might have better luck with 12.04 since it is a Long Term Support (LTS) release.

The Dell repository is valid and the packages are there.

You should have a file called **linux.dell.com.sources.list** under /etc/apt/sources.list.d.

Inside that file you should have:  

```
deb http://linux.dell.com/repo/community/deb/latest /
```

---

### Post by dwpsco on 2013-05-09
Okay dude, seriously you ARE THE MAN! That 'linux.dell.sources.list' did NOT exist so I created it, added the line 'deb [http://linux.dell.com/repo/community/deb/latest](http://linux.dell.com/repo/community/deb/latest) /' and bingo presto it works. :D and as for the 12.04 vs 13.04 gee now you tell me! LOL I got 13.04 installed on 7 servers! Thanks again for your help, you are my HERO for the day.

---

### Post by tgalati4 on 2013-05-09
Servers tend to be upgraded on a slower pace because of the agony units involved in migrating services.  So if all of your services run OK on 13.04, then you should be OK.  Most services on [http://bitnami.org/stacks](http://bitnami.org/stacks) are built to 12.04 for one-click (well, almost) installation.  Most of these services won't be rebuilt until the next LTS, probably 14.04 in April 2014.

I have a couple of PE1750's.  I found the Dell OpenManage utilities to be really heavy CPU-wise, so I turned them off.  You might want to check how much overhead they consume.  Besides the fancy graphical interface, all you really need is uptime.  And that you can get by installing *rwho* and *rwhod* and using *ruptime*.  Install that on all of your servers and on a desktop and you can monitor the remote uptime of all of your servers with one command.

---

