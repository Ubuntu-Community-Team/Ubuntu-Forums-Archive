---
title: "Apt-get 404 Errors"
date: 2007-03-21
forum: Desktop Environments
---

### Post by jazee on 2007-03-21
I don't know what I did but for some reason I can no longer connect to any of the Repos with apt-get. When ever I run:

```
sudo apt-get update
```

I get nothing but 404 errors back.

```

Err http://us.archive.ubuntu.com edgy/main Packages
  404 Not Found
Err http://us.archive.ubuntu.com edgy/restricted Packages
  404 Not Found
Err http://us.archive.ubuntu.com edgy/main Sources
  404 Not Found
Err http://us.archive.ubuntu.com edgy/restricted Sources
  404 Not Found
Err http://us.archive.ubuntu.com edgy/universe Packages
  404 Not Found
Err http://us.archive.ubuntu.com edgy/universe Sources
  404 Not Found
Err http://us.archive.ubuntu.com edgy-updates/main Packages
  404 Not Found
Err http://us.archive.ubuntu.com edgy-updates/restricted Packages
  404 Not Found
Err http://us.archive.ubuntu.com edgy-updates/main Sources
  404 Not Found
Err http://us.archive.ubuntu.com edgy-updates/restricted Sources
  404 Not Found
Err http://us.archive.ubuntu.com edgy-backports/main Packages
  404 Not Found
Err http://us.archive.ubuntu.com edgy-backports/restricted Packages
  404 Not Found
Err http://us.archive.ubuntu.com edgy-backports/universe Packages
  404 Not Found
Err http://us.archive.ubuntu.com edgy-backports/multiverse Packages
  404 Not Found
Err http://us.archive.ubuntu.com edgy-backports/main Sources
  404 Not Found
Err http://us.archive.ubuntu.com edgy-backports/restricted Sources
  404 Not Found
Err http://us.archive.ubuntu.com edgy-backports/universe Sources
  404 Not Found
Err http://us.archive.ubuntu.com edgy-backports/multiverse Sources
  404 Not Found

```

Any Ideas as to what I may have done to get this error. I was in the progress of doing the Beryl install if that helps. At the point of doing the lupine's key add.
[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

---

### Post by digitzero on 2007-03-21
What does your /etc/apt/sources.list file look like?  Any changes?

---

### Post by roberthr on 2007-03-21
Something seems to be wrong with Ubuntu repositories. I can't update or install anything since today. It just stops when it comes to IP 91.189.89.8 or 91.189.89.6

---

### Post by digitzero on 2007-03-21
I just ran:

```

apt-get update
```

Without a problem:

Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources [3786B]    
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Sources [430B]   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release                               
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release [38.4kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages

---

### Post by roberthr on 2007-03-21
It's moving here but really slow. Package with size of 22 kb took about 5 minutes to download...

---

### Post by tomane on 2007-03-21
I also got the same 404 errors with pt.archive.ubuntu.com
Oddly, I can `aptitude update´, the problem comes when do thre actual upgrade, most packages return err404 :(

---

### Post by Metalmurphy on 2008-04-01
Sorry to bump this but I'm having the exact same problem. Tons of 404s from the pt.archive.ubuntu.com

Is there any way to change what archives it uses?

---

### Post by jqpretor on 2008-04-23
Hi all...

I recently installed Ubuntu 8.04 BETA from the alternative install CD and I had to manually set up a proxy pointing to our default gateway for the initial installation. After that the network was automatically detected by nm-applet and everything seemed to work fine, internet, network browsing, all that.... EXCEPT apt-get gave 404 errors. 

Clearing the contents of /etc/apt/apt.conf made apt-get work again...

Hope that helps someone.

---

