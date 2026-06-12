---
title: "Broken Packages, can not fix"
date: 2005-08-16
forum: Desktop Environments
---

### Post by raven on 2005-08-16
Feedback:
ubuntu hoary 5.04 I have GDM and KDE 3.4.2 I use KDE by default
superkaramba superkaramba_0.37-RC1-1_i386.deb got it from kde.look.org for sid

what happens is I want to install superkaramba_0.37-RC1-1_i386.deb
but could not cause dependence issues, ver in ubunutu repo are lower than need it,
so I downloded them from debian server all stable version
list of dependencies superkaramba needed I downloaded and installed

here is the list of dependencies:
libc6_2.3.2.ds1-22_i386.deb
libidn11_0.5.13-1.0_i386.deb
libqt3c102-mt_3.3.4-3_i386.deb
libfontconfig1_2.3.2-1_i386.deb
xmms_1.2.10+cvs20050209-2_i386.deb
then installed superkaramba_0.37-RC1-1_i386.deb all went fine and dandy

now when I use synaptic it tells me you have 6 broken packages
those are the packages that were replaced that are marked in red
in synaptic they are the old packages that are from ubuntu that are boken.
and when I try to do fix broken packages
I get this enormous list that I have to uninstall

here is the list to be removed:
build-essential will be removed
comerr-dev will be removed
g++ will be removed
g++-3.3 will be removed
kde will be removed
kdebase-dev will be removed
kdelibs4-dev will be removed
kdesdk will be removed
kspy will be removed
language-pack-en will be removed
language-pack-en-base will be removed
libart-2.0-dev will be removed
libarts1-dev will be removed
libartsc0-dev will be removed
libasound2-dev will be removed
libaudiofile-dev will be removed
libbz2-dev will be removed
libc6-dev will be removed
libc6-i686 will be removed
libcupsys2-dev will be removed
libesd0-dev will be removed
libexpat1-dev will be removed
libfontconfig1-dev will be removed
libfreetype6-dev will be removed
libgcrypt11-dev will be removed
libglib2.0-dev will be removed
libgnutls11-dev will be removed
libgpg-error-dev will be removed
libice-dev will be removed
libidn11-dev will be removed
libjpeg62-dev will be removed
libkrb5-dev will be removed
libmng-dev will be removed
libogg-dev will be removed
libopenexr-dev will be removed
libpcap0.8-dev will be removed
libpcre3-dev will be removed
libpng12-dev will be removed
libqt3-mt-dev will be removed
libsasl2-dev will be removed
libsm-dev will be removed
libsqlite3-dev will be removed
libstdc++5-3.3-dev will be removed
libtiff4-dev will be removed
libvorbis-dev will be removed
libx11-dev will be removed
libxcursor-dev will be removed
libxext-dev will be removed
libxft-dev will be removed
libxi-dev will be removed
libxinerama-dev will be removed
libxml2-dev will be removed
libxmu-dev will be removed
libxrandr-dev will be removed
libxrender-dev will be removed
libxslt1-dev will be removed
libxt-dev will be removed
libxv-dev will be removed
locales will be removed
lsb will be removed
ubuntu-base will be removed
ubuntu-desktop will be removed
xlibmesa-gl-dev will be removed
xlibmesa-glu-dev will be removed
xlibs-static-dev will be removed
zlib1g-dev will be removed

I am not pressing apply on all of these, it seems removing the system lol
when I try to uninstall any of the boken packages above 
or any of the dependencies that I installed I get the list to be removed above where I have to remove 100 of packages.
ex: "I want to uninstall libc6_2.3.2.ds1-22_i386.deb 1 of the new packages" or
"I want to remove libc6-i686 the original ubuntu package (now in red in synaptic)"
I get the remove list of around 100 of packages

NB: if you need more info or feedback please do ask
this is my main system and do not have an other
any help is appreciated

---

### Post by varunus on 2005-08-16
Hate to break it to you, but you're going to have to reinstall ubuntu, I think.  Or try and uninstall superkaramba and downgrade the packages you got from debian.

Some of those packages you installed from debian are system-critical (especially libc6) and some programs need a SPECIFIC version to run properly.  This is why everyone says not to mix Debian and Ubuntu...

---

### Post by raven on 2005-08-16
Thanx for the reply
as I mentioned any of the packages even superkaramba
that I try to uninstall through synaptic
will give the remove list of 100 of packages.
are you sure it is a dead case
or there is some other way ?

---

### Post by varunus on 2005-08-16
Even uninstalling superkaramba wants to remove all of those?  Hm...

Well, can you try to downgrade superkaramba?  Click it in synaptic, and choose "package->force version" and choose the ubuntu version...

Then try the same with all the packages you got from debian...This might be able to fix your system.

If you want the newest versions of things:
Are you using Ubuntu Backports?  These guys upgrade all of the Ubuntu packages in a safe way...They have superkaramba 0.36 as opposed to 0.35 like in hoary standard...Here's instructions on how to enable the repositories:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

They may not have the best versions, but they're more up-to-date than regular hoary, usually.

---

### Post by raven on 2005-08-16
my back ports are the same as in your link
## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

when I search in synaptic to superkaramba I get only the ver that is installed on my box 0.37 which I got from kde-look.org it was for Debian
I can not get any other versions, so in a way I can not force downgrade
when I try to remove it as always will give me the remove list mentioned earlier

EDIT: my mistake I understand whant you mean by downgrading,
I see all versions now
but unfortunatly when I choose the ubuntu version, I force it
will accept but ask me the remove list again

---

### Post by varunus on 2005-08-16
Can you try:

Accept the remove packages when you downgrade superkaramba, but don't click apply yet.

Then, downgrade all of the other packages that you got from debian to their ubuntu versions.

Then, try to unmark all of the packages marked for removal (synaptic's marked changes tab will show you these).

If this works, you can go ahead and click apply...but if it won't let you unmark the removal-marked packages, then I don't know what you can do aside from reinstall...Sorry.

---

### Post by raven on 2005-08-16
thanx varunus
Yes I got to that moment when you feel you're at the end of the wire
the only way is to reinstall system
the whole system is uninstalled now as I had to click apply
1 question how do I reinstall the system without loosing my home
what I mean, when I clicked apply it removed all  essentials packages
synaptic is off, I have only terminal working my sudo is out, I had to use su
can I rebuid from the ashes lol ?
I did not boot yet, my browser are working
what kind of packeges shoud I reinstall that contains the base to rebuild ?

---

### Post by varunus on 2005-08-17
Try installing the "ubuntu-desktop" package.  This should get you back.

Good luck...

---

### Post by raven on 2005-08-17
at this moment I am with a system that is dead, 
can not log in either with root or my own user and for sure no X
the only hope I have, if there is a way to rebuild through a live CD
is that a possible solution ?
if not I am saving my home file through live cd and reinstall sys.

FYI: It was my mistake, you told me to uncheck all the essentials packages
I did this the first time, then something happen that I had to do it again
but missed apt-utils, after that I was stuck with a sys with no apt-get ability
you can imagine the horror...  ](*,) 

thanx for the replies

---

### Post by varunus on 2005-08-23
Sorry for all of your problems; I think you should try and use a liveCD (ubuntu or knoppix or whatever) and get all of your essential files off the computer...you'll have to reinstall after that.

Just remember in the future not to mix debian and Ubuntu packages...they really should a warning for it or something.

Sorry for all of the problems.

---

