---
title: "Synaptic package install problem"
date: 2009-01-07
forum: General Help
---

### Post by shouldersmagru on 2009-01-07
Hello everybody, 

I have a post in the installation and upgrades section ([http://ubuntuforums.org/showthread.php?t=1032583](http://ubuntuforums.org/showthread.php?t=1032583)) and this might look like a repost, but this post is more specific to my problem with the synaptic package manager, not my own attempts at compiling the programs at hand.

I am trying to re-install **autoconf** and **automake** on my system. I marked both for a complete removal off the system to start fresh. First i am just trying to get autoconf installed, since automake won't even think about installing until thats on. 

The prerequisites are installed, m4, perl etc. I get this error when autoconf is trying to install via the synaptic package manager: '**install -info: No dir file specified**'

Does anyone know what this means? Do i have to create a directory for it? Or do i need to set a system variable? or just download the source and tweak the make/ configure file (which im trying to do and running into more problems) or is the problem simpler than i'm making out?

Since the synaptic package install process is fairly autonomous, at what point can i set this 'dir' variable that it needs? Will this mean i will probably have to do a '**sudo apt-get**' and include some switches in that command string?

Any help on this problem would be greatly appreaciated.

---

