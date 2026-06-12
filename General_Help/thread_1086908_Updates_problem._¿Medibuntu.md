---
title: "Updates problem. ¿Medibuntu?"
date: 2009-03-04
forum: General Help
---

### Post by marticc on 2009-03-04
HI, I am having some troubles updating Ubuntu 8.10, and I hope you might help me. Before starting I would like to apologise for my poor English.  Please note that I have my Ubuntu in Spanish, so I have translated into English all the messages quoted below, and I guess that my translation won’t be perfect, but I hope you won’t have any troubles understanding them.

Let’s get to the point: Everytime I try to update Ubuntu, I press system/administration /Ubuntu Update manager. When I press the button to check whether there are new updates available or not, I get the following message:

“The repositories are not available or it has been impossible to connect due to network problems. If available, an older version  of the wrong index will be used. Otherwise the repository will be ignored. Check your network settings, and check that the repository’s web address you have in your preferences is right.

GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release The following signatures could not be verified because your public key is not available.: NO_PUBKEY 2EBC26B60C5A2783 Unable to get:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please
use apt-cdrom to get APT to read this CD. apt-get update can not be used to add new CDs

Unable to get cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to get APT to accept this CD. apt-get update  can not be used to add CDs

Unable to get [http://es.archive.ubuntu.com/ubuntu/dists/intrepid/Release](http://es.archive.ubuntu.com/ubuntu/dists/intrepid/Release)  Unable to find expected entry  mail/binary-i386/Packages in Meta-index file (malformed Release file?)

Some of the index files could not be dowloaded , have been ignored, or have been replaced by other older files”

Despite the fact I get this error, I get some updates I can download (it takes ages to download this updates). Howewer, once I have downloaded and installes these updates, if I close and open the Update manager, I get a message saying that I last checked whether  new updates are available 40 days ago.

I am a newbie, but I guess that the problem is related to Medibuntu, That is why I tried (several times) doing everything said on [https://help.ubuntu.com/community/Medibuntu;](https://help.ubuntu.com/community/Medibuntu;) but everytime I have tried to add the GPG key, I have got the following message:

“W: GPG Error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release The following signatures could not be verified due to your key is not available: NO_PUBKEY 2EBC26B60C5A2783

W: Unable to get  cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386
(20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use pt-cdrom to get APT to read this CD. apt-get update can not add new CDs

W: Unable to get  cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386
(20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please apt cdrom to get APT to read this CD. apt-get update  can not add new CDs

W: Unable to get
[http://es.archive.ubuntu.com/ubuntu/dists/intrepid/Release](http://es.archive.ubuntu.com/ubuntu/dists/intrepid/Release)  Unable to
find expected entry  mail/binary-i386/Packages in Meta-index file
(malformed Release file?)

E: Some index files could not be downloaded, have been skipped, or some older files have been used instead 

I do not know what CD is that message talking about, because I got the message without any CD in my computer. I tried using my Ubuntu CD, but I got the same message. Besides, I do not know what  apt -  cdrom is. 

I would like to say, that I do not have any troubles downloading packages using the synaptic or sudo apt-get install package (in fact the packages are downloaded and installed really quickly, so I don’t think there is a problem with my network settings). If I try to update my system by using sudo apt-get update, I get the same error message. I tried  changing the server in system/administration/ software sources but I could not fix the problem.

I would be grateful if someone could help to fix this problem

Thanks.

---

### Post by plucky on 2009-03-04
> W: Unable to get cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386
(20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz Please use pt-cdrom to get APT to read this CD. apt-get update can not add new CDs


It is trying to locate the install CD .Use the **Software Sources** and deselect the CD rom as a source.(See screenshot)


> GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release The following signatures could not be verified because your public key is not available.: NO_PUBKEY 2EBC26B60C5A2783 Unable to get:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz Please


From this [link](https://help.ubuntu.com/community/Medibuntu) use the command in a terminal to add the GPG key for the Medibuntu repository ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```


Good Luck

---

### Post by marticc on 2009-03-07
Hello, thanks for your answer.

I have done what you told me, but despite the fact that the problem with the CD ROM seems to be fixed, I have not solved the problem with the updates yet.

After running the command you told me to install the medibuntu key, I have got the following message (please note again that this is a translation into English of the original message. Sorry for any mistake I might have made)

"W: GPG ERROR: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release The following signatures could not be checked because your public key is not available: NO_PUBKEY 2EBC26B60C5A2783

W: Unable to get [http://es.archive.ubuntu.com/ubuntu/dists/intrepid/Release](http://es.archive.ubuntu.com/ubuntu/dists/intrepid/Release)  Unable to find expected entry  to mail/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files have not been downloaded, have been skipped or some other older files have been used instead."

If I try to update my ubuntu, I go to the update manager I press the check new updates button and I get the following message:

“The repositories are not available or it has been impossible to connect due to network problems. If available, an older version of the wrong index will be used. Otherwise the repository will be ignored. Check your network settings, and check that the repository’s web address you have in your preferences is right.

GPG ERROR: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release The following signatures could not be checked because your public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Unable to get [http://es.archive.ubuntu.com/ubuntu/dists/intrepid/Release](http://es.archive.ubuntu.com/ubuntu/dists/intrepid/Release)  Unable to find expected entry  to mail/binary-i386/Packages in Meta-index file (malformed Release file?)

Some index files have not been downloaded, have been skipped or  other older files have been used instead."

I hope someone can help me with this problem.

Thanks.

---

### Post by DougieFresh4U on 2009-03-07
Did you add the key using terminal as stated in post #2?
Try updating using the terminal
Applications>Accessories>Terminal
In terminal, one line at a time:
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a
```
Post what ever errors you are getting.
I find that there is better control over updating using terminal

EDIT: Also, under System>Administration>Software Sources, look under 'Third-Party Software' and see if there is a checkmark in the line with 'Medibuntu' in it

---

### Post by marticc on 2009-03-07
Hello, and Thanks for your answer.

I had added the key using the terminal as posted before

I have done everything you said but upgrading my Ubuntu (maybe I am wrong but as far as I know the second command is to upgrade my dist, and for the time being I am not interesting to move to 9.04).

When I run sudo apt-get update I ve got the same error:

"W: GPG ERROR: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release The following signatures could not be checked because your public key is not available: NO_PUBKEY 2EBC26B60C5A2783

W: Unable to get [http://es.archive.ubuntu.com/ubuntu/...trepid/Release](http://es.archive.ubuntu.com/ubuntu/...trepid/Release) Unable to find expected entry to mail/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files have not been downloaded, have been skipped or some other older files have been used instead."

When I run sudo apt-get -f install, no errors have been found. 
"Reading list of packages... done
Creating dependencies tree...done
Reading info about the status...done
0 updated, 0 will be installed, 0 to be deleted y 0 not updated."

When I run sudo dpkg --configure -a nothing has happened

"marti@ubuntu:~$ sudo dpkg --configure -a
 marti@ubuntu:~$ "

I have checked Medibuntu in the third party software section:

[http://packages.medibuntu.org/intrepid](http://packages.medibuntu.org/intrepid) free non-free
[http://packages.medibuntu.org/intrepid](http://packages.medibuntu.org/intrepid) free non-free (source code)

Thanks again.

---

### Post by plucky on 2009-03-07
Try this command ```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```


Can you also post your sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by marticc on 2009-03-09
Hello, thanks for your answer.

I have run the command:  wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
 And yet again I have found the same error

"W: Unable to get [http://es.archive.ubuntu.com/ubuntu/dists/intrepid/Release](http://es.archive.ubuntu.com/ubuntu/dists/intrepid/Release)  Unable to find expected entry  mail/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files have not been downloaded, have been ignored,
or other older files have been used instead."

PLease find below my sources.list

"# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security restricted main multiverse universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://es.archive.ubuntu.com/ubuntu/](http://es.archive.ubuntu.com/ubuntu/) intrepid mail
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main"

Thanks again for your time, and for your help.

---

### Post by plucky on 2009-03-09
> "W: GPG ERROR: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release The following signatures could not be checked because your public key is not available: NO_PUBKEY 2EBC26B60C5A2783

W: Unable to get [http://es.archive.ubuntu.com/ubuntu/...trepid/Release](http://es.archive.ubuntu.com/ubuntu/...trepid/Release) Unable to find expected entry to mail/binary-i386/Packages in Meta-index file (malformed Release file?)


You don't get the "GPG error" anymore.

The other error is caused by ```
deb http://es.archive.ubuntu.com/ubuntu/ intrepid mail
deb http://ppa.launchpad.net/openoffice-pkgs/ubuntu intrepid main"

``` in your sources.list file.
Edit the file ```
gksudo gedit /etc/apt/sources.list
``` and put a # in front of that line and remove the " from the second line.Then run ```
sudo apt-get update
``` and see what happens.

The PPA.launchpad.net will probably now complain about a GPG error so you will have to add the key for that repository or put a # also in front of that line.


Good Luck

---

### Post by marticc on 2009-03-09
Hello, I just want to let you know that your solution has worked PERFECTLY.

As you told me, I have put a # in front of the first line, and I have updated my Ubuntu with no problems. The " you advised me to remove, did not need to be removed (I added them in my latest post because I was  quoting what I had found out). By the way, no GPG error were reported when I updated the system.

To sum up: THANK YOU FOR YOUR HELP

---

### Post by plucky on 2009-03-09
> **marticc said:**
> Hello, I just want to let you know that your solution has worked PERFECTLY.

As you told me, I have put a # in front of the first line, and I have updated my Ubuntu with no problems. The " you advised me to remove, did not need to be removed (I added them in my latest post because I was  quoting what I had found out). By the way, no GPG error were reported when I updated the system.

To sum up: THANK YOU FOR YOUR HELP

You are welcome...


Enjoy:D

---

