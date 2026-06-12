---
title: "Installating KDE on UBUNTU?"
date: 2005-07-07
forum: Desktop Environments
---

### Post by mhbengal on 2005-07-07
I installed Ubuntu on my laptop but needed KDE hence I used the FAQ steps to do the following:

"sudo apt-get remove ubuntu-desktop" (This works and is removed)
"sudo apt-get install kubuntu-desktop" using the UNIVERSE repos, but an error message turns up saying no such package found.

How do I now install KDE (Convert to Kubuntu) on this existing Ubuntu Hoary installation. Is there a way at the tiem of installating Ubuntu to get KDE installed.

Mustapha

---

### Post by tread on 2005-07-07
sudo apt-get remove ubuntu-desktop
will not remove all the gnome packages, just the meta package ubuntu-desktop.

Did you do a:
sudo apt-get update
after you enabled the universe repos?

Incidentally, I would recommend doing 
sudo aptitude install kubuntu-desktop

since if you install using aptitude, you can uninstall it much more easily later, if you so desire.

---

### Post by mhbengal on 2005-07-07
Yes, I did an "apt-get update" after enablibng the UNIVERSE repos, however i still get the message "cant find package".

Further I tried to run: "apt-get install kde", but many dependencies were missing or just not installable.

Mustapha

---

### Post by tread on 2005-07-07
You are on Hoary, right? Hmm .. I can't think of another quick solution .. would you post the contents of /etc/apt/sources.list here?

---

### Post by mohaham on 2005-07-07
have you enabled the extra repos like this...
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by tread on 2005-07-07
You dont need extra repos for kubuntu, do you? Its in the default ubuntu repos .. the backports might contain updated apps but thats all.

---

### Post by SGC on 2005-07-07
[QUOTE=tread]You dont need extra repos for kubuntu, do you? Its in the default ubuntu repos .. the backports might contain updated apps but thats all.[/QUOTE]
 For kubuntu-desktop you need kubuntu.org repository (the one with kde 3.4.1), read how to enable it here:
[http://www.ubuntuforums.org/showpost.php?p=225750&postcount=2](http://www.ubuntuforums.org/showpost.php?p=225750&postcount=2)

---

### Post by tread on 2005-07-07
Thats weird?
```

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://acm.cs.umn.edu/ubp/ hoary-backports main universe multiverse restricted
deb http://acm.cs.umn.edu/ubp/ hoary-extras main universe multiverse restricted

```

Thats my sources.list, and I can see kubuntu-desktop in the packages list.

---

### Post by SGC on 2005-07-07
[QUOTE=tread]Thats weird?
...
Thats my sources.list, and I can see kubuntu-desktop in the packages list.[/QUOTE]
 Yes it is in the package list, since it's on ubuntu repository, but when you try to install it you will need a dependency from kubuntu.org.

---

### Post by tread on 2005-07-07
hmm .. its still strange. I recollect installing kubuntu-desktop and didn't add any repos for it. Or maybe I installed KDE, not kubuntu-desktop :confused:

---

### Post by aragorn2909 on 2005-07-07
Correct me if I'm wrong, but the kubuntu-desktop package isn't *required* to get kde up and running.  I just posted this in another thread, shouldn't ```
sudo apt-get install kde
``` do the trick?

---

### Post by SGC on 2005-07-07
[QUOTE=tread]hmm .. its still strange. I recollect installing kubuntu-desktop and didn't add any repos for it. Or maybe I installed KDE, not kubuntu-desktop :confused:[/QUOTE]
 Its started to happenes after realesing kde 3.4.1, apt-get or synaptic will tells that kubuntu-desktop dependes on konversation 3.4.1 .

[http://ubuntuforums.org/showthread.php?t=46401](http://ubuntuforums.org/showthread.php?t=46401)
[http://ubuntuforums.org/showthread.php?t=43818](http://ubuntuforums.org/showthread.php?t=43818)
[http://ubuntuforums.org/showthread.php?t=43442](http://ubuntuforums.org/showthread.php?t=43442)

---

### Post by tread on 2005-07-07
Oh, ok .. thanks.

---

### Post by SGC on 2005-07-07
But the applications and the settings that cames with kubuntu-desktop worth the while

---

### Post by jcohen on 2005-07-07
That's not really the problem. The fault is actually with backports. If you do "apt-cache show kubuntu-desktop" you'll see that kubuntu-desktop does not depend on any particular version of konversation. The problem is that Backport's version of Konversation is broken. It depends on KDE 3.4.1 (which it shouldn't since backports is meant to be used on a base Hoary system). You will need to force the hoary version of Konversation to be installed manually with:

sudo apt-get install konversation=0.16-1ubuntu1

You can also force the hoary version to be installed in synaptic. Bring up synaptic and search for konversation. Highlight the konversation package and then select Package > Force Version from the menu and select 0.16-1ubuntu1 (hoary).After that, hit apply to install. Once that's complete you can install kubuntu-desktop or the kde meta-pacakge in synaptic or with apt-get.  In order to prevent synaptic or Update Manager from complaining in the future that it can't upgrade konversation, you can also lock the version to 0.16 by choosing Package > Lock Version after highlighting the konversation package. This needs to be done after konversation 0.16 has been installed. 

Oh, and one of the forum posts said that you should install KDE 3.4.1. This is ABSOLUTELY unnecessary and may make the upgrade to breezy more difficult. Don't do this!

---

