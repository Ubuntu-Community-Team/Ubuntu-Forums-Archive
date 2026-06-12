---
title: "warnin on openin synaptic."
date: 2006-01-25
forum: Desktop Environments
---

### Post by krait on 2006-01-25
hi, 

everytime i open synaptic, i get the following warnin. Cud someone tell me if its somethin minor or?

thanks 


W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://sg.archive.ubuntu.com](http://sg.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/sg.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages (/var/lib/apt/lists/wine.sourceforge.net_apt_binary_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://deb.opera.com](http://deb.opera.com) unstable/non-free Packages (/var/lib/apt/lists/deb.opera.com_opera_dists_unstable_non-free_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by alamba on 2006-01-25
Are you connected to the net?

Akshay

---

### Post by krait on 2006-01-25
[QUOTE=alamba]Are you connected to the net?

Akshay[/QUOTE]

Yes i am connecting to the net. 

cheers

---

### Post by carlosqueso on 2006-01-25
try opening your sources.list (sudo gedit /etc/apt/sources.list) and taking out the sq before the address. The country mirrors don't seem to work for some reason.  Also, if you don't know anything specific that you need from those non-ubuntu sites, I'd comment them out by putting a # in front of them.

---

### Post by krait on 2006-01-25
[QUOTE=carlosqueso]try opening your sources.list (sudo gedit /etc/apt/sources.list) and taking out the sq before the address. The country mirrors don't seem to work for some reason.  Also, if you don't know anything specific that you need from those non-ubuntu sites, I'd comment them out by putting a # in front of them.[/QUOTE]

i did as u told me. but i still get some warnings. please find my sources.list below. do lemme know wat changes i am to make.

thanks


##inddeb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse universe main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
##deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
##deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf) breezy free non-free
##deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf) breezy free non-free
##deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) unstable non-free

---

### Post by trevorv on 2006-01-25
I doubt it's much help, but have you tried running apt-get update ?

---

### Post by carlosqueso on 2006-01-25
that's weird then....if you get errors from the ubuntu repos, It sounds like a network problem. Unfortunately, I'm not qualified to help you with that.  Sorry.  Possibly try posting in the repositories forum.

---

### Post by earobinson on 2006-01-25
do a ping [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) to see if you can axcess the repo or better yet you can go there in a web browse.

---

### Post by sayanchak on 2006-01-25
When you get those wierd errors. Close the dialog box and hit Reload. There is a green button towards the top left.

---

### Post by krait on 2006-01-25
[QUOTE=sayanchak]When you get those wierd errors. Close the dialog box and hit Reload. There is a green button towards the top left.[/QUOTE]

i did as u said, and it started downloadin some stuff. but at the end, it gave me this,

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz:](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz:) MD5Sum mismatch

On clickin Ok to this ,i got another warnin,

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


and to EAROBINSON' s question, yes i tried to open the link on the browser, and it was workin fine.

thanks

(later)- i tried reopenin Synaptic and this time i dint get any warnings. So does this mean the problem has been solved?

---

### Post by krait on 2006-01-31
well hello again. the problem is back. I think its a problem with the sites on my sources.list file. i get 404  not found for quite a few of them. I would really appreciate it if someone could pass on their sources.list file. someone using the singpore mirrors?

thanks.

This is the error i get.

: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ftp.lug.ro](http://ftp.lug.ro) main/restricted Packages (/var/lib/apt/lists/ftp.lug.ro_ubuntu-backports_breezy-extras_dists_main_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ftp.lug.ro](http://ftp.lug.ro) main/universe Packages (/var/lib/apt/lists/ftp.lug.ro_ubuntu-backports_breezy-extras_dists_main_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ftp.lug.ro](http://ftp.lug.ro) main/multiverse Packages (/var/lib/apt/lists/ftp.lug.ro_ubuntu-backports_breezy-extras_dists_main_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

---

### Post by mcduck on 2006-01-31
Try Source-O-Matic:

[http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

---

### Post by Almighty on 2006-01-31
[QUOTE=mcduck]Try Source-O-Matic:

[http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")[/QUOTE]


I am having the same problem with my system. Unfortunately source-O-matic didnt help.

---

### Post by PhilOSparta on 2006-02-10
It's interesting to note that I just ran EasyUbuntu and now I have the same problem with the bad signing keys.  Everything worked prior to running EasyUbuntu. ( which wasn't that easy!:cry: )

I'll research further and post back here with what I find.

---

### Post by PhilOSparta on 2006-02-10
There is an error in the GPG key in your box compared to the one at the source site. I ran [http://ubuntulinux.nl/source-o-matic](http://ubuntulinux.nl/source-o-matic)
which generates a sources.list file for you based on the repos that you want. Under sudo, replace your /etc/apt/sources.list file with the generated file. The generated file has instructions in it for changing the keys for the repos.

This is a sample of the file generated for one of my selected repos.
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

Check the man page for apt-key for additional info.

This worked for me.

---

### Post by robotgeek on 2006-02-11
[QUOTE=PhilOSparta]It's interesting to note that I just ran EasyUbuntu and now I have the same problem with the bad signing keys.  Everything worked prior to running EasyUbuntu.
[/QUOTE]
EasyUbuntu does not mess with your apt keys. If you are convinced otherwise, please file a bug on launchpad (link is in my signature). 

[QUOTE=PhilOSparta]
( which wasn't that easy!:cry: )
[/quote]
We know, it's not released yet for that reason. It's still in beta, and people who want to help us fix bugs may test it before we release it.

---

