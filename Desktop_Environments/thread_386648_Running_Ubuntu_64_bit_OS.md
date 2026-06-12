---
title: "Running Ubuntu 64 bit OS?"
date: 2007-03-17
forum: Desktop Environments
---

### Post by CarlosinFL on 2007-03-17
I just installed Ubuntu 64 bit on my work PC and well I have only one slight issue. The fact is that I used the CLI to install "[COLOR="DarkOrange"]Firefox 2.0.0.2[/COLOR]" via APT-GET.

Now that I have this installed, I do need "Flash 9" plugin however after a quick Google search it appears that there is no 64 port for the Flash plugin. Can someone tell me what the work around is for using a 64 bit OS and getting a Flash plugin to work.

Thanks for any help!

---

### Post by Sef on 2007-03-17
Check [RestrictedFormats/Flash]("https://help.ubuntu.com/community/RestrictedFormats/Flash").

---

### Post by CarlosinFL on 2007-04-13
[QUOTE=URL You Linked]Ubuntu 6.10 (Edgy Eft)

This method will install the latest flashplayer from the Ubuntu repositories, for Firefox, Konqueror, Mozilla, Epiphany and other browsers.

    *

      Install the package flashplugin-nonfree. You will need to have added the Multiverse component for this package to be present. See InstallingSoftware
    *

      Restart your web browser. Flash should now work.
[/QUOTE]

How do I get the Multiverse for my source list? When I cat my source.list, it appears to be the last few, no?

**My Source List**

[i]deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates multiverse
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-security multiverse
[/i]

---

### Post by CarlosinFL on 2007-04-13
Bump - anyone?

---

### Post by yatt on 2007-04-14
nspluginwrapper is the answer. It takes 32bit plugins, does something, and then they work in your 64-bit FF. Search the forum for it, and you should find a thread with a repo, and some instructions.

---

### Post by CarlosinFL on 2007-04-14
Found the thread you referred to and it worked perfectly.

---

