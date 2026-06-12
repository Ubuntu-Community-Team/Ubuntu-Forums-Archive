---
title: "Installing Kubuntu, got these update errors"
date: 2012-02-13
forum: Desktop Environments
---

### Post by murderd2death on 2012-02-13
i got an error at the end of the install in the terminal, Kubuntu was installed and i can log into it and browse the net but anytime i try to update anything i get these errors.

```
The following packages have unmet dependencies:

libkactivities6: Depends: libkactivities-bin (= 4:4.8.0-0ubuntu1~oneiric1~ppa1) but it is not installed
plasma-desktop: Depends: libkephal4abi1 (= 4:4.8.0b-0ubuntu1~oneiric1~ppa2) but 4:4.8.0b-0ubuntu1~oneiric1~ppa2 is installed
                Depends: libkworkspace4abi1 (= 4:4.8.0b-0ubuntu1~oneiric1~ppa2) but 4:4.8.0b-0ubuntu1~oneiric1~ppa2 is installed
                Depends: libplasmagenericshell4 (= 4:4.8.0b-0ubuntu1~oneiric1~ppa2) but 4:4.8.0b-0ubuntu1~oneiric1~ppa2 is installed
                Depends: libtaskmanager4abi3 (= 4:4.8.0b-0ubuntu1~oneiric1~ppa2) but 4:4.8.0b-0ubuntu1~oneiric1~ppa2 is installed
                Depends: plasma-widgets-workspace (= 4:4.8.0b-0ubuntu1~oneiric1~ppa2) but 4:4.8.0b-0ubuntu1~oneiric1~ppa2 is installed
                Depends: libkactivities-bin but it is not installed
plasma-netbook: Depends: libkephal4abi1 (= 4:4.8.0b-0ubuntu1~oneiric1~ppa2) but 4:4.8.0b-0ubuntu1~oneiric1~ppa2 is installed
                Depends: libplasmagenericshell4 (= 4:4.8.0b-0ubuntu1~oneiric1~ppa2) but 4:4.8.0b-0ubuntu1~oneiric1~ppa2 is installed
                Depends: plasma-widgets-workspace (= 4:4.8.0b-0ubuntu1~oneiric1~ppa2) but 4:4.8.0b-0ubuntu1~oneiric1~ppa2 is installed
                Depends: libkactivities-bin but it is not installed

```

im also told to take off any third party repositories for software updates and i did and i get the same result.

someone help, please.

---

### Post by drmrgd on 2012-02-13
> **murderd2death said:**
> i got an error at the end of the install in the terminal, Kubuntu was installed and i can log into it and browse the net but anytime i try to update anything i get these errors.

```
The following packages have unmet dependencies:

libkactivities6: Depends: libkactivities-bin (= 4:4.8.0-0ubuntu1~oneiric1~ppa1) but it is not installed
plasma-desktop: Depends: libkephal4abi1 (= 4:4.8.0b-0ubuntu1~oneiric1~ppa2) but 4:4.8.0b-0ubuntu1~oneiric1~ppa2 is installed
                Depends: libkworkspace4abi1 (= 4:4.8.0b-0ubuntu1~oneiric1~ppa2) but 4:4.8.0b-0ubuntu1~oneiric1~ppa2 is installed
                Depends: libplasmagenericshell4 (= 4:4.8.0b-0ubuntu1~oneiric1~ppa2) but 4:4.8.0b-0ubuntu1~oneiric1~ppa2 is installed
                Depends: libtaskmanager4abi3 (= 4:4.8.0b-0ubuntu1~oneiric1~ppa2) but 4:4.8.0b-0ubuntu1~oneiric1~ppa2 is installed
                Depends: plasma-widgets-workspace (= 4:4.8.0b-0ubuntu1~oneiric1~ppa2) but 4:4.8.0b-0ubuntu1~oneiric1~ppa2 is installed
                Depends: libkactivities-bin but it is not installed
plasma-netbook: Depends: libkephal4abi1 (= 4:4.8.0b-0ubuntu1~oneiric1~ppa2) but 4:4.8.0b-0ubuntu1~oneiric1~ppa2 is installed
                Depends: libplasmagenericshell4 (= 4:4.8.0b-0ubuntu1~oneiric1~ppa2) but 4:4.8.0b-0ubuntu1~oneiric1~ppa2 is installed
                Depends: plasma-widgets-workspace (= 4:4.8.0b-0ubuntu1~oneiric1~ppa2) but 4:4.8.0b-0ubuntu1~oneiric1~ppa2 is installed
                Depends: libkactivities-bin but it is not installed

```

im also told to take off any third party repositories for software updates and i did and i get the same result.

someone help, please.

You might try the good old standby:

```
sudo apt-get update
```

followed by:

```
sudo apt-get install -f
```

Try that, and if you still get errors, please give us the output and we'll work on the next step.

---

### Post by murderd2death on 2012-02-13
> **drmrgd said:**
> You might try the good old standby:

```
sudo apt-get update
```

followed by:

```
sudo apt-get install -f
```

Try that, and if you still get errors, please give us the output and we'll work on the next step.

This is what i get after that

```
dpkg: error processing /var/cache/apt/archives/libkactivities-bin_4%3a4.8.0-0ubuntu1~oneiric1~ppa1_i386.deb (--unpack):
 trying to overwrite '/usr/share/kde4/services/kactivitymanagerd.desktop', which is also in package kde-runtime-data 4:4.7.4-0ubuntu0.1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libkactivities-bin_4%3a4.8.0-0ubuntu1~oneiric1~ppa1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by murderd2death on 2012-02-14
bump

i tried removing kubuntu-desktop and this is what i get as well
```
 sudo apt-get remove kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libkactivities6 : Depends: libkactivities-bin (= 4:4.8.0-0ubuntu1~oneiric1~ppa1) but it is not going to be installed
 plasma-desktop : Depends: libkactivities-bin but it is not going to be installed
 plasma-netbook : Depends: libkactivities-bin but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by drmrgd on 2012-02-14
> **murderd2death said:**
> This is what i get after that

```
dpkg: error processing /var/cache/apt/archives/libkactivities-bin_4%3a4.8.0-0ubuntu1~oneiric1~ppa1_i386.deb (--unpack):
 trying to overwrite '/usr/share/kde4/services/kactivitymanagerd.desktop', which is also in package kde-runtime-data 4:4.7.4-0ubuntu0.1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libkactivities-bin_4%3a4.8.0-0ubuntu1~oneiric1~ppa1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It looks like the problem might be from dpkg complaining about overwriting an existing package. For some reason, there's a hang up between repositories for KDE 4.7 and 4.8 maybe? Try following the instructions in this link to forcibly overwrite kactivitymanagerd.desktop with  libkactivities-bin.

Hope that helps!

---

### Post by murderd2death on 2012-02-14
> **drmrgd said:**
> It looks like the problem might be from dpkg complaining about overwriting an existing package. For some reason, there's a hang up between repositories for KDE 4.7 and 4.8 maybe? Try following the instructions in this link to forcibly overwrite kactivitymanagerd.desktop with  libkactivities-bin.

Hope that helps!

wheres the link at?

---

### Post by drmrgd on 2012-02-14
Ooops!  Forgot to paste it in.  It's here:

[http://www.webupd8.org/2011/02/fix-dpkg-error-trying-to-overwrite-x.html](http://www.webupd8.org/2011/02/fix-dpkg-error-trying-to-overwrite-x.html)

Sorry about that!

---

### Post by murderd2death on 2012-02-20
> **drmrgd said:**
> Ooops!  Forgot to paste it in.  It's here:

[http://www.webupd8.org/2011/02/fix-dpkg-error-trying-to-overwrite-x.html](http://www.webupd8.org/2011/02/fix-dpkg-error-trying-to-overwrite-x.html)

Sorry about that!

so what directory to I put for something that hasn't been installed yet?

---

### Post by murderd2death on 2012-02-22
> **drmrgd said:**
> Ooops!  Forgot to paste it in.  It's here:

[http://www.webupd8.org/2011/02/fix-dpkg-error-trying-to-overwrite-x.html](http://www.webupd8.org/2011/02/fix-dpkg-error-trying-to-overwrite-x.html)

Sorry about that!

this worked, thanks a lot :)

---

