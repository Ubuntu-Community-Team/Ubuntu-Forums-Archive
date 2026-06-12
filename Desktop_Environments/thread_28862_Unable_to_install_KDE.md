---
title: "Unable to install KDE"
date: 2005-04-21
forum: Desktop Environments
---

### Post by Trickyphillips on 2005-04-21
Hello all... I'm having some trouble installing KDE. When I used apt-get, I got:

> root@ubuntu:/home/ron/Desktop # apt-get install kde
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kde: Depends: kdesdk but it is not going to be installed
E: Broken packages
root@ubuntu:/home/ron/Desktop #
 

So, I try installing kdesdk, but during ./configure, I get:

> checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!


So this puts me in an endless loop. You can't install KDE unless you first install kdesdk, but you can't install kdesdk unless KDE is installed. ](*,)

---

### Post by lorap on 2005-04-22
hi friend.
donno if it's the reason but it could be it's one of causes.
open synaptic package manager,go to the repositories and mark all checkboxes possible regardless the warnings then press ok.after what you'll be present again with synaptic window.press reload button after what you'll probably be able install kde desktop environment.
have a nice day.
pavel

---

### Post by clb137 on 2005-04-22
Make sure that you have added the extra repositires then use synaptic to install 'kde

---

### Post by Trickyphillips on 2005-04-22
[QUOTE=clb137]Make sure that you have added the extra repositires then use synaptic to install 'kde[/QUOTE]
 Here's my current sources.list:

> deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main


I've been doing fine with it. Should I add another repository?

---

### Post by derrick1985 on 2005-04-22
[QUOTE=Trickyphillips]Here's my current sources.list:



I've been doing fine with it. Should I add another repository?[/QUOTE]
 No, KDE in Ubuntu is Kubuntu. If you want that, you have to type:

sudo apt-get install kubuntu-desktop

I did it yesteday, it works fine. Now instead of 2 or 3 different programs for everything, i got 6.

And during the install it will ask you if you want to use KDM or GDM as your default login manager (debconf) i just stuck with gdm.

EDIT: You might want to add the universe repositorys too, but I don't think they are needed. Just take out the # symbol and do an sudo apt-get update

---

### Post by Trickyphillips on 2005-04-22
[QUOTE=derrick1985]No, KDE in Ubuntu is Kubuntu. If you want that, you have to type:

sudo apt-get install kubuntu-desktop

I did it yesteday, it works fine. Now instead of 2 or 3 different programs for everything, i got 6.

And during the install it will ask you if you want to use KDM or GDM as your default login manager (debconf) i just stuck with gdm.

EDIT: You might want to add the universe repositorys too, but I don't think they are needed. Just take out the # symbol and do an sudo apt-get update[/QUOTE]

Everything's working perfectly now! Thanks a lot, Derrik!  :)

---

