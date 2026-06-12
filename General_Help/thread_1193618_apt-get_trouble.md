---
title: "apt-get trouble"
date: 2009-06-21
forum: General Help
---

### Post by Bearded-flower on 2009-06-21
Ok i am getting generally weird things when i try to install stuff it says unable to fetch...
and this is the results of when i tried to update.
edan@edan-laptop:~$ sudo apt-get update
```
Ign http://au.archive.ubuntu.com jaunty Release.gpg                           
Ign http://au.archive.ubuntu.com jaunty/main Translation-en_AU                
Ign http://au.archive.ubuntu.com jaunty/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com jaunty/universe Translation-en_AU
Ign http://au.archive.ubuntu.com jaunty/multiverse Translation-en_AU
Ign http://au.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://au.archive.ubuntu.com jaunty-updates/main Translation-en_AU
Ign http://au.archive.ubuntu.com jaunty-updates/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com jaunty-updates/universe Translation-en_AU
Ign http://au.archive.ubuntu.com jaunty-updates/multiverse Translation-en_AU
Ign http://au.archive.ubuntu.com jaunty-security Release.gpg
Ign http://au.archive.ubuntu.com jaunty-security/main Translation-en_AU
Hit http://archive.canonical.com jaunty Release.gpg
Ign http://archive.canonical.com jaunty/partner Translation-en_AU
Ign http://au.archive.ubuntu.com jaunty-security/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com jaunty-security/universe Translation-en_AU
Ign http://au.archive.ubuntu.com jaunty-security/multiverse Translation-en_AU
Ign http://au.archive.ubuntu.com jaunty Release
Ign http://au.archive.ubuntu.com jaunty-updates Release
Ign http://au.archive.ubuntu.com jaunty-security Release
Hit http://archive.canonical.com jaunty Release
Ign http://au.archive.ubuntu.com jaunty/main Packages
Ign http://au.archive.ubuntu.com jaunty/restricted Packages
Ign http://au.archive.ubuntu.com jaunty/main Sources
Ign http://au.archive.ubuntu.com jaunty/restricted Sources
Ign http://au.archive.ubuntu.com jaunty/universe Packages
Ign http://au.archive.ubuntu.com jaunty/universe Sources
Ign http://au.archive.ubuntu.com jaunty/multiverse Packages
Ign http://au.archive.ubuntu.com jaunty/multiverse Sources
Ign http://au.archive.ubuntu.com jaunty-updates/main Packages
Ign http://au.archive.ubuntu.com jaunty-updates/restricted Packages
Ign http://au.archive.ubuntu.com jaunty-updates/main Sources
Ign http://archive.canonical.com jaunty/partner Packages
Ign http://au.archive.ubuntu.com jaunty-updates/restricted Sources
Ign http://au.archive.ubuntu.com jaunty-updates/universe Packages
Ign http://au.archive.ubuntu.com jaunty-updates/universe Sources
Ign http://au.archive.ubuntu.com jaunty-updates/multiverse Packages
Ign http://au.archive.ubuntu.com jaunty-updates/multiverse Sources
Ign http://au.archive.ubuntu.com jaunty-security/main Packages
Ign http://au.archive.ubuntu.com jaunty-security/restricted Packages
Ign http://au.archive.ubuntu.com jaunty-security/main Sources
Ign http://au.archive.ubuntu.com jaunty-security/restricted Sources
Ign http://au.archive.ubuntu.com jaunty-security/universe Packages
Ign http://au.archive.ubuntu.com jaunty-security/universe Sources
Hit http://archive.canonical.com jaunty/partner Packages
Ign http://au.archive.ubuntu.com jaunty-security/multiverse Packages
Ign http://au.archive.ubuntu.com jaunty-security/multiverse Sources
Ign http://au.archive.ubuntu.com jaunty/main Packages
Ign http://au.archive.ubuntu.com jaunty/restricted Packages
Ign http://au.archive.ubuntu.com jaunty/main Sources
Ign http://au.archive.ubuntu.com jaunty/restricted Sources
Ign http://au.archive.ubuntu.com jaunty/universe Packages
Ign http://au.archive.ubuntu.com jaunty/universe Sources
Ign http://au.archive.ubuntu.com jaunty/multiverse Packages
Ign http://au.archive.ubuntu.com jaunty/multiverse Sources
Ign http://au.archive.ubuntu.com jaunty-updates/main Packages
Ign http://au.archive.ubuntu.com jaunty-updates/restricted Packages
Ign http://au.archive.ubuntu.com jaunty-updates/main Sources
Ign http://au.archive.ubuntu.com jaunty-updates/restricted Sources
Ign http://au.archive.ubuntu.com jaunty-updates/universe Packages
Ign http://au.archive.ubuntu.com jaunty-updates/universe Sources
Ign http://au.archive.ubuntu.com jaunty-updates/multiverse Packages
Ign http://au.archive.ubuntu.com jaunty-updates/multiverse Sources
Ign http://au.archive.ubuntu.com jaunty-security/main Packages
Ign http://au.archive.ubuntu.com jaunty-security/restricted Packages
Ign http://au.archive.ubuntu.com jaunty-security/main Sources
Ign http://au.archive.ubuntu.com jaunty-security/restricted Sources
Ign http://au.archive.ubuntu.com jaunty-security/universe Packages
Ign http://au.archive.ubuntu.com jaunty-security/universe Sources
Ign http://au.archive.ubuntu.com jaunty-security/multiverse Packages
Ign http://au.archive.ubuntu.com jaunty-security/multiverse Sources
Err http://au.archive.ubuntu.com jaunty/main Packages
  404 Not Found
Err http://au.archive.ubuntu.com jaunty/restricted Packages
  404 Not Found
Err http://au.archive.ubuntu.com jaunty/main Sources
  404 Not Found
Err http://au.archive.ubuntu.com jaunty/restricted Sources
  404 Not Found
Err http://au.archive.ubuntu.com jaunty/universe Packages
  404 Not Found
Err http://au.archive.ubuntu.com jaunty/universe Sources
  404 Not Found
Err http://au.archive.ubuntu.com jaunty/multiverse Packages
  404 Not Found
Err http://au.archive.ubuntu.com jaunty/multiverse Sources
  404 Not Found
Err http://au.archive.ubuntu.com jaunty-updates/main Packages
  404 Not Found
Err http://au.archive.ubuntu.com jaunty-updates/restricted Packages
  404 Not Found
Err http://au.archive.ubuntu.com jaunty-updates/main Sources
  404 Not Found
Err http://au.archive.ubuntu.com jaunty-updates/restricted Sources
  404 Not Found
Err http://au.archive.ubuntu.com jaunty-updates/universe Packages
  404 Not Found
Err http://au.archive.ubuntu.com jaunty-updates/universe Sources
  404 Not Found
Err http://au.archive.ubuntu.com jaunty-updates/multiverse Packages
  404 Not Found
Err http://au.archive.ubuntu.com jaunty-updates/multiverse Sources
  404 Not Found
Err http://au.archive.ubuntu.com jaunty-security/main Packages
  404 Not Found
Err http://au.archive.ubuntu.com jaunty-security/restricted Packages
  404 Not Found
Err http://au.archive.ubuntu.com jaunty-security/main Sources
  404 Not Found
Err http://au.archive.ubuntu.com jaunty-security/restricted Sources
  404 Not Found
Err http://au.archive.ubuntu.com jaunty-security/universe Packages
  404 Not Found
Err http://au.archive.ubuntu.com jaunty-security/universe Sources
  404 Not Found
Err http://au.archive.ubuntu.com jaunty-security/multiverse Packages
  404 Not Found
Err http://au.archive.ubuntu.com jaunty-security/multiverse Sources
  404 Not Found
W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-i386/Packages  404 Not Found

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-i386/Packages  404 Not Found

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources  404 Not Found

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources  404 Not Found

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages  404 Not Found

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources  404 Not Found

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages  404 Not Found

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources  404 Not Found

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-i386/Packages  404 Not Found

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages  404 Not Found

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources  404 Not Found

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources  404 Not Found

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages  404 Not Found

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources  404 Not Found

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages  404 Not Found

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources  404 Not Found

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-i386/Packages  404 Not Found

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-i386/Packages  404 Not Found

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources  404 Not Found

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources  404 Not Found

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-i386/Packages  404 Not Found

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources  404 Not Found

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-i386/Packages  404 Not Found

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
edan@edan-laptop:~$
```

---

### Post by SuperSonic4 on 2009-06-21
Perhaps the sites are just down at that moment in time?

---

### Post by RobOrr on 2009-06-21
a quick way to test if the servers are down is to change which server you get your updates from. If I recall correctly, au. is australia, so go to Software Sources (System > Administration) and change the server in the "Download From..." section.

I don't know if this will solve your problem, but it will certainly help narrow down whether it's a server-side problem or not.

---

### Post by Bearded-flower on 2009-06-21
Right ok, ill try that when i go home.
I DONT WANNA BE AT SCHOOL!!!

---

### Post by Bearded-flower on 2009-06-22
Yeah i think it was the servers.
its fine now
thanks

---

### Post by wubbzy on 2009-10-07
> **RobOrr said:**
> a quick way to test if the servers are down is to change which server you get your updates from. If I recall correctly, au. is australia, so go to Software Sources (System > Administration) and change the server in the "Download From..." section.

I don't know if this will solve your problem, but it will certainly help narrow down whether it's a server-side problem or not.

Rob,

I'm having the same problem right now. Is there a way to change the software server through the command line interface? I don't have access to the Ubuntu GUI. Oh wait, I see you can just edit /etc/apt/sources.list.

I just commented out these two lines

#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

and I'm getting past the 404 Not Found errors. 

Thanks.

-W

---

### Post by MelDJ on 2009-10-07
> **wubbzy said:**
> Rob,

I'm having the same problem right now. Is there a way to change the software server through the command line interface? I don't have access to the Ubuntu GUI. Oh wait, I see you can just edit /etc/apt/sources.list.

I just commented out these two lines

#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

and I'm getting past the 404 Not Found errors. 

Thanks.

-W

you are using an outdated ubuntu version. Gutsy is no longer supported. therefore you get the 404 error

---

### Post by wubbzy on 2009-10-07
> **MelDJ said:**
> you are using an outdated ubuntu version. Gutsy is no longer supported. therefore you get the 404 error

Thanks. I'm in a situation where, although I have some admin privileges, I'm not allowed to upgrade the Ubuntu on my server to a more recent version. Could I just update my sources.list file to a more recent one? If so, where could I find a more recent version of the sources.list file? 

Thanks.

---

### Post by unutbu on 2009-10-07
See [http://ubuntuforums.org/showpost.php?p=7167277&postcount=2](http://ubuntuforums.org/showpost.php?p=7167277&postcount=2)

---

