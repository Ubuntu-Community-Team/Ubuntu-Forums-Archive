---
title: "Synaptic problem...."
date: 2006-02-03
forum: Desktop Environments
---

### Post by yarvin on 2006-02-03
whenever I do an update or go into the synaptic program I get this error:

W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)

how can I fix it?

thanks for any help given....

---

### Post by Heliix on 2006-02-03
hi yarvin
open your 
/etc/apt/sources.list
as root and edit manually the lines that say where to look for the packages. 
the server(s) should be close to your geographical location. 
i have here
deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) breezy main restricted
..and some more lines like this.. for universe, security packages
hope it helps you where/what to look for
Heliix

---

### Post by Heliix on 2006-02-03
hi yarvin
open your 
/etc/apt/sources.list
as root and edit manually the lines that say where to look for the packages. 
the server(s) should be close to your geographical location. 
i have here
deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) breezy main restricted
..and some more lines like this.. for universe, security packages
hope it helps you where/what to look for
Heliix

---

### Post by MartinG on 2006-02-03
Can you post your /etc/apt/sources.list, please. It looks as if the entries for plf are screwed.

---

### Post by yarvin on 2006-02-03
um... yeah sure...

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://kubuntu.org/packages/kde35](http://kubuntu.org/packages/kde35) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

---

### Post by MartinG on 2006-02-03
OK, they look fine.  Another bright idea bites the dust :(

Flying blind now, what I'd suggest is that you comment out these lines (add # at the start of the line), and then do an update.  Once you've done this, open /var/lib/apt/lists and remove any files beginning ftp.free.fr.  Then re-enable the repositories and try update again.

---

### Post by yarvin on 2006-02-03
there was no begining with "ftp.free.fr."....

---

### Post by MartinG on 2006-02-03
[QUOTE=yarvin]there was no begining with "ftp.free.fr."....[/QUOTE]That's fine. When you ran update after disabling the repos, apt will have removed them itself.  I was just concerned that a corrupt file might have lingered.  Have you finished the process of re-enabling and updating again?

---

### Post by yarvin on 2006-02-03
yeah I re enabled them.... and then ran the update....

---

### Post by MartinG on 2006-02-03
[QUOTE=yarvin]yeah I re enabled them.... and then ran the update....[/QUOTE]And are you still getting the error messages?

---

### Post by yarvin on 2006-02-05
ok now I'm getting a different error...

[QUOTE=yarvin's laptop]
W: GPG error: [http://kubuntu.org](http://kubuntu.org) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A506E6D4DD4D5088
W: You may want to run apt-get update to correct these problems
[/QUOTE]

and this time there were a bunch of ftp.free.fr

[QUOTE=also from yarvin's laptop]
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Get:25 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Get:26 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Get:27 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages [2304kB]
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Get:29 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Get:30 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Get:31 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages [545B]
Get:32 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages [2337B]
Get:33 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources [316B]
Get:34 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources [473B]
[/QUOTE]

and it listed a bunch of Kubuntu stuff too... I don't know why.... I never did install kubuntu.....> 

---

### Post by MartinG on 2006-02-06
[QUOTE=yarvin]ok now I'm getting a different error...

and this time there were a bunch of ftp.free.fr

and it listed a bunch of Kubuntu stuff too... I don't know why.... I never did install kubuntu.....[/QUOTE]Right, the original error (post #1 in this thread) is now sorted, OK?

Turning to this lot, your second quote is not an error, it's the proper working of apt-get update, just telling you what's going on.  According to your sources.list (post #5 in this thread) you have enabled the ftp.free.fr and kubuntu.org repositories.  However, enabling a repository is not the same as installing software from it.  All that you have in your quote is a listing of the repositories as it retrieves the package lists; it's not installing anything, and it's not reporting errors.  This is true of the ftp.free.fr stuff and the kubuntu stuff.  What did you *think* was going on?

As to your first quote, there are two ways of dealing with this.  If you don't want any packages from KDE 3.5, comment out the kubuntu.org line in your sources.list, and run apt-get update.  If you do use some KDE 3.5 stuff, you need to add the key as follows:```
wget http://people.ubuntu.com/~jriddell/kubuntu-packages-jriddell-key.gpg
 sudo apt-key add kubuntu-packages-jriddell-key.gpg
sudo apt-get update
```

---

