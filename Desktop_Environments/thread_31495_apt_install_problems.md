---
title: "apt install problems"
date: 2005-05-03
forum: Desktop Environments
---

### Post by mdm4301 on 2005-05-03
For over a week now I can not install anything through apt and I did not change anything that I can think of.  Here is the error that I am getting:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe php4-pear-log 1.6.0-1
  Could not resolve â8080â
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe horde2 2.2.7-7
  Could not resolve â8080â
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/p/php4-pear-log/php4-pear-log_1.6.0-1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/p/php4-pear-log/php4-pear-log_1.6.0-1_all.deb)  Could not resolve â8080â
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/h/horde2/horde2_2.2.7-7_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/h/horde2/horde2_2.2.7-7_all.deb)  Could not resolve â8080â

This is the error I get when I click on reload in synaptic:

[http://us.archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg:) Could not resolve ‘8080’
[http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/Release.gpg:) Could not resolve ‘8080’
[http://security.ubuntu.com/ubuntu/dists/hoary-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/hoary-security/Release.gpg:) Could not resolve ‘8080’
[http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz:) Could not resolve ‘8080’
[http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/binary-i386/Packages.gz:) Could not resolve ‘8080’
[http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz:) Could not resolve ‘8080’
[http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/source/Sources.gz:) Could not resolve ‘8080’
[http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz:) Could not resolve ‘8080’
[http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz:) Could not resolve ‘8080’
[http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz:) Could not resolve ‘8080’
[http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/source/Sources.gz:) Could not resolve ‘8080’
[http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz:) Could not resolve ‘8080’
[http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/source/Sources.gz:) Could not resolve ‘8080’
[http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz:) Could not resolve ‘8080’
[http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz:) Could not resolve ‘8080’
[http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz:) Could not resolve ‘8080’
[http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz:) Could not resolve ‘8080’

My first thought was that something is wrong with their server.  However after a week of this I thought it could be something else.  I am very new to linux and ubuntu and not sure what to do.
Any ideas?

---

### Post by mdm4301 on 2005-05-03
So this afternoon I tried it again without changing anything and it worked this time.  Is it possible the servers have been down for a long time?  Is there only a certain time interval when we are supposed to install packages?

---

### Post by mdm4301 on 2005-05-03
Apparently it only worked for about 5 minutes because when I tried it again a little later I was back to getting the same error message.  Is anyone else having this problem?

---

### Post by Takis on 2005-05-03
[QUOTE=mdm4301]Apparently it only worked for about 5 minutes because when I tried it again a little later I was back to getting the same error message.  Is anyone else having this problem?[/QUOTE]

Are you using a proxy? From the looks of things, it's trying to find the proxy server named '8080' (rather than port 8080).

Can you run this command:
```
$echo $HTTP_PROXY $HTTPS_PROXY $FTP_PROXY
```

Admittedly we probably only need the first, but the others may be incorrectly set as well.

---

### Post by mdm4301 on 2005-05-04
Thanks alot for the help takis.  I was using a zshrc file someone else had created and did not realize I still had their proxies being set.  Once I removed those values the problem was fixed.

---

