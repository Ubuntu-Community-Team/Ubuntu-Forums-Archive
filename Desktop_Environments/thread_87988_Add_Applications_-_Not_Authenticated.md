---
title: "Add Applications - Not Authenticated"
date: 2005-11-09
forum: Desktop Environments
---

### Post by Darrin on 2005-11-09
I was going to install blam using add applications. When I click apply I get this warning about the software im about to install cant be authenticated. Doing so could  allow a malicious individual to take over my system. 

I tried Epiphany browser as well, and get the same thing. Is there something wrong here?

I dont get this message when installing through synaptic.

---

### Post by Kyral on 2005-11-09
What repositories are you using? Epiphany shouldn't give you that error...

I dunno about blam. If you show me your /etc/apt/sources.list I can tell you if those repositories are good though

---

### Post by Darrin on 2005-11-09
Heres my list.

```
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://us.archive.ubuntu.com/ubuntu/ breezy multiverse universe main restricted
```

---

### Post by Darrin on 2005-11-09
That was strange. I tried epiphany again. This time the message wasnt there. :confused:

---

### Post by Kyral on 2005-11-09
Hmm, all your sources are good repos. As long as you are running with these settings I'd say ignore any authetication errors you see. The Ubuntu Repos are valid and good :D

---

### Post by seatea on 2005-11-09
I saw your post and wondered if I  would have the  same problem. I did when trying to install epiphany. I tried to apt-get update and got an error:
 "W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com".

 Maybe  there is a problem with the repository or reinstalling firefox did something to the  source.list.

---

### Post by Kyral on 2005-11-09
Nah....those have been going around again, like they were when Breezy first went stable. Ignore'em. They should be resolved soon.

archive.ubuntu.com is the master repository, so its safe (otherwise we are all screwed because every other mirror syncs to it)

---

### Post by Darrin on 2005-11-09
[QUOTE=Kyral]Hmm, all your sources are good repos. As long as you are running with these settings I'd say ignore any authetication errors you see. The Ubuntu Repos are valid and good :D[/QUOTE]
Thanks for checking them out.

---

### Post by Adapted.Cat on 2005-11-10
I've been getting this same error for a while now. The sequence is:

apt-get update
apt-get upgrade
<get not authenticated error>
<press ctrl-C>
apt-get update
apt-get upgrade
<no errors this time>

The same happens through the desktop update tool. I have to click "Reload" and then everything works fine. I also intermittently get the bad signature error.

So there's nothing wrong with the signatures - it's just that they're not checked when they should be...you have to ask nicely and then they will be.

Bit of a bug, if you ask me ;)

---

### Post by Pete051 on 2005-11-10
I had this problem too, the answer's in another thread just remove "us" from the archive, in my case it was "gb" but it's solved the problem
Pete

---

