---
title: "Jaunty Duplicate source.list entries and gpg key will not download"
date: 2009-05-22
forum: General Help
---

### Post by stevepb on 2009-05-22
I keep getting an error when updating. apparently duplicate repositories are the problem, but I cannot see where.... I'd really appreciate some help, i've been trying different fixes for the last fews weeks and i am not getting anywhere.

Error message :

W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-i386_Packages)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC6D7D9D009ED615


I have removed duplicate entries in my source.list but i keep getting the same error message and cannot figure why it insists i have duplicated entries, maybe i am just blind??
Also the last error is a new one today, I can't seem to download the gpg key using this command : gpg --keyserver keyserver.ubuntu.com --recv 009ED615


Below is a copy of my source.list :

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty restricted
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) jaunty-proposed restricted main multiverse universe
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/mozillateam/ppa/ubuntu](http://ppa.launchpad.net/mozillateam/ppa/ubuntu) jaunty main
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) jaunty main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope"
deb [http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) jaunty main
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) jaunty main
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free #google
deb [http://ppa.launchpad.net/lidaobing/ubuntu](http://ppa.launchpad.net/lidaobing/ubuntu) jaunty main #chmsee
deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) jaunty main #shutter
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security restricted main multiverse universe

Thanks for any assistance.

---

### Post by plucky on 2009-05-22
> W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_free_binary-i386_Packages)
W: Duplicate sources.list entry [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages (/var/lib/apt/lists/packages.medibuntu.org_dists_jaunty_non-free_binary-i386_Packages)



See if you have another **Medibuntu** entry in sources.list.d with ```
cat /etc/apt/sources.list.d/medibuntu.list
```

If you have,then edit the entry in sources.list and put a # in front of ```
deb http://packages.medibuntu.org/ jaunty free non-free
```


> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC6D7D9D009ED615


for PPA key,see this [thread](http://ubuntuforums.org/showthread.php?t=1056099&highlight=ppa)

or

This [blog](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)


Good Luck

---

### Post by stevepb on 2009-05-22
Hi Pluky,

Thanks a lot for your reply.

I didn't realise I had a seperate medibuntu source list, I do now though, thanks a lot. There was the same entry found in this list as the default source list. So that solved my duplicate entried problem, your bloody brilliant :-) Cheers...

I had a look at the script to auto search for pgp keys and import them, I used the instructions and another key was added. But this did not solve my problem, and i have anther key issue due to the import.

the error message :
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures were invalid: BADSIG 61270A939E324B12 Launchpad PPA for LI Daobing
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures were invalid: BADSIG FC6D7D9D009ED615 Launchpad PPA for Shutter Team

I've tried this a number of times after removing the invalid keys.
I followed instruction to add the ppa teams key.

When i visit the ppa teams overview page it displays the following, but the shutter team does not have a link!


Search results for '0x5017d4931d0acade295b68adfc6d7d9d009ed615'

Type bits/keyID    Date       User ID

pub  1024R/009ED615 2009-01-20 Launchpad PPA for GScrot Team
                   no link --> Launchpad PPA for Shutter Team <-- no link!


This is the key I used, but it does not work.

Public Key Server -- Get ``0xfc6d7d9d009ed615 ''

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXWdeAEEAL3XbmiasfSzhJ84HPSZaKxKCzSmJmzck/zyBADJfNq018XHmvfsdqNgNwqG
PcSG52iI11ZxVOU/VYfqozbSenGQg3sCittv//ydZEzfYpPvPJ3DVV9xgNR4JL0Pr+KHCGQz
ZrCbdez/l1MeRoaYcgjpiTuLg+0GBkU+hcqX6vchABEBAAG0HUxhdW5jaHBhZCBQUEEgZm9y
IEdTY3JvdCBUZWFtiJ8EMAECAAkFAkm/bPECHSAACgkQ/G19nQCe1hXEFQP/aGwzEL9hMGo/
DHKQxxEqGPAmSzTuYC8l3df6tKOSw7f4+6Q1Za8Y0ZI+1wqcXQoN8cblQYGcj2pMkbpCxE/a
ELQNJQ+oZVE8dDQTefsv5HcI6CnABPgFxkwE4l1gE8jCungK0HyJCt1fBWQELU4N7/VkkZCg
3knvFO6nQLSmV7CItgQTAQIAIAUCSXWdeAIbAwYLCQgHAwIEFQIIAwQWAgMBAh4BAheAAAoJ
EPxtfZ0AntYVzmcD/ifMEE1R9kilp3Gsvom2F/A9xCLuTvNwOU9SqO3mDxaZgj3DR3JKND1g
1Yn0h8smbC3T1svOxXfS4MUtuhWBUfOc81CohQb/Gq89/0S80pfRa/X7maXzFVKNnM97fHU1
KK+C8AAY+7XF/YWschrCiUDmL+y0xex0dH8FFnFSqCfwtB5MYXVuY2hwYWQgUFBBIGZvciBT
aHV0dGVyIFRlYW2ItgQTAQIAIAUCSZtyGwIbAwYLCQgHAwIEFQIIAwQWAgMBAh4BAheAAAoJ
EPxtfZ0AntYVHjkD/ime7XsYxVGcfU9JClNcN4a3JKw96sJ4Vnr4OWZey7MVeK1zM6p6tbpg
KNMf/wFaY7sEy/Lt3B+a89Jy9jxdRXMNtHft7KT3CcWoE8qe9Yjk1X6sUMIxGiQ3TLa1dKC6
O+1FxiRudUYl4taYz8BQ6SScMuhju3E80/HRyLkJ73Tz
=qtZP
-----END PGP PUBLIC KEY BLOCK-----

After I add this key I get the following error : 

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 61270A939E324B12

I haven't tried the above key, not sure what team it is....

[mid post update]
I found them in ppa and it reports that it is for Hardy, i'm using Jaunty, does this means i've accidentally installed a hardy package?
Whoops!.... If so what can I do?

LI Daobing

deb [http://ppa.launchpad.net/lidaobing/ubuntu](http://ppa.launchpad.net/lidaobing/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/lidaobing/ubuntu](http://ppa.launchpad.net/lidaobing/ubuntu) hardy main

Continuing Error Message :

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures were invalid: BADSIG FC6D7D9D009ED615 Launchpad PPA for Shutter Team
W: You may want to run apt-get update to correct these problems

Any Ideas?

Thanks :-)

---

### Post by plucky on 2009-05-22
Did you follow the steps in the video precisely?

Just added both the LiDaobing and Shutter team PPA and keys using the steps on the video and it is working for me.

This is the link for the Shutter Team [https://launchpad.net/~shutter/+archive/ppa](https://launchpad.net/~shutter/+archive/ppa)

and

 This is the link for Li Daobing [https://launchpad.net/~lidaobing/+archive/ppa](https://launchpad.net/~lidaobing/+archive/ppa)

Don't know where the Hardy repository came from as they weren't in your sources.list in the first post.

Good Luck

---

### Post by stevepb on 2009-05-22
HI,

Yeah followed the instructions to the letter...

I also find it odd that the automated script I used also had problems with the gpg keys. Perhaps there is something wrong there....?

And the hardy related issue wasnt really an issue, i was looking at their profile which had hardy repos, d'uh...

Here are the keys i use from the links you provided, the key for shutter is the same as previously used. It's just outputting BADSIG invalid key errors :-k.

key for uid Launchpad PPA for Shutter Team
sig  sig3  009ED615 2009-02-18 __________ __________ [selfsig]
 is

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXWdeAEEAL3XbmiasfSzhJ84HPSZaKxKCzSmJmzck/zyBADJfNq018XHmvfsdqNgNwqG
PcSG52iI11ZxVOU/VYfqozbSenGQg3sCittv//ydZEzfYpPvPJ3DVV9xgNR4JL0Pr+KHCGQz
ZrCbdez/l1MeRoaYcgjpiTuLg+0GBkU+hcqX6vchABEBAAG0HUxhdW5jaHBhZCBQUEEgZm9y
IEdTY3JvdCBUZWFtiJ8EMAECAAkFAkm/bPECHSAACgkQ/G19nQCe1hXEFQP/aGwzEL9hMGo/
DHKQxxEqGPAmSzTuYC8l3df6tKOSw7f4+6Q1Za8Y0ZI+1wqcXQoN8cblQYGcj2pMkbpCxE/a
ELQNJQ+oZVE8dDQTefsv5HcI6CnABPgFxkwE4l1gE8jCungK0HyJCt1fBWQELU4N7/VkkZCg
3knvFO6nQLSmV7CItgQTAQIAIAUCSXWdeAIbAwYLCQgHAwIEFQIIAwQWAgMBAh4BAheAAAoJ
EPxtfZ0AntYVzmcD/ifMEE1R9kilp3Gsvom2F/A9xCLuTvNwOU9SqO3mDxaZgj3DR3JKND1g
1Yn0h8smbC3T1svOxXfS4MUtuhWBUfOc81CohQb/Gq89/0S80pfRa/X7maXzFVKNnM97fHU1
KK+C8AAY+7XF/YWschrCiUDmL+y0xex0dH8FFnFSqCfwtB5MYXVuY2hwYWQgUFBBIGZvciBT
aHV0dGVyIFRlYW2ItgQTAQIAIAUCSZtyGwIbAwYLCQgHAwIEFQIIAwQWAgMBAh4BAheAAAoJ
EPxtfZ0AntYVHjkD/ime7XsYxVGcfU9JClNcN4a3JKw96sJ4Vnr4OWZey7MVeK1zM6p6tbpg
KNMf/wFaY7sEy/Lt3B+a89Jy9jxdRXMNtHft7KT3CcWoE8qe9Yjk1X6sUMIxGiQ3TLa1dKC6
O+1FxiRudUYl4taYz8BQ6SScMuhju3E80/HRyLkJ73Tz
=qtZP
-----END PGP PUBLIC KEY BLOCK-----


For LI Daobing Key

pub  1024R/9E324B12 2009-01-19            

uid Launchpad PPA for LI Daobing
sig  sig3  9E324B12 2009-01-19 __________ __________ [selfsig]

is

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXQaFQEEALX4DiOqvIjzGRk5sRVPaXwFP+xDdyHiZ94tjbR9+LrdVMeuBgDJXbvhwbst
h/AWGHy99sb7IDP7TgCCK2NX6Cp1s30OUCytlb/9PljSyEu9aW5QeI5KoLA8OOnoLr7TjdPj
LkFU1d/uDMc7xZ38oB4MXQFtKomoLQuMTqlGpwxLABEBAAG0HExhdW5jaHBhZCBQUEEgZm9y
IExJIERhb2JpbmeItgQTAQIAIAUCSXQaFQIbAwYLCQgHAwIEFQIIAwQWAgMBAh4BAheAAAoJ
EGEnCpOeMksSeC4D/1kyLO1evUDX8NNbiI5FkyLGE93pQ0mlmspZmTPa/YOPkHAePKvC+Gts
7CRJc/eiW9P+FoM1WqMxMJ9i1XCixz3E0Fri2KIdNA9dRD0pZnyeCT3I4AOktHe1jqecpdfC
lBLCGpfbwhGq5oOBpovnKVg7xrmz0uOWktvx+6W348co
=EMVl
-----END PGP PUBLIC KEY BLOCK-----

I also tried this in the console : 

Shutter team
command : sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0x5017d4931d0acade295b68adfc6d7d9d009ed615

Shell output : ~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0x5017d4931d0acade295b68adfc6d7d9d009ed615
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 0x5017d4931d0acade295b68adfc6d7d9d009ed615
gpg: requesting key 009ED615 from hkp server keyserver.ubuntu.com
gpg: key 009ED615: public key "Launchpad PPA for Shutter Team" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
training@ulatop:~$ 


LI Daobing
command : sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0x2cc3ed28dde25271b59e187561270a939e324b12

sheilds output: ~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0x2cc3ed28dde25271b59e187561270a939e324b12
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 0x2cc3ed28dde25271b59e187561270a939e324b12
gpg: requesting key 9E324B12 from hkp server keyserver.ubuntu.com
gpg: key 9E324B12: public key "Launchpad PPA for LI Daobing" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)


when I do sudo apt-get update I get this error :
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures were invalid: BADSIG 61270A939E324B12 Launchpad PPA for LI Daobing
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures were invalid: BADSIG FC6D7D9D009ED615 Launchpad PPA for Shutter Team
W: You may want to run apt-get update to correct these problems

Same as before ... very confusing....

Thanks for helping me out.

Have you any more suggestions? (I hope :-)) 
I'm sure these are the correct keys.

Cheers

---

### Post by plucky on 2009-05-22
The error has changed from > W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC6D7D9D009ED615

To > W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures were invalid: BADSIG 61270A939E324B12 Launchpad PPA for LI Daobing
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures were invalid: BADSIG FC6D7D9D009ED615 Launchpad PPA for Shutter Team

Open Software Sources and go to the Authentication tag and check what keys have been added.Delete the ones for the PPA repositories.

Then edit your sources.list and put a # in front of all the PPA repositories except one.Then try to add the key for that repository.If that works,then add the other repositories one at a time.Use the method specified in the video as I am not too sure what the script method uses.

Do you know why you need the PPA repositories?
Are there special programs that you need?

The messages you are getting are only warnings and should not stop you installing software from the PPA repositories.

Good Luck

---

