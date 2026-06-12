---
title: "Help needed: Synaptic Package Manage locked-up"
date: 2009-03-06
forum: General Help
---

### Post by GARoss on 2009-03-06
I'm working in Kubuntu jaunty but I'm sure this problem is not alpha related & would be with any platform. I was trying to add a 3rd party software source to Synaptic Package Manage that failed so I simply closed the program but appearently was saved somehow. Now when I open the Synaptic Package Manage it gives me the following error; 

[I]E: Type 'http://www.nvidia.com/object/linux_display_amd64_180.29.html' is not known on line 42 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.[/I]

When I close the error the Synaptic Package Manage closes, too.
I'm a newbie but understand it wants me to go to the root directory & change or delete line 42. 
Using the terminal I get this;

[I]root@kgeorge-desktop:~# /etc/apt/sources.list
-bash: /etc/apt/sources.list: Permission denied[/I]

How do change permissions? As the owner, why would it lock me out? 
Could someone step me through this process?:?:

---

### Post by GARoss on 2009-03-06
Mark this post as solved! A tip from kubuntuforums.net solved things.

kdesudo kate /etc/apt/sources.list

Then deleting the bad line & saving did the trick.

---

