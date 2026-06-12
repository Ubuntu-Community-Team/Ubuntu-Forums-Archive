---
title: "Installing Fluxbox"
date: 2005-10-08
forum: Desktop Environments
---

### Post by Comrade on 2005-10-08
I uncommented the sources in my /etc/apt/sources.list file, and I did an apt-get install fluxbox. However, I am struck by the following error:
> Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  fluxbox: Depends: menu (>= 2.1.19) but it is not going to be installed
  libltdl3: Depends: libc6 (>= 2.3.5-1) but 2.3.2.ds1-22 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution). I then tried apt-get install menu, but it gives the same error for libc6. How am I supposed to get libc6 version 2.3.5-1, if it is not in my sources, and I can't find any sources for it?

---

### Post by DJ_Max on 2005-10-08
Post your sources.list file.

---

### Post by Comrade on 2005-10-08
*saketh@ubuntu:~$ cat /etc/apt/sources.list*
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

---

### Post by Comrade on 2005-10-08
I searched around, and I found that other people also had problems with libc6. I can't get Enlightenment to work either.

---

### Post by DJ_Max on 2005-10-08
[QUOTE=Comrade]I searched around, and I found that other people also had problems with libc6. I can't get Enlightenment to work either.[/QUOTE]
I found the same. I installed both Fluxbox and E17, but from source. I don't know whats up with this dependency problem. Doing some more searching on these forums and the Wiki may yeild some info.

---

### Post by Comrade on 2005-10-08
[quote=DJ_Max]I found the same. I installed both Fluxbox and E17, but from source. I don't know whats up with this dependency problem. Doing some more searching on these forums and the Wiki may yeild some info.[/quote]
Did you get Fluxbox and e17 to work? Can you tell me how you did it?

Further inquiries lead me to believe that the version of libc6 that comes with Ubuntu is too old. But apt-get update doesn't update it for some reason, and Googling for the library does not yield any results that are usable under Ubuntu.

---

### Post by DJ_Max on 2005-10-08
[QUOTE=Comrade]Did you get Fluxbox and e17 to work? Can you tell me how you did it?

Further inquiries lead me to believe that the version of libc6 that comes with Ubuntu is too old. But apt-get update doesn't update it for some reason, and Googling for the library does not yield any results that are usable under Ubuntu.[/QUOTE]
The version of libc6 is not old, to say the least, but there's a dependency issue with the binaries. The package is, for some odd reason, requiring a version of libc6 not included with Ubuntu. With that said, I wouldn't touch libc, it will only cause problems.

[Fluxbox](http://fluxbox.sourceforge.net/) is really easy to install. Grab the 0.9.14 source. Extract, do the simple ./configure && make && sudo make install.

And in in /usr/share/xsessions
create a file called fluxbox.desktop
```

[Desktop Entry]
Encoding=UTF-8
Name=FLUXBOX
Comment=This session logs you into FLUXBOX
Exec=/usr/bin/fluxbox
Terminal=False
Type=Application

[Window Manager]
SessionManaged=true

```

Note that *Exec=/usr/bin/fluxbox* will depend on where you installed Fluxbox. It could be /usr/local/bin/fluxbox

As far as E17, it hasn't been released yet and is only available via CVS since it's in heavy development. There's a thread with a script on building it, but it's not for the  Linux newbie.

---

### Post by Comrade on 2005-10-08
That's odd. Suddenly Synaptic works and Fluxbox/Blackbox both install without a hitch. Well, problem solved I suppose. I'm still interested in e17, though. Perhaps I should have a look at the Elive thing.

---

