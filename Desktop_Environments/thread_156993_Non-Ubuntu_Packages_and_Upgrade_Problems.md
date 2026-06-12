---
title: "Non-Ubuntu Packages and Upgrade Problems"
date: 2006-04-08
forum: Desktop Environments
---

### Post by larry on 2006-04-08
Dear All,
I installed on my system some packages which either are not included at all in the Ubuntu repositories or are there but I need a more up-to-date version.
Do not think about exotic weird stuff: I mainly use scientific software for numerical computations or financial stuff (e.g. Quantlib and Blitz++ libraries, some R-cran packages etc...).
All these packages are used by many scientists around the world, are well tested and absolutely harmless for your system.
In most of the cases I built them from source after downloading them from CVS.
I have been using these packages for weeks if not months without any problems.
However, when I tried to upgrade from Warty to Hoary, from Hoary to Breezy and  now to Dapper, the dist-upgrade process always broke down because of one of these totally "in order" packages (this time I had a problem with the QuantLib library).
Now, how comes? Is there some better way to update your distro apart from the usual update of the repository and the bare dist-upgrade command?
This time I am really annoyed; Ubuntu is great but this is pissing me out.
I am sorry I did not wrote down the exact error signalled by the system, but after my laptop went unbootable, I was not in the mood to file a bug report!
Many thanks

Larry

---

### Post by localzuk on 2006-04-08
If you use custom built software, you cannot expect it not to break when you upgrade the version of your OS. You would need to recompile your software really as the libraries that Ubuntu uses are being updated to newer versions and therefore have different functionality.

Also, dapper is currently still at the testing stage, so you should expect things to break until it is actually released as stable in June.

---

### Post by larry on 2006-04-08
[QUOTE=localzuk]If you use custom built software, you cannot expect it not to break when you upgrade the version of your OS. You would need to recompile your software really as the libraries that Ubuntu uses are being updated to newer versions and therefore have different functionality.

Also, dapper is currently still at the testing stage, so you should expect things to break until it is actually released as stable in June.[/QUOTE]
Alright, now I am in a better mood, apologies for my previous angry tone.
However, this is not a problem I have had only with Dapper, which is still a beta in some sense.
So, for the future, what should I do when going for the next dist-upgrade?
Should I first remove all the custom-built software?
You said I would need to recompile my software, but how can I easily remove a library which gets installed somewhere in the core of my system and maybe has some links, dependencies etc...?
Thanks for your advice

Larry

---

### Post by localzuk on 2006-04-08
It depends how you build it. I would look into building it via check install [https://wiki.ubuntu.com/CheckInstall](https://wiki.ubuntu.com/CheckInstall) which would keep track of all installed files.

---

