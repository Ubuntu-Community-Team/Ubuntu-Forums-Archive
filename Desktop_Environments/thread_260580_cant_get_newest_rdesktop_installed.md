---
title: "cant get newest rdesktop installed"
date: 2006-09-19
forum: Desktop Environments
---

### Post by kewlb on 2006-09-19
Hey All,

I want to use ubuntu as a complete desktop replacement; however I am unable to do this without the newest rdesktop client. I can not get it installed for the life of me.

It keeps telling me it can't find my openssl directory even though the package manager states that openssl is installed.

I read through a few posts I found on google and it seems that people there got it installed by installing libssl-dev.. however when I try to install libssl-dev it tells me that its missing zlib1g-dev which is not installable.

I have tried to get zlib1g-dev installed every which way but its just not working and I am just about fed up. 

error msgs:

The following packages have unmet dependencies:
  libssl-dev: Depends: zlib1g-dev but it is not installable
E: Broken packages
brian@brian-laptop:~/temp$

and trying an apt-get install zlib1g-dev

Package zlib1g-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package zlib1g-dev has no installation candidate
brian@brian-laptop:/$

any help would be appreciated.

---

### Post by kewlb on 2006-09-19
9 hours later.. 3 of them still fooling with this problem and still don't have it worked out :(

---

### Post by dmflad on 2006-09-20
In same spot. Am using rdesktop to reach WinXP PC okay but not Win2k server. Was hoping rdesktop 1.5 would cure "reset by peer" err msg but ./configure returns "can't find OpenSSL library directory". Came to forum before going out to Google. Tried the "--with-openssl" option but still no luck getting ./configure to go correctly.  Have not tried installing libssl-dev yet.

---

### Post by dmflad on 2006-09-20
Used synaptic gui and downloaded/installed libssl-dev and the zlib1g-dev came along too. Now ./configure works BUT now running make gives me huge number of  xwin.c error messages that numble about 'something not in a union or structure'.

---

### Post by brottman on 2006-10-05
Bump. I'm having this same issue.

---

### Post by mrinvader on 2007-04-03
I had same issue and installing libx11-dev and its dependencies fixed the issue. 

I'm on Ubuntu 6.1 edgy eft

   -MrInvader

---

