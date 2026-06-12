---
title: "I'd like to contribute to free software..."
date: 2009-03-03
forum: General Help
---

### Post by csrrmrzrn on 2009-03-03
[FONT="Verdana"][SIZE="3"]Hi everybody.

My name is César, I'm a computer science student and I'm from Venezuela.

I'd like to contribute to free software (software libre, open source) with my dissertation. A teacher of my university gave me an idea about a network package management system, do you guys know what I mean? A package management system that enables simple network installations, maintenance and removal of package in multiple computers. So, some system administrators or someone who doesn't have a high technical knowledge can make the task of managing software packages quickly and easily without the need to worry about the heterogeneity of operating systems Linux on the network or time consuming to acquire new knowledge to make a shell script. In addition, the package management will take control over these tasks through the network... And the case of study will be Ubuntu :D

What do you guys think about this subject? It seems to me very interesting but I'm kind of worried because this subject is big enough and the teacher seems to doesn't have much time to be my mentor...

Do you guys have any other idea to a dissertation?
I'll appreciate your answers.[/SIZE][/FONT]

---

### Post by dmizer on 2009-03-03
You mean like the package manager "apt": [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto) that Debian and Ubuntu rely on? Or [YUM](http://en.wikipedia.org/wiki/Yellow_dog_Updater,_Modified) that Redhat and Fedora rely on. Or [Packman](http://en.wikipedia.org/wiki/Pacman_(Arch_Linux)) in Arch?

Why reinvent the wheel? Is there something specific that these package managers are missing? Any of these can be hosted on a local server to push software to LAN clients.

Edit: here's a good howto -> [http://news.softpedia.com/news/Create-a-LAN-Repository-with-Apt-Cacher-45978.shtml](http://news.softpedia.com/news/Create-a-LAN-Repository-with-Apt-Cacher-45978.shtml)

---

### Post by lisati on 2009-03-03
Other things to think about include installing the updates remotely on multiple machine (maybe from your server to networked machines). 

Another possibility is having a cache of the updates on your network's server(s) that the network users can access at their leisure (possibly with some "corporate guidelines")

(I don't know the specifics on either suggestions: the computers on my home network all have different operating systems.....)

---

