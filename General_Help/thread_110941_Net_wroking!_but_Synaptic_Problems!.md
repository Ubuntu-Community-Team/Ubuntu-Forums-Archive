---
title: "Net wroking! but Synaptic Problems!"
date: 2006-01-01
forum: General Help
---

### Post by s_spiff on 2006-01-01
Hey,
finally got my net working on ubuntu, so no more restarting a hundered times to ask queries! now I wanted to add / install packages from the Synaptic Package Manager, and when I started it, I got the following error. Can someone please explain what it means, and what I have to do to get rid of it?


<hr>


W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)

<hr>

Someone HELP!

---

### Post by s_spiff on 2006-01-01
wow! when i used to take the trouble of rebooting in windows everytime just to post a question here, i used to get answers in like 3 minutes, and today, 45 mins later, I still don't have a reply! Anways, hope someone turns up!

---

### Post by GeneralZod on 2006-01-01
[QUOTE=s_spiff]wow! when i used to take the trouble of rebooting in windows everytime just to post a question here, i used to get answers in like 3 minutes, and today, 45 mins later, I still don't have a reply! Anways, hope someone turns up![/QUOTE]

Most of the people here are probably hung over :)

Have you tried clicking "Reload" in Syanptic? If that doesn't help, then the sites are probably down and you'll need to find a mirror - something like replacing 

[http://in.archive.ubuntu.com](http://in.archive.ubuntu.com)

with 

[http://us.archive.ubuntu.com](http://us.archive.ubuntu.com)

or suchlike should do the trick.

---

### Post by bonzodog on 2006-01-01
I heard there was a problem with the repos across the world. The US ones are worse affected. Some of the EU ones are working.

---

