---
title: "update manager help"
date: 2009-02-12
forum: General Help
---

### Post by mikeonthebeach on 2009-02-12
i have ubuntu 8.10 and my update manager shows an error message everytime i start it.

GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783GPG error: [http://ubuntu.cafuego.net](http://ubuntu.cafuego.net) intrepid-cafuego Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 81600957AF425CB5Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. 

i have no idea what to do can some1 please help me??:confused:

---

### Post by plucky on 2009-02-12
> i have no idea what to do can some1 please help me?

Open a terminal input this command ```
cat /etc/apt/sources.list
``` and post output to the forums.

---

### Post by mikeonthebeach on 2009-02-13
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main multiverse universe restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) intrepid-security universe main multiverse restricted #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-updates universe main multiverse restricted #Added by software-properties
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"
deb [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) intrepid-cafuego broadcom
deb-src [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) intrepid-cafuego broadcom
mike@Mike-Linux:~$ 


a bunch of more **** popped up

---

### Post by plucky on 2009-02-13
Tip: When pasting large quantities of text to the forum,if you use a [noparse]```
[/noparse] bracket at the start of the text and a [noparse]
```[/noparse] at the end of the text,it is much easier to read.


You have Gutsy and Intrepid Repositories mixed up in your sources.list,which is strange because you shouldn't have been able to upgrade from Gutsy to Intrepid.

How did you upgrade? If you did go from Gutsy to Intrepid,you should think of doing a clean install of Intrepid.

To workaround your problem:-

You need to edit the sources.list file and put a # in front of every line that has "gutsy" in it.Also put a # on the lines that start with "deb cdrom".

See this link for adding the [Medibuntu Repository](https://help.ubuntu.com/community/Medibuntu) and GPG key.

See this link for adding the [Wine repository](http://www.winehq.org/download/deb) and GPG key.

Not sure about the cafuego key so I would comment that out for the time being.


Post back if you have any more problems.


Good Luck

---

### Post by plucky on 2009-02-13
This command will get you the key for cafuego ```
wget -q http://ubuntu.cafuego.net/cafuego.gpg -O- | sudo apt-key add - && sudo apt-get update
```.

Just tried it and it works.


Good luck

---

### Post by sarah28 on 2009-02-18
> **plucky said:**
> Open a terminal input this command ```
cat /etc/apt/sources.list
``` and post output to the forums.
Please help!  I am a complete novice and have a similar problem with the update manager on my sons new laptop.  I have run the command that you recommended to mikeonthebeach,  and the following list is what I got:


tom@tom-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb http:download.skype.com/linux/repos/debian/ stable non-free
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main

As you can see the problem seems to be slightly different so if you can help I would really appreciate it.
Many thanks,
Sarah

---

### Post by plucky on 2009-02-19
What is the problem?

What errors do you get?

Go to **System > Administration > Software Sources** and un-tick **CDrom.**

All you have given us is your sources.list, what we need is the error you are seeing and what you are doing to get the error.

Also this line is incorrect ```
deb http:download.skype.com/linux/repos/debian/ stable non-free
```.You should edit the file and put a # at the beginning of the line.

For **Skype** use the [Medibuntu Repository](https://help.ubuntu.com/community/Medibuntu)

Good Luck

---

### Post by sarah28 on 2009-02-19
Hi,
[COLOR="Navy"]I've unclicked CDRom and I received the following error:[/COLOR]

W: GPG error: [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

[COLOR="Navy"]My original problem is that every time I open update manager I get an error and it will not complete the update.  The error is exactly the same as the one above.

I think I will need more than luck, as I have no clue what I am doing!
[/COLOR]
If you are able to help, I will be most grateful.
Many thanks,
Sarah

---

### Post by plucky on 2009-02-19
> W: GPG error: [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Those errors are warnings and should not stop you updating and installing packages.


To add a key for the Medibuntu repository,open a terminal **Applications > Accessories > Terminal** and copy and paste this command ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

For the debian multimedia key, you need to go [http://www.debian-multimedia.org/faq.php#q1](http://www.debian-multimedia.org/faq.php#q1)  and download the debian multimedia keyring .deb file and install it using the command in a terminal ```
dpkg -i debian-multimedia-keyring
```

I would be careful about using the debian repositories as,although Ubuntu is debian based,not all the debian packages will be compatible.


Good Luck

---

### Post by sarah28 on 2009-02-19
Hi,
Thank you for taking the time to help me.  I have followed the instructions you have given me and hopefully I am nearly there!
After downloading the debian multimedia key I got the following message:

W: GPG error: [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems
tom@tom-laptop:~$ dpkg -i debian-multimedia-keyring
dpkg: requested operation requires superuser privilege
tom@tom-laptop:~$ 

What does that mean?
Many thanks,
Sarah

---

### Post by Mercury_Alpha on 2009-02-19
> **sarah28 said:**
> 
What does that mean?
Many thanks,
Sarah

That means you need to use sudo at the beginning of the line. the "su" in sudo stands for "super user." It's a command that temporarily invokes super user privileges. So it will look like

```
sudo dpkg -i debian-multimedia-keyring
```

It will prompt you to enter your password, which should be the one you log into Ubuntu with. Type it out (no characters will show up) and hit Enter.

---

### Post by plucky on 2009-02-19
> tom@tom-laptop:~$ dpkg -i debian-multimedia-keyring
dpkg: requested operation requires superuser privilege


You need super user privileges. Use ```
sudo dpkg -i debian-multimedia-keyring
``` and input your login password,should do the trick.


Good Luck

---

### Post by sarah28 on 2009-02-19
Thank you so very much. 
It has worked and I can check for updates using the update manager and no errors occur.  Yippee!!!!

The only thing that does not look quite right is that when I entered the command, I got the following message:

dpkg: error processing debian-multimedia-keyring (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 debian-multimedia-keyring
tom@tom-laptop:~$ 

Is it anything to worry about?

Thank you again I really appreciate it,
Sarah

---

### Post by plucky on 2009-02-20
> **sarah28 said:**
> Thank you so very much. 
It has worked and I can check for updates using the update manager and no errors occur.  Yippee!!!!

The only thing that does not look quite right is that when I entered the command, I got the following message:

dpkg: error processing debian-multimedia-keyring (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 debian-multimedia-keyring
tom@tom-laptop:~$ 

Is it anything to worry about?

Thank you again I really appreciate it,
Sarah

That looks like a problem with the install.But if you aren't getting the previous error about the GPG then the key must have been installed.

In a terminal use ```
sudo apt-get update
``` and post output if any errors.

---

### Post by sarah28 on 2009-02-20
No errors so hopefully alls well that ends well.

Thanks again for taking the time to help me.  I am going to buy a book to read up on all that is Ubuntu.  I might know what I am doing then.

Many thanks,
Sarah

---

