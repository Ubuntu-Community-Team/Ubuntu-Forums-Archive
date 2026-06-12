---
title: "Problem Trying to Burn a CD"
date: 2006-03-06
forum: Desktop Environments
---

### Post by danish_demon on 2006-03-06
hello everybody,

as i've done before, i'm going to link to another discussion thread to provide an introduction to my problem.  basically, i can't burn a cd:

[http://www.ubuntuforums.org/showthread.php?p=798313#post798313](http://www.ubuntuforums.org/showthread.php?p=798313#post798313)

anyone know what is wrong?

thanks.

---

### Post by dcstar on 2006-03-07
[QUOTE=danish_demon]hello everybody,

as i've done before, i'm going to link to another discussion thread to provide an introduction to my problem.  basically, i can't burn a cd:

[http://www.ubuntuforums.org/showthread.php?p=798313#post798313](http://www.ubuntuforums.org/showthread.php?p=798313#post798313)

anyone know what is wrong?

thanks.[/QUOTE]
If you are going to install packages, use Synaptic and take advantage of the built-in functions for fixing dependencies and broken packages.

---

### Post by danish_demon on 2006-03-07
alright, i decided to see if my sources.list was the problem, and (surprise, surprise) it was.  i redid it by following this link:
[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

and then doing a "sudo apt-get update"
followed by "sudo apt-get install cdrdao" and it installed fine.  i don't have time right now to see if it will burn a disc now, but i'll try it later today.

---

### Post by danish_demon on 2006-03-07
just to update, it works now.  i just had some problems with my /etc/apt/sources.list ; the clean copy from the link i previously provided solved the problem

---

### Post by Djartklom on 2006-03-08
One KDE app I found worthwhile to install in Gnome was K3b, the disk-burning utility.  It easily rivals Nero Burning ROM in terms of ease of use.

---

### Post by orazios on 2006-03-08
My Ubuntu is my first disto with Gnome but to my experience with KDE, I agree with Djartklom that K3b is excellent for burning !

---

