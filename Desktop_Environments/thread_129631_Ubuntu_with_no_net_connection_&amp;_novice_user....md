---
title: "Ubuntu with no net connection &amp; novice user..."
date: 2006-02-14
forum: Desktop Environments
---

### Post by gilbertuntu on 2006-02-14
I just recieved my ubuntu disks, my first encounter with linux except for a brief affair with knoppix... I used the ubuntu live disc first, everything seemed good, movies, mp3's etc worked, installed the OS successfully on a seperate partition... loads fine etc... it's just putting new things on there.

I do not have an internet connection at home at present so the universe and multiverse repositories are of no use yet, I do however need mp3 codecs etc but have no idea where to get them from or how to install them...

I have a few coverdiscs from linux magazines and have followed their instructions for installing programs, extracting the tar.gz etc then ./configure but at the end it says something like C Compiler cannot create executables, and the shell does not recognise the "make" command as printed in the magazines... I'm a fairly competent computer user, but this is all new to me, I have no idea how to get the stuff i want onto linux without the internet and apt-get.

Much thanks for any help..

---

### Post by Robgould on 2006-02-14
You will have to bring files you need on other media and install from there.  You will have a hell of a time resolving dependencies.  That is what apt and synaptic do for you, resolve all of your dependencies and make sure everything works.  You would think that if an installation went wrong it would just mess itself up, but that is wrong.  You could actually cause other packages to break.  I think you can put a .deb file on a disk and let synaptic install it, as long as synaptic has all the dependencies (you could use and .rpm with alien).  But the trouble will come when you start running into dependencies of dependencies that don't exist.  
 
I guess what I am trying to say is that it can be done, just be careful.  Download the .deb file that you want to use and let synaptic install it, or tell you why it can't.

---

### Post by gilbertuntu on 2006-02-14
Ok, thanks for the speedy reply... you just confirmed what I thought.

Cheers.

---

