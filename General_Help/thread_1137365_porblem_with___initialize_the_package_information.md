---
title: "porblem with :  initialize the package information"
date: 2009-04-25
forum: General Help
---

### Post by hsx826 on 2009-04-25
hi...

I have ubuntu 9.04 .


when I tried to update it or open synaptic or add/remove i always got Errors:confused:!!!



with update :

[IMG]http://i43.tinypic.com/15ygo6x.jpg[/IMG]



> Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/sa.archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


with synaptic :


[IMG]http://i39.tinypic.com/30s95r8.jpg[/IMG]


> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/sa.archive.ubuntu.com_ubuntu_dists_jaunty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.




with add/remove :

[IMG]http://i44.tinypic.com/t05jsh.jpg[/IMG]



> Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.



how I can fix it please ?????????:(


and I'm sorry about my language :-\"

---

### Post by hsx826 on 2009-04-28
I found the answer :)



system>>>>administration>>>software source


and change the server :
  

[IMG]http://i39.tinypic.com/2ztcac8.jpg[/IMG]

---

