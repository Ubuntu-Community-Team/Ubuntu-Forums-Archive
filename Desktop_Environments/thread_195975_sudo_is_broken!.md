---
title: "sudo is broken!"
date: 2006-06-13
forum: Desktop Environments
---

### Post by drews_blunted on 2006-06-13
So i have some odd problem with my ubuntu system Sudo does not work at all! i have to manual su to root to use any admin programs that usualy work with sudo. does anyone know why this is. i set my root passwd could this of messed sudo up? i get a gtk error when trying to load any program like synaptic using sudo in the terminal?

---

### Post by theonhighgod on 2006-06-13
i have the same problem exactly, i used to have the problem with loading any x based programs from root, but then that seemed to be fixed after i rebboted (i upgraded loads of packages in berrtween), 

its causeing load of packages to malfunction effecting sounda nd ksusu and other simeral small programs which makes running configuartion stuff hard,

please can some one offer some help?

its a clean install i just dont understand :(

---

### Post by aysiu on 2006-06-13
Maybe this might help.
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by theonhighgod on 2006-06-14
thanxs for the link, randomly lastnite i figured it out, in other distro i used the groups had been setup b4 i used it, but it seemed i had to ad me to a fewgroups to allow stuff, 

to change my users groups i used "userconfig", and ran it as root, then added admin and audio and a few others in "secondary groups",

pretty simple when u know how looking back!

---

