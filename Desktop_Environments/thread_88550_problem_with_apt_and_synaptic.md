---
title: "problem with apt and synaptic"
date: 2005-11-10
forum: Desktop Environments
---

### Post by etcpool on 2005-11-10
while i was trying to retrieve new software to my system : get this

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)


------------------------------------

W: Failed to fetch [http://th.archive.ubuntu.com/ubuntu/pool/universe/h/helix-player/helix-player_1.0.6-1ubuntu1_i386.deb](http://th.archive.ubuntu.com/ubuntu/pool/universe/h/helix-player/helix-player_1.0.6-1ubuntu1_i386.deb)
  403 Forbidden [IP: 82.211.81.167 80]


-----------------------

i have other ubuntu 5.10 box (for server) in DMC zone and that box work find

can't apt-get update and even install anything... my network connection should not be the problem (or should it??) as i'm using it now with no interrupt...


Thank you very much in advance

it would be nice if i get the answer quickly bcause i have my jobs waiting to be done on this machine and can't proceed with out added software :P

Thanks again ;)

---

### Post by raublekick on 2005-11-10
when you're in Synaptic, hit the refresh/reload button, that hopefully will fix it.

---

### Post by etcpool on 2005-11-10
when i hit reload i got this :


Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.


[http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz:) 403 Forbidden
[http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz:) 403 Forbidden
[http://th.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://th.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) 403 Forbidden [IP: 82.211.81.167 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) 403 Forbidden [IP: 82.211.81.151 80]
[http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz:) 403 Forbidden [IP: 82.211.81.151 80]



i wanna know what the f*ck 's happenning to my computer :P :P :P :S

i used to happend to my server box in dmz , but just like this situation it just facking unresonnbly come and go with no clue :(


Thanks  for the reply , i guess i should get more time to find out..... :P

---

### Post by migueljacq on 2005-11-10
Sometimes I've noticed that there is such a problem. I've been told that it's just maintenance or problems at the other end, and having kept trying for a while, maybe an hour later or so, it seems to be running again.
I just keep running apt-get update til it works, because it looks like there is nothing wrong with your repositories.

---

