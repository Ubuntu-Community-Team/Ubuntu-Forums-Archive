---
title: "Command to find out the dependencies of a package"
date: 2016-11-11
forum: Desktop Environments
---

### Post by williepabon on 2016-11-11
Hi:

I recently installed Musescore directly from the developer website. I need to know all the software this package depends on.  How do I get to  know this?
Thanks.

---

### Post by howefield on 2016-11-11
Try..

```
apt-cache rdepends musescore
```

---

### Post by williepabon on 2016-11-11
**howefield:**

Thanks for answering, but maybe I didn't explain myself with enough clarity. What I'm looking is a list of all the libraries that that need to be available in the system for the application to function. I want to be able to run a terminal command that will list the same list that shows when I go to synaptics package manager, select the application and in the menu choose package properties --> Dependecies.
wp

---

### Post by howefield on 2016-11-11
Then..

```
apt-cache show musescore
```

should do it ?

Could always grep for Depends to filter out the rest of the output.

---

### Post by Dennis N on 2016-11-11
> I need to know all the software this package depends on...
What I'm looking is a list of all the libraries that that need to be available.

More information would help:

Is this from a .deb file? How did you install it?

Do you want to list the needed libraries, or the packages that provide the libraries?

---

### Post by ian-weisser on 2016-11-11
> **williepabon said:**
> I need to know all the software this package depends on.

If installing a deb from the musescore website (or, even better, the Ubuntu repos), your Ubuntu system learns the dependencies from the Debian control file within the .deb.
Apt will automatically install all dependencies for you while it installs musescore. That's why we use debs and apt.

If you are installing using any other method, then you must ask the Musescore project for the list of dependencies...and compatible versions of those dependencies.
Your Ubuntu system is good, but not psychic.

If you want an estimate of the dependencies, based on the musescore package in the ubuntu repos, simply ask apt: 'apt depends musescore'

---

### Post by williepabon on 2016-11-12
**Dennis N:**
Thanks for your comments. As I said in my last post, "[COLOR=#000000] [/COLOR][COLOR=#000000] I want to be able to run a terminal command that will list the same list that shows when I go to synaptics package manager, select the application and in the menu choose package properties --> Dependecies. Don't know if this is possible. If I do a terminal command, I would be able to print such a list..Thanks.
[/COLOR]

---

### Post by williepabon on 2016-11-12
howefield:
You gave me the idea.
> apt-cache depends musescore
is the command that I wanted. Thanks.
wp

---

### Post by howefield on 2016-11-12
Cool, feel free to mark the thread as solved :)

---

### Post by steeldriver on 2016-11-12
Note that 

```

apt-cache depends

```

is not recursive by default - i.e. it will only list the "first level" of dependencies. You can add --recurse to the command to drill down to dependencies-of-dependencies-of-dependencies - but in practice it's rarely useful in my experience

```

apt-cache depends --recurse musescore

```

---

### Post by ian-weisser on 2016-11-12
The apt command will also do it (16.04 and later).
```
apt depends musescore
apt depends --recurse musescore
```

---

### Post by SeijiSensei on 2016-11-12
I'd just use "dpkg -s packagename".  It returns a complete inventory of the .deb like this:
```

$ dpkg -s firefox

Package: firefox
Status: install ok installed
Priority: optional
Section: web
Installed-Size: 109878
Maintainer: Ubuntu Mozilla Team <ubuntu-mozillateam@lists.ubuntu.com>
Architecture: amd64
Version: 50.0~b11+build1-0ubuntu0.14.04.1
Replaces: kubuntu-firefox-installer
Provides: gnome-www-browser, iceweasel, www-browser
**Depends**: lsb-release, libasound2 (>= 1.0.16), libatk1.0-0 (>= 1.12.4), libc6 (>= 2.17), libcairo-gobject2 (>= 1.10.0), libcairo2 (>= 1.10.0), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.78), libfontconfig1 (>= 2.9.0), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0 (>= 2.31.8), libgtk-3-0 (>= 3.4), libgtk2.0-0 (>= 2.14), libpango-1.0-0 (>= 1.22.0), libpangocairo-1.0-0 (>= 1.14.0), libstartup-notification0 (>= 0.8), libstdc++6 (>= 4.6), libx11-6, libx11-xcb1, libxcb-shm0, libxcb1, libxcomposite1 (>= 1:0.3-1), libxdamage1 (>= 1:1.1), libxext6, libxfixes3, libxrender1, libxt6
Recommends: xul-ext-ubufox, libcanberra0, libdbusmenu-glib4, libdbusmenu-gtk4
Suggests: fonts-lyx
Conffiles:
 /etc/firefox/syspref.js 09e457e65435a1a043521f2bd19cd2a1
 /etc/apport/blacklist.d/firefox ee63264f847e671832d42255912ce144
 /etc/apport/native-origins.d/firefox 7c26b75c7c2b715c89cc6d85338252a4
 /etc/apparmor.d/usr.bin.firefox f54f7a43361c7ecfa3874abca2f292cf
Description: Safe and easy web browser from Mozilla
 Firefox delivers safe, easy web browsing. A familiar user interface,
 enhanced security features including protection from online identity theft,
 and integrated search let you get the most out of the web.
Xul-Appid: {ec8030f7-c20a-464f-9b0e-13a3a9e97384}

```

---

