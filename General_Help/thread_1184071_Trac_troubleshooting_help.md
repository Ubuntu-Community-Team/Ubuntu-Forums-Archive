---
title: "Trac troubleshooting help"
date: 2009-06-10
forum: General Help
---

### Post by jon.mithe on 2009-06-10
Hi,

I have a home setup with Apache, Trac and SVN.  I recently upgraded to 9.04 (from 8.10) and my Trac seems to of been canned in the process :/  I'm a bit stuck so wandering if anyone can help! :P 

The problem in a little more detail... I try and access my trac page through firfox via the localhost / apache and I get an Internal server error, random gumph and at the end:

```
Apache/2.2.11 (Ubuntu) DAV/2 SVN/1.5.4 PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch mod_python/3.3.1 Python/2.6.2
```

From what I have been reading, this might of been caused by the upgrade installing python 2.6.x and I'm not 100% on this, but I believe trac is installed in python 2.5 so its just not finding things, this folder exists:

```
/usr/lib/python2.5/site-packages/Trac-0.11b1-py2.5.egg/
```

and I have a python2.6 directory, but with no site-packages in.

So I'm thinking I need to install the latest version into the python 2.6 there and delete the older 2.5 version? (would that just be deleting that trac folder?)

I'm trying being carful to not loose my trac environments / projects. I noticed a folder 

```
/var/trac
```

I'm guessing thats that folder containing all my projects (seems to have directories for projects, with a database file in it).  Probably would be worth backing that up... :P

So, I'm guessing I just need to delete that trac folder in the python2.5 dir and install the latest trac into python2.6 somehow?

I checked my /etc/apache2/sites-enabled$ and theres nothing point to the track, so I persume its just picking up the latest version of python.  Also points to the var/trac dir so guessing installing the new version and everything should work.

My svn works fine which is good :)

Any help/thoughts/confirmation of this would be a great help thanks

Cheers, 
Jon

---

### Post by jon.mithe on 2009-09-08
hmm oddly duplicated, found the problem / solution here: 

[http://ubuntuforums.org/showthread.php?t=1184079](http://ubuntuforums.org/showthread.php?t=1184079)

---

