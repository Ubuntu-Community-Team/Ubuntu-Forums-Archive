---
title: "How to upgrade pidgin"
date: 2008-04-01
forum: Desktop Environments
---

### Post by johnswb on 2008-04-01
Hello all,

I'm having a problem where I am unable to add users to Pidgin.  I get the following error on each user - "Not on server list", not sure what server list it is talking about.  I've read on a few forum where people said they've seen the same thing running 2.2.1 and was able to fix it upgrading to 2.3.x or higher. 
 
 I've down loaded 2.4.1 from here [http://sourceforge.net/project/downloading.php?groupname=pidgin&filename=pidgin-2.4.1.tar.bz2&use_mirror=superb-west](http://sourceforge.net/project/downloading.php?groupname=pidgin&filename=pidgin-2.4.1.tar.bz2&use_mirror=superb-west)
 I get the following error running this one - ./install-sh: no input file specified
Still new to Linux so I'm not sure if I am missing something?

I've also gone to 
[http://www.getdeb.net/](http://www.getdeb.net/)
 I get the following - Error: Dependency is not satisfiable: pidgin-data

and still unable to upgrade from 2.2.1 and anyone else ran into this problem and found a fix?

---

### Post by aomlives on 2008-04-01
> **johnswb said:**
> 
 I get the following - Error: Dependency is not satisfiable: pidgin-data


This error means Pidgin depends on another package called pidgin-data. You can download this package here: 

[http://packages.ubuntu.com/gutsy/pidgin-data](http://packages.ubuntu.com/gutsy/pidgin-data)

If you are using another version of Ubuntu than 7.10, replace gutsy in the link with your version name.
Or just go to packages.ubuntu.com and search for pidgin-data with the correct options.

There are no other dependent packages associated with pidgin-data so after installing pidgin-data, you should be able to upgrade Pidgin succesfully.

Greetz

---

