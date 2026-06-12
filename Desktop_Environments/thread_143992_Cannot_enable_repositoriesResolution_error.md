---
title: "Cannot enable repositories/Resolution error"
date: 2006-03-13
forum: Desktop Environments
---

### Post by galume on 2006-03-13
Hi, when I try to enable the universe or multiverse I get the following:

[COLOR="RoyalBlue"]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Temporary failure resolving 'us.archive.ubuntu.com'
[http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg:) Temporary failure resolving 'archive.ubuntu.com'
[/COLOR]
Then this:

[COLOR="RoyalBlue"]The following problems were found on your system:
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)[/COLOR]

and again:

[COLOR="RoyalBlue"]The following problems were found on your system:
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)[/COLOR]


I am unable to add any applications due to these errors.  Also, a member recommended I try Automatix.  When I try the command I get the following output:
[COLOR="RoyalBlue"]
[http://beerorkid.com/automatix/automatix_5.6-2_i386.deb](http://beerorkid.com/automatix/automatix_5.6-2_i386.deb)
--03:03:11--  [http://beerorkid.com/automatix/automatix_5.6-2_i386.deb](http://beerorkid.com/automatix/automatix_5.6-2_i386.deb)
           => `automatix_5.6-2_i386.deb'

Resolving beerorkid.com... failed: Temporary failure in name resolution.[/COLOR]

Am I having a resolution problem?   I am able to use the internet freely, which throws me off.  I should be able to resolve domain names, so are there any thoughts on this problem?

---

### Post by Teroedni on 2006-03-13
hmm you may have get some source list which point to the wrong direction or are yust outdated.

try to run this command


```
Sudo apt-get update
```

If that not helps i would recommend  getting a source .list from one of the many users online here. I cannot help you with that since im running Ubuntu Dapper Drake testing.

---

### Post by galume on 2006-03-13
Hi, here's the output...doesn't look good:

[COLOR="RoyalBlue"]# apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Tempor ary failure resolving 'us.archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Temporary  failure resolving 'archive.ubuntu.com'
Reading package lists... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_bi nary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Pa ckages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary -i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packag es (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Pa ckages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_bi nary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Pac kages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i 386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used ins tead.
[/COLOR]

---

### Post by htinn on 2006-03-14
You have all those _ characters? Weird. Your sources.list should look more like this:

> ## Breezy official
#deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Breezy major bug fix updates
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
#deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Breezy unsupported (universe/multiverse)
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse main restricted
# deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security updates for official
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

## Security updates for universe/multiverse
deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

## Backports for official and universe/multiverse
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

---

### Post by galume on 2006-03-14
I read something about the Ubuntu repositories not lining up with the Debian repositories over time...but then everyone would have that problem.  Anyway, looks like I'll be awaiting the new release and reloading.:-| 
Galume

---

### Post by Teroedni on 2006-03-14
galume please use htinn source list
That should fix it for you:)

---

### Post by galume on 2006-03-16
Teroedni,

Sorry to disappoint...I don't know what "use htinn source list" means.  I mean, I think that you're directing me to use a list of sources other than the default ones in Ubuntu, but i haven't the foggiest idea how exactly...:-k

---

### Post by Teroedni on 2006-03-17
Here how you do it

1.Open a program called Terminal

2.paste this command in and hit enter and submitt your password

```
sudo gedit /etc/apt/sources.list

```


3.Gedit open with a text file. This is your source list

4 Replace your source list with htinn source list

5. Then save and exit from gedit

6.Then you post this command in your Terminal

```
sudo apt-get update
```

Hope this helps:)

---

### Post by leogibson on 2006-03-17
i have a similar problem, only i get this error:

Fetched 2360kB in 14s (159kB/s)
Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: You may want to run apt-get update to correct these problems


i edited my cources.list to what teroedni said. is this a problem? or can i continue using ubuntu without reinstalling, i cant add any programs it seems without other errors about directories and folders missing...???

thanks for any help, 
leo

---

