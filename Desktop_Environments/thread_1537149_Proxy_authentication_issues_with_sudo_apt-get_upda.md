---
title: "Proxy authentication issues with sudo apt-get update"
date: 2010-07-23
forum: Desktop Environments
---

### Post by Deland01 on 2010-07-23
Can anyone help out with this, I'm having no luck at all using apt-get  update

I've just started using Linux / Ubuntu but here's what  I've done so far.


test@sh-vm-ubuntudesktop:~$ [COLOR=DarkSlateBlue]**sudo apt-get update**[/COLOR]
Ign  [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid Release.gpg                  
Ign  [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main  Translation-en_GB              
Ign  [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid/main  Translation-en_GB                     
Ign  [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted  Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/)  lucid/restricted Translation-en_GB
Ign  [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe  Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/)  lucid/universe Translation-en_GB
Ign  [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse  Translation-en_GB
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/)  lucid/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)  lucid-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com)  lucid-security Release
Ign [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/)  lucid-updates/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com)  lucid-security/main Packages          
Ign  [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/restricted  Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com)  lucid-security/restricted Packages
Ign  [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/universe  Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main  Sources                                 
Ign  [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse  Translation-en_GB        
Ign [http://security.ubuntu.com](http://security.ubuntu.com)  lucid-security/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)  lucid Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe  Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates Release
Ign  [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Ign  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Packages
Ign  [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Ign  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Packages
Ign  [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Ign  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Sources
Ign  [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Ign  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted Sources
Ign  [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Ign  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Packages
Ign  [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Ign  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Sources
Ign  [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Ign  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Packages
Ign  [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Ign  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Sources
Ign  [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Ign  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Packages
Ign  [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Ign  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Packages
Ign  [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Ign  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Sources
Err  [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
  407  Proxy  Authentication Required
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)  lucid-updates/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com)  lucid-security/restricted Packages
  407  Proxy Authentication  Required
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe  Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
   407  Proxy Authentication Required
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)  lucid-updates/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com)  lucid-security/restricted Sources
  407  Proxy Authentication  Required
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse  Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe  Packages
  407  Proxy Authentication Required
Ign  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Sources
Ign  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Packages
Err  [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
  407   Proxy Authentication Required
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)  lucid/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com)  lucid-security/multiverse Packages    
  407  Proxy Authentication  Required
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main  Sources                  
Err [http://security.ubuntu.com](http://security.ubuntu.com)  lucid-security/multiverse Sources     
  407  Proxy Authentication  Required
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/restricted  Sources            
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe  Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Sources
Ign  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Packages
Ign  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Sources
Ign  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Packages
Ign  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Packages
Ign  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Sources
Ign  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/restricted Sources
Ign  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Packages
Ign  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Sources
Ign  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Packages
Ign  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Sources
Err  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Packages
  407  Proxy  Authentication Required
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)  lucid/restricted Packages
  407  Proxy Authentication Required
Err  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/main Sources
  407  Proxy  Authentication Required
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)  lucid/restricted Sources
  407  Proxy Authentication Required
Err  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/universe Packages
  407  Proxy  Authentication Required
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)  lucid/universe Sources
  407  Proxy Authentication Required
Err  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid/multiverse Packages
  407  Proxy  Authentication Required
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)  lucid/multiverse Sources
  407  Proxy Authentication Required
Err  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Packages
  407  Proxy  Authentication Required
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)  lucid-updates/restricted Packages
  407  Proxy Authentication  Required
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/main Sources
   407  Proxy Authentication Required
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)  lucid-updates/restricted Sources
  407  Proxy Authentication Required
Err  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/universe Packages
  407   Proxy Authentication Required
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)  lucid-updates/universe Sources
  407  Proxy Authentication Required
Err  [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) lucid-updates/multiverse Packages
   407  Proxy Authentication Required
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)  lucid-updates/multiverse Sources
  407  Proxy Authentication Required
W:  Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz)   407  Proxy Authentication Required

W: Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz)   407  Proxy Authentication Required

W: Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz)   407  Proxy Authentication Required

W: Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz)   407  Proxy Authentication Required

W: Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz)   407  Proxy Authentication Required

W: Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz)   407  Proxy Authentication Required

W: Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz)   407  Proxy Authentication Required

W: Failed to fetch  [http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz)   407  Proxy Authentication Required

W: Failed to fetch  [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)   407  Proxy Authentication Required

W: Failed to fetch  [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)   407  Proxy Authentication Required

W: Failed to fetch  [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz)   407  Proxy Authentication Required

W: Failed to fetch  [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz)   407  Proxy Authentication Required

W: Failed to fetch  [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)   407  Proxy Authentication Required

W: Failed to fetch  [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz)   407  Proxy Authentication Required

W: Failed to fetch  [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)   407  Proxy Authentication Required

W: Failed to fetch  [http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz)   407  Proxy Authentication Required

W: Failed to fetch  [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)   407  Proxy Authentication Required

W: Failed to fetch  [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)   407  Proxy Authentication Required

W: Failed to fetch  [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz)   407  Proxy Authentication Required

W: Failed to fetch  [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)   407  Proxy Authentication Required

W: Failed to fetch  [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)   407  Proxy Authentication Required

W: Failed to fetch  [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz)   407  Proxy Authentication Required

W: Failed to fetch  [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)   407  Proxy Authentication Required

W: Failed to fetch  [http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz)   407  Proxy Authentication Required

E: Some index files failed to  download, they have been ignored, or old ones used instead.
test@sh-vm-ubuntudesktop:~$  

I then updated the global proxy file to allow authentication

[COLOR=DarkSlateBlue]**sudo nano /etc/apt/apt.conf**[/COLOR]

This  opens my http global proxy which looks like this

**ccm-ca** =  my domain
**domain-admin-pw-here** = my actual file has the  correct domain password which allows full access on the proxy server.
**192.168.2.58**  = this is the address of my proxy server

Acquire::http::proxy  "http://ccm-ca\administrator:domain-admin-pw-here@192.168.2.58:8080/";
Acquire::ftp::proxy  "ftp://ccm-ca\administrator:domain-admin-pw-here@192.168.2.58:8080/";
Acquire::https::proxy  "https://ccm-ca\administrator:domain-admin-pw-here@192.168.2.58:8080/";

I've  also tried the above file with no "ccm-ca\" on the user name

Im  still seeing  a "407 Proxy Authentication Required" error. We have a  smoothwall proxy server in place, to which I have allowed full access  out for my IP address.

Any suggestions what I'm doing wrong /  what I need to do next?

---

### Post by clrg on 2010-07-23
I don't see why this wouldn't work. Does the proxy authentication with this configuration work with other applications? Try Firefox, for example. Mine looks like this and works just fine:
(There's an SSH tunnel on 8080)

```
phirt@detox:~$ cat /etc/apt/apt.conf
Acquire::http::proxy "http://127.0.0.1:8080/";

```

---

### Post by Deland01 on 2010-07-23
I have Firefox set to use the global proxy settings, as soon as I open it, it prompts to to enter the uername & PW for the proxy authentication. I entered the same as what I had in the apt.conf file

---

### Post by clrg on 2010-07-23
That means the problem isn't apt, its either your proxy or your LDAP/Kerberos/AD. Does it work after you supply your authentication information to Firefox?

---

### Post by Deland01 on 2010-07-26
[COLOR=black][FONT=Verdana]Yeh, Firefox works fine after the proxy username & PW are entered. However if I have them saved in the apt.conf & tell Firefox to use the global settings it wont work, this is why I cant figure it out. I know its the proxy stopping the authentication but I’m trying to understand how Ubuntu passes the credentials onto it. This is the part which doesn’t appear to be happening.[/FONT][/COLOR]

---

### Post by clrg on 2010-07-26
Sniff the traffic. Wireshark or tcpdump are your friends :> I guess it uses normal HTTP unencrypted authentication? Or does your proxy require something else?

---

### Post by Deland01 on 2010-07-26
I'll give Wireshark a go, Ive used it before.

---

