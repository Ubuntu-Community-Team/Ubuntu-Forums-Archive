---
title: "[SOLVED] Gtk/Glib installation"
date: 2009-01-05
forum: General Help
---

### Post by Gaambo on 2009-01-05
HeyHo!

I'm trying to install Gtk - so first I've  to install glib,pango and atk.
So I started with glib, downloaded it, unpacked it. Then I did the './configure'. There everything seemed fine and i didn't get an error. But when i tried to 'make' glib the following error came along:

```
make: *** Keine Regel vorhanden, um das Target »po/LINGUAS«, 
  benötigt von »config.status«, zu erstellen.  Schluss.

```

For those who can't speak German: It says that there is 'no rule' to build(/make) the 'Target' "po/LINGUAS", which is needed by >config.status<

Could anyone help me please? 
What does this error mean? the ./configure went fine, so I really don't know what the problem is. :confused:

---

### Post by mali2297 on 2009-01-05
Why do you need to compile it from source?

GTK+ is already installed by default on Ubuntu. If you need the development libraries, then they can be obtained through the package manager. See this [howto](https://help.ubuntu.com/community/SynapticHowto) on installing software with Synaptic. The package is called **libgtk2.0-dev**.

---

### Post by Gaambo on 2009-01-05
Well, I wanted to install the UbuntuEEE-nbr-desktop-switcher, and I must compile it, but during the ./configure it always says

```

No package 'gtk+-2.0' found
No package 'gconf-2.0' found
No package 'gmodule-2.0' found
No package 'gio-2.0' found

```

so I thought, gtk isn't installed.

---

### Post by blazemore on 2009-01-05
Is the package called libgtk2?
```
sudo apt-get build-dep **libgtk2**
```
Replace text in bold with proper name of package, I don't know what it is.
This command will install the build dependancies of the package.
Also, I know it sounds obvious, but have you done
```
sudo apt-get install build-essential
```

---

### Post by Gaambo on 2009-01-05
> **blazemore said:**
> Is the package called libgtk2?
```
sudo apt-get build-dep **libgtk2**
```
Replace text in bold with proper name of package, I don't know what it is.
This command will install the build dependancies of the package.


I tried so, but it just said that the package 'build dep' couldn't be found.
The proper name is libgtk2.0, isn't it?

EDIT: sorry, i did ```
sudo apt-get install build dep ..
``` :D
okey, now i did right, but it said that there is no source pack for libgtk2.0

---

### Post by blazemore on 2009-01-05
Not apt get INSTALL build-dep
Just apt-get build-dep

---

### Post by mali2297 on 2009-01-05
> **Gaambo said:**
> Well, I wanted to install the UbuntuEEE-nbr-desktop-switcher, and I must compile it, but during the ./configure it always says

```

No package 'gtk+-2.0' found
No package 'gconf-2.0' found
No package 'gmodule-2.0' found
No package 'gio-2.0' found

```

so I thought, gtk isn't installed.

You need the development files, install the packages build-essential and libgtk2.0-dev through Synaptic. Alternatively, you can use the terminal:
```

sudo apt-get install build-essential libgtk2.0-dev 

```

---

### Post by mcduck on 2009-01-05
> **Gaambo said:**
> Well, I wanted to install the UbuntuEEE-nbr-desktop-switcher, and I must compile it, but during the ./configure it always says

```

No package 'gtk+-2.0' found
No package 'gconf-2.0' found
No package 'gmodule-2.0' found
No package 'gio-2.0' found

```

so I thought, gtk isn't installed.

When compiling, the errors about missing packages pretty much always mean the development packages (package names ending with "-dev"). So in this case you need the dev packages for gtk2, gconf2, gmodule2 and gio2.

The non-development versions of those packages are most likely already installed, since great part of your applications (including the Gnome desktop itself) needs them to work.

---

### Post by Gaambo on 2009-01-05
@blazemore: already edited, sorry

@mali:

build-essential is already installed, without problems, but when I want to install libgtk2.0-dev it says:

```
Einige Pakete konnten nicht installiert werden. Das kann bedeuten, dass
Sie eine unmögliche Situation angefordert haben oder dass, wenn Sie die
Unstable-Distribution verwenden, einige erforderliche Pakete noch nicht
kreiert oder aus Incoming herausbewegt wurden.
Die folgenden Informationen helfen Ihnen vielleicht, die Situation zu lösen:

Die folgenden Pakete haben nichterfüllte Abhängigkeiten:
  libgtk2.0-dev: Hängt ab: libatk1.0-dev (>= 1.6.1-2) soll aber nicht installiert werden
                 Hängt ab: libcairo2-dev soll aber nicht installiert werden
                 Hängt ab: libpango1.0-dev (>= 1.10.0-2) soll aber nicht installiert werden
                 Hängt ab: libx11-dev (>= 2:1.0.0-6) soll aber nicht installiert werden
                 Hängt ab: libxcomposite-dev soll aber nicht installiert werden
                 Hängt ab: libxcursor-dev soll aber nicht installiert werden
                 Hängt ab: libxdamage-dev soll aber nicht installiert werden
                 Hängt ab: libxext-dev soll aber nicht installiert werden
                 Hängt ab: libxfixes-dev soll aber nicht installiert werden
                 Hängt ab: libxi-dev soll aber nicht installiert werden
                 Hängt ab: libxinerama-dev soll aber nicht installiert werden
                 Hängt ab: libxrandr-dev soll aber nicht installiert werden
E: Kaputte Pakete

```

Sorry for my bad englisch, I don't know the proper englisch form for 'nicht erfüllte abhängigkeiten' .. Maybe you know what I  mean.

Thanks for helping me!

---

### Post by blazemore on 2009-01-05
```
sudo sed -i -e "s/# deb/deb/g" /etc/apt/sources.list
```
Then try again.
This enables all repositories.

---

### Post by Gaambo on 2009-01-05
Same problem.
I tried to install some of these packages myself, but there just came more errors.
for example while installing libatk1.0-dev it says

```
 libatk1.0-dev: Hängt ab: libatk1.0-0 (= 1.22.0-0ubuntu1) aber 1.24.0-1 soll installiert werden

```
Allthough it's german, I don't understand.

---

### Post by mali2297 on 2009-01-05
> **Gaambo said:**
> 

Sorry for my bad englisch, I don't know the proper englisch form for 'nicht erfüllte abhängigkeiten' .. Maybe you know what I  mean.


Try using Synaptic, I think there is an option to fix broken packages. You can also check that you have all repositories enabled via Settings -> Repositories.

EDIT:
If it still does not work, post the content of /etc/apt/sources.list. You can use the command
```

cat /etc/apt/sources.list

```
in a terminal.

---

### Post by blazemore on 2009-01-05
Is there no way to get this in English? These look familiar but I don't know exactly how to help.
That looks like it's expecting a version, but you have a later version installed.
Can we try doing it through Synaptic?

---

### Post by Gaambo on 2009-01-05
i could send it through google-translator :D
ah, yeah that's what it says!

Synaptic is very funny today -.- . I tried to install gtk2.0-dev, it said that some of its dependences just couldn't be installed:
```

libgtk2.0-dev:
 Hängt ab: »libatk1.0-dev«, aber es wird nicht installiert.

```
Means that 'libatk1.0-dev' is needed, but won't be installed. And i don't know why.

---

### Post by Gaambo on 2009-01-05
@mali:
```
deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://at.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://at.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://at.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://at.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://at.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://at.archive.ubuntu.com/ubuntu/ hardy universe
deb http://at.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://at.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://at.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://at.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://at.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://at.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://at.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://at.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://wine.budgetdedicated.com/apt hardy main #WineHQ - Ubuntu 8.04 "Hardy Heron"
deb http://unicap-imaging.org/packages feisty main contrib
deb http://ftp.at.debian.org/debian experimental main

```

my sources.list

---

### Post by mali2297 on 2009-01-05
> **Gaambo said:**
> 
deb [http://unicap-imaging.org/packages](http://unicap-imaging.org/packages) feisty main contrib
deb [http://ftp.at.debian.org/debian](http://ftp.at.debian.org/debian) experimental main
[/CODE]

my sources.list

Open the file in an editor, for example with
```

sudo nano /etc/apt/sources.list

```
Comment out the two last lines in the file. That is, make it
```

# deb http://unicap-imaging.org/packages feisty main contrib
# deb http://ftp.at.debian.org/debian experimental main

```
Try again to install libgtk2.0-dev.

---

### Post by Gaambo on 2009-01-05
Same problem. -.-
Well, could it help if i remove the old gtk/glib/usw packages and reinstall them?
I already did apt-get update/upgrade.

---

### Post by mali2297 on 2009-01-05
My guess is that you have installed packages from debian experimental which are in conflict with the native ubuntu packages. You are looking at a dependency hell. :-) 

Yes, you could try reinstalling packages. However, there might be a risk that you break things further.

---

### Post by Gaambo on 2009-01-05
> **mali2297 said:**
> My guess is that you have installed packages from debian experimental which are in conflict with the native ubuntu packages. You are looking at a dependency hell. :-) 

Which packages could that be? .. ^^

Sounds like i've got a lot of problems in my system .. :D

---

### Post by mali2297 on 2009-01-05
> **Gaambo said:**
> Which packages could that be? ..

Look in Synaptic. I think that you can browse packages by repositories.

---

### Post by Gaambo on 2009-01-05
Well, I looked after broken packages in Synaptic. But it didn't find any. 
Anything is wrong here, I don't know what ..

---

### Post by mali2297 on 2009-01-05
Start with libatk1.0-dev and check that you have the version 1.22.0-0ubuntu1.

---

### Post by Gaambo on 2009-01-05
It isn't installed yet. So I tried to install it, it sais that libatk1.0 (in version =1.22.0-0ubuntu1 ) is needed, but 1.24.0-1 is installed. Shall I reinstall libatk1.0 with the old version?

---

### Post by Gaambo on 2009-01-05
Okey, I finally got it working.
I found the answer here: [http://forum.ubuntuusers.de/topic/gtk-glib-installation/](http://forum.ubuntuusers.de/topic/gtk-glib-installation/)

aptitude seems to be more intelligent :D

Allthough, I thank you ;)

---

### Post by mali2297 on 2009-01-05
So aptitude could sort out all dependencies and install libgtk2.0-dev successfully? I will remember that in case I see posts with similar problems.

---

### Post by Gaambo on 2009-01-05
Yeah, it seems so. Aptitude 'deupdatet' some packages, so everything could be installed properly.
Crazy :D

---

