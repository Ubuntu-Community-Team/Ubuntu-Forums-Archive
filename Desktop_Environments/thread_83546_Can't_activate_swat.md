---
title: "Can't activate swat"
date: 2005-10-29
forum: Desktop Environments
---

### Post by matw on 2005-10-29
I've installed samba, and netkit-inetd, but swat still doesn't work. I get a connection refused alert when I try [http://localhost:901](http://localhost:901).

What's up?

---

### Post by HermanAB on 2005-10-29
Is swat running???

# ps -e | grep -e "swat"

Anyhoo, you'll quickly find that it is easier to manage samba by editing the smb.conf file manually.  Just remember to restart smb after changing the file.

See this:
[http://www.aerospacesoftware.com/samba-debug-howto.html](http://www.aerospacesoftware.com/samba-debug-howto.html)

Cheers,

Herman
[http://www.AerospaceSoftware.com/linuxhowtos.html](http://www.AerospaceSoftware.com/linuxhowtos.html)

---

### Post by matw on 2005-10-29
Thanks Herman.

I was mislead. Swat wasn't installed, even though the samba package description in synaptic says swat is part of the package. < grumble>

One must uncomment the 'universe' lines in /etc/apt/sources.list to install the swat package. Once intsalled, swat works fine.

---

### Post by dbott67 on 2005-10-29
I like to peruse the forums looking for questions that I might be able to answer, as well as just read other posts just to learn what some of the problems are and how they we resolved.

This is a perfect example of how to respond after getting some help --- a quick thank you, as well as what the problem was and how you fixed it. I wish more people took the time to post whether or not the proposed solution worked, as well as any additional steps they took to resolve it.

Thanks Mat & Herman! :)

---

### Post by Marcelo Ferreira da Costa on 2005-10-31
Hi guys,
I have installed the Samba and SWAT packages as you told here, but I do not now how to run SWAT as service. Can somebody help me?

---

### Post by jaa1180 on 2005-11-12
I had to install the inetd package...
netkit-inetd to be exact.
once I did that... then SWAT worked...

---

### Post by avc on 2005-11-23
Shouldn't inetd be a suggested package? dpkg --status swat doesn't show it to be, and only in the man page will it suggest using inetd for swat. Maybe there's another way of running swat I don't know of. I would think listing inetd as a suggest or even dependency would solve some newbie problems (at least mine :) ).

---

### Post by fonva on 2006-01-06
Thanks,

I had the same problem with SWAT, but once I installed netkit-inetd swat worked. The problem is that in every guide I read they didnt mentioned the netkit-inetd installation issue, they just mention swat, inetd and openssl.

---

