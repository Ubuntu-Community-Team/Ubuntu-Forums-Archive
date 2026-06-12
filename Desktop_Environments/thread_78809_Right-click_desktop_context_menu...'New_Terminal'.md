---
title: "Right-click desktop context menu...'New Terminal'"
date: 2005-10-19
forum: Desktop Environments
---

### Post by bacchus_3 on 2005-10-19
Hi All,

I'm new to these forums so hope you could welcome me with a reply to this question.

In Hoary, the right-click mouse context menu includes 'New Terminal'.  In Breezy, it seems like the development team opted to remove it.  Is there a way to put it back?  I've been looking around the settings options in Breezy but I've failed to see it if there should be one.

By the way,  I was able to successfuly upgrade my distro thru 'apt-get' and I'm not having problems.  I'm using an HP Compaq Presario M2215.  I've set-up everything except for the built-in modem.  All is good...:p

---

### Post by AgenT on 2005-10-19
This has been made into its own package. Install package nautilus-open-terminal and you will have the New Terminal action. Even better, it now allows you to open a terminal in any folder you are viewing in Nautilus!

---

### Post by bacchus_3 on 2005-10-19
that's werid...why was it done that way?  anyway, I'll try to install that package.  Thanks for the help.

---

### Post by Murgle on 2005-10-19
I would also reccomend as a handy tip for the terminal, adding a keyboard shortcut for it.  go to System -> Preferences -> Keyboard Shortcuts. at the end of the Desktop section, the first, there is the run a terminal click on the shortcut column and make one up, I use Crtl + Alt + T

---

### Post by manicka on 2005-10-19
[QUOTE=Murgle]I would also reccomend as a handy tip for the terminal, adding a keyboard shortcut for it.  go to System -> Preferences -> Keyboard Shortcuts. at the end of the Desktop section, the first, there is the run a terminal click on the shortcut column and make one up, I use Crtl + Alt + T[/QUOTE]

That's a nice tip. I settled for <alt>t

thanks :D

---

### Post by gushy on 2005-10-19
Excellent.  Now I can stop creating new folders by mistake. :rolleyes:

---

### Post by bionnaki on 2005-10-19
[QUOTE=AgenT]This has been made into its own package. Install package nautilus-open-terminal and you will have the New Terminal action. Even better, it now allows you to open a terminal in any folder you are viewing in Nautilus![/QUOTE]


thanks! exactly what I wanted :razz:

---

### Post by rsankuratri on 2005-10-20
It would be very helpful if you could also describe the installation process for the nautilus-open-terminal.

Thanks in advance

---

### Post by Efwis on 2005-10-20
[QUOTE=rsankuratri]It would be very helpful if you could also describe the installation process for the nautilus-open-terminal.

Thanks in advance[/QUOTE]

sudo apt-get install nautilus-open-terminal

---

### Post by rsankuratri on 2005-10-20
Thanks for the reply Efwis.  But it looks like the US archives are down :???:

---

### Post by Efwis on 2005-10-20
[QUOTE=rsankuratri]Thanks for the reply Efwis.  But it looks like the US archives are down :???:[/QUOTE]
hmm, is your sources.list set up properly?

I just did it with no problems.

---

### Post by rsankuratri on 2005-10-20
The error message I receive is
=========================================
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:) 404 Not Found [IP: 130.239.18.142 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 130.239.18.142 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 130.239.18.142 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 130.239.18.142 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz:) 404 Not Found [IP: 130.239.18.142 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz:) 404 Not Found [IP: 130.239.18.142 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz:) 404 Not Found [IP: 130.239.18.142 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz:) 404 Not Found [IP: 130.239.18.142 80]
==============================================

Are these not valid anymore?  Do you have them in your sources.lst file?


====================================
[B]
Update[/B]

The ones that are working did bring the pkg nautilus-open-terminal.  The version is 0.4 Is that right.  The nautilus-open-terminal website said that 0.6 was the latest.

---

### Post by armeck on 2005-10-20
[quote=AgenT]This has been made into its own package. Install package nautilus-open-terminal and you will have the New Terminal action. Even better, it now allows you to open a terminal in any folder you are viewing in Nautilus![/quote]
Right clicking on a directory and the terminal opening with you already in that directory is simply brilliant.

---

### Post by Efwis on 2005-10-20
[QUOTE=rsankuratri]The error message I receive is
=========================================
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz:) 404 Not Found [IP: 130.239.18.142 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 130.239.18.142 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 130.239.18.142 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 130.239.18.142 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz:) 404 Not Found [IP: 130.239.18.142 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz:) 404 Not Found [IP: 130.239.18.142 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz:) 404 Not Found [IP: 130.239.18.142 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz:) 404 Not Found [IP: 130.239.18.142 80]
==============================================

Are these not valid anymore?  Do you have them in your sources.lst file?


====================================
[B]
Update[/B]

The ones that are working did bring the pkg nautilus-open-terminal.  The version is 0.4 Is that right.  The nautilus-open-terminal website said that 0.6 was the latest.[/QUOTE]

This is what your sources.list should look like. feel free to edit yours and set it up like mine with a copy and paste.

to do so open terminal and type/copy and paste the following
```

sudo gedit /etc/apt/sources.list
```

then copy and paste this entire listing by selecting all and then paste it.
```

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


# deb-src http://dk.archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://dk.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb-src http://dk.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://dk.archive.ubuntu.com/ubuntu breezy universe main restricted multiverse
# deb-src http://dk.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://dk.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://dk.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe main restricted multiverse
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```
after doing that go back to terminal and type the following
```

sudo apt-get update
```
Then try it, it will work, the back ports aren't operational yet. 0.6 will probably be added after the backports are up if they decide to do that, otherwise 0.6 will more then likely be in dapper if there isn't a newer version out at that time.

---

### Post by bvc on 2005-10-20
```
#!/bin/bash
cd $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
gnome-terminal
```saving that as ~/.gnome2/nautilus-scripts/Open Terminal acheives the same, well except you have another menuitem to go to (Scripts).

---

