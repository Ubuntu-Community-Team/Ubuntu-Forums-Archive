---
title: "MSTTCOREFONTS fails to download"
date: 2005-10-13
forum: Desktop Environments
---

### Post by xyzzyman on 2005-10-13
It downloads the main package from the repositories, but then it fails to download the various .exe files from the sourceforge mirrors. Anyone had any success?

---

### Post by binarymelon on 2005-10-13
It's working for me.  Some of the sourceforge servers were giving some long waits, but everything installed ok.

---

### Post by Petrush on 2005-10-14
I have same problem.

```
HTTP request sent, awaiting response... 400 Bad Request
14:10:46 ERROR 400: Bad Request.

andale32.exe: No such file or directory

```

---

### Post by Petrush on 2005-10-14
Hmm.. I think this could be due to that i'm behind a proxy. I have set the Network proxy in gnome and synaptic, but is this exported to the msttcorefonts install script?

---

### Post by xyzzyman on 2005-10-14
I have no proxy and it's still doing it. I just wound up copying all my TTF files over from my windows installation and did the command to rebuild the font cache.

---

### Post by t2kburl on 2005-10-15
what is that command?

---

### Post by georgek on 2005-10-15
I just hit this problem too.  I **am** behind a proxy and the logs showed that was the problem.

I had already set proxy details for gnome, firefox and synaptic so I thought I'd better sort out the relevant environment variables - ```
http_proxy=http://proxy:port/
``` (similar for ftp & https).
Searching the forums and wiki pointed me to /etc/environment so I tried that first.  Result - user shell had environment variables set OK but a root shell ```
sudo su -
``` did not.  Synaptic still failed.

Next set them in /etc/bash.bashrc.  Result - both user and root shell had them set OK but synaptic still failed.  I also tried apt-get from the root shell to see if that would help as I was sure I had the correct environment.  Also failed.

Having seen someone mention wget somewhere, I then set them in /etc/wgetrc.  Result - downloaded and installed fine with synaptic.

FWIW I expect that I could have put them in /root/.wgetrc instead but I haven't actually tried that.

Hope this helps someone out.

---

### Post by xyzzyman on 2005-10-15
Thanks georgek, 

I turned off 'passive ftp' in that file and now it works.

---

### Post by Petrush on 2005-10-19
I think there must be some problem with the proxy things in msttcorefonts.

I did a dpkg -x of the msttcorefont deb package. If I execute the script from shell, same problem appears, however if I take the wget command that is issued and run it in a separate terminal with http_proxy environment variable set, it download it fine.

I have tried to set proxy in wgetrc too, but no success, seems like the script uses some passing parameter for proxy? (this is not my area.. :)

---

### Post by georgek on 2005-10-20
Interestingly enough, I've now built another box and I saw something which hadn't appeared before.  When I installed msttcorefonts from synaptic a debconf window popped up and asked me if I was behind a proxy.

I had already set up all the environment variables and /root/.wgetrc as I said earlier so I have no idea if this would have been able to do the download without any extra setup.

Without trying to go off topic, this box pops up debconf window every so often but I never saw a single one on my previous box.:???:

---

### Post by montun on 2006-03-09
thanks georgek

I youst added my http_proxy and ftp_proxy variables to $USER/.wgetrc and did
```
sudo apt-get dist-upgrade
```
To finish up the broken installation.

```
http_proxy=http://wwwproxy.corp.com:3128
ftp_proxy=http://wwwproxy.corp.com:3128

```

---

### Post by stryderjzw on 2006-03-28
I am having this problem, but I am not behind the proxy.  Please help.  Thanks.

---

### Post by frogg on 2006-07-02
I am also not behind a proxy and I have the same issue.

---

### Post by thebigfatgeek on 2006-07-02
I have had this problem since the previous version of Ubuntu. No proxy, broadband, all repositories checked (multiverse, beerofkids etc) and still cannot resolve the msttcorefonts from any of the sourceforge sites.

How about an explanation on setting up these fonts manually i.e from my Windows disk (as they do currentlty exist on that machine, and I can access it via SAMBA)?

---

### Post by svaucher on 2006-07-18
I had a proxy error as well. My install tried to use a proxy when I don't use one...

In /etc/wgetrc, I set

use_proxy = off

... that's it, that's all. 

I could probably have done it in $USER/.wgetrc

---

