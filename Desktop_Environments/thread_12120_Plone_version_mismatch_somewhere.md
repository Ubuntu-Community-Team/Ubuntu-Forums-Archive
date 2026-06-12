---
title: "Plone version mismatch somewhere"
date: 2005-01-22
forum: Desktop Environments
---

### Post by Alessio on 2005-01-22
I have installed plone form apt-get! But I have this error:
[http://plone.org/documentation/error/typeerror-exactly-n-arguments](http://plone.org/documentation/error/typeerror-exactly-n-arguments)
when I add news ..
in the plone documentation I read:
------
This means that you have a version mismatch somewhere - either running Plone 2.0 on CMF 1.5 or Plone 1 on CMF 1.4 or something else entirely.

Check all your package/product versions, and make sure it is a valid combination. The Plone Core tarball always ships with the correct dependencies, use that as reference if you are not certain which version combinations are valid.
------
Is the problem in the packages???
I'm in warty
Bye

---

### Post by Alessio on 2005-01-22
This post:
[http://ubuntuforums.org/showthread.php?t=10556&highlight=plone](http://ubuntuforums.org/showthread.php?t=10556&highlight=plone)
detect the same problem! :confused:

---

### Post by Alessio on 2005-01-22
Apt-get install:
zope 2.6.4-1.1
plone 1.0.5.20030909-3.1

---

### Post by Alessio on 2005-01-24
[QUOTE=Alessio]Apt-get install:
zope 2.6.4-1.1
plone 1.0.5.20030909-3.1[/QUOTE]
 Is it possible? Anyone?

---

### Post by steffen on 2005-01-27
I have had the exact same problem, numerous times. I have tried both Hoary and Warty.

Don't know if this will help you, but I just kept on apt-get install plone, until all files are downloaded. In the end, it actually managed to get everything, and I finally have a working Plone/Zope installation.

---

### Post by steffen on 2005-02-01
Have you actually managed to run Plone/Zope in Ubuntu?

First I had trouble installing it under Warty. Then I tried with Hoary. I have now been able to install it, but I can't find any scripts for starting zope --> not any zope* file in /etc and none in any /bin directory. There are loads of zope files elsewhere on the computer, but none that let's me start zope/plone. The only place that contains zope is /usr/lib/. I thought there should be a zopectl somewhere. I didn't get any errors when I installed it.

If I try to go to [http://localhost:8080/manage](http://localhost:8080/manage), I don't get anything (except that I am not allowed to access)

---

### Post by benshead on 2005-02-03
Have you tried installing it from source? I found the directions at [http://plone.org/documentation/howto/setup-from-source](http://plone.org/documentation/howto/setup-from-source) to be very helpful, even for a Linux newbie like me. It took less than an hour to get a Plone site up and running this morning.

If it would help, I'd be happy to post more about what I did...

---

### Post by steffen on 2005-02-03
I have thought about that - just installing from source. I haven't been able to get the apt-repositories working, even though I've been able to get all dependancies through the debian unstable repositories, etc.

Did you do anything else than following the instructions on Plone.org? Any Ubuntu specific issues?

---

