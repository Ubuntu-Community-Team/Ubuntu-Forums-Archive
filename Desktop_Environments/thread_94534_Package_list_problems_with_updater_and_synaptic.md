---
title: "Package list problems with updater and synaptic"
date: 2005-11-24
forum: Desktop Environments
---

### Post by stretched_lobes on 2005-11-24
Hello I just did a fresh reinstall of Breezy yesterday. Today I had an update and this message was given to me. 

W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

 
I then looked for new repositories through synaptic. It stalled and gave me the lists of packages that may be outdated they were:


[http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release](http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release)


I am kind of dissapointed because, I was having problems with updates before on 5.04. It was giving me Bad SIG messages. I hope this is not a problem with synaptic being buggy. 

I would like to know how to fix this problem.


If anyone has any ideas please post them, they would be greatly appreciated. 

                                                                                Thanks

---

### Post by Lambert on 2005-11-24
There have been posts lately about the us mirrors and problems. Go into your /etc/apt/sources.list and remove the us. from the lines

exmaple

deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") breezy-updates main restricted

becomes

deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") breezy-updates main restricted

---

### Post by Pablo_Escobar on 2005-11-24
No Dapper for a Breezy User :)
And Lambert makes a valid suggestion - remove the us. It helped me :)

---

### Post by Lambert on 2005-11-24
Thanks for catching that, make sure you use breezy and not dapper.

---

