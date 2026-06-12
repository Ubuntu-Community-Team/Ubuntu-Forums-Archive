---
title: "Now Osmo wont' start at all in Lubuntu"
date: 2012-01-13
forum: Desktop Environments
---

### Post by M_Mynaardt on 2012-01-13
Hi!

I just tried running Osmo from the GUI; no response.  So I tried from the terminal and this was the result I got:
```
:~$ osmo
**
gtkspell:ERROR:/build/buildd/gtkspell-2.0.16/./gtkspell/gtkspell.c:752:gtkspell_new_attach: assertion failed: (spell == NULL)
Aborted

```

Does anyone know what that would be all about?

Thanks...

---

### Post by Toz on 2012-01-13
What version of ubuntu are you using:
```
cat /etc/lsb-release
```

How did you install osmo? From the software centre, a PPA, or from source?

What version of osmo do you have installed:
```
apt-cache policy osmo
```

And what version(s) of gtkspell do you have installed?
```
dpkg -l | grep gtkspell
```

---

### Post by Rex Bouwense on 2012-01-13
OP is using Lubuntu, which I believe installs Osmo by default.

---

### Post by M_Mynaardt on 2012-01-14
> **Toz said:**
> What version of ubuntu are you using:
```
cat /etc/lsb-release
```

How did you install osmo? From the software centre, a PPA, or from source?

What version of osmo do you have installed:
```
apt-cache policy osmo
```

And what version(s) of gtkspell do you have installed?
```
dpkg -l | grep gtkspell
```

I believe that Osmo came with Lubuntu 11.10.

As for the other bits:

Version of Lubuntu:
```
:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
```

Version of Osmo:
```
:~$ apt-cache policy osmo
osmo:
  Installed: 0.2.10+svn922-2
  Candidate: 0.2.10+svn922-2
  Version table:
 *** 0.2.10+svn922-2 0
        500 http://ca.archive.ubuntu.com/ubuntu/ oneiric/universe i386 Packages
        100 /var/lib/dpkg/status
```

Version(s) of gtkspell:
```
:~$ dpkg -l | grep gtkspell
ii  libgtkspell-common
2.0.16-1ubuntu2     spell-checking addon for GTK's TextView widget
ii  libgtkspell0
2.0.16-1ubuntu2     spell-checking addon for GTK's TextView widget
ii  libgtkspell3-0
2.0.16-1ubuntu2     spell-checking addon for GTK's TextView widget
ii  python-gtkspell
2.25.3-7ubuntu3      Python bindings for the GtkSpell library
```

I also found that if I deleted the ~/.osmo folder and replaced it with a back up of its contents, the Osmo worked fine again.  So *something* is making a hash of the ~/.osmo contents somehow, I figure.

Thanks!

---

### Post by on4aa on 2012-09-11
I experienced exactly the same problem today after changing the Spell checker language under the General Preferences and setting Enable spell checker in day notes on.

The solution does not have to be as drastic as deleting the whole ~/.osmo directory; Deleting config.xml in that directory suffices.

As a reference for debuggers, I have attached the offending config.xml as a text file.

---

### Post by M_Mynaardt on 2012-09-11
> **on4aa said:**
> I experienced exactly the same problem today after changing the Spell checker language under the General Preferences and setting Enable spell checker in day notes on.

The solution does not have to be as drastic as deleting the whole ~/.osmo directory; Deleting config.xml in that directory suffices.

As a reference for debuggers, I have attached the offending config.xml as a text file.

I never thought of deleting the Osmo config.xml file.  That does not do any damage to Osmo?  I just don't like tinkering with these things for fear of making them worse.

Thanks.

---

### Post by on4aa on 2012-09-13
> **M_Mynaardt said:**
> I never thought of deleting the Osmo config.xml file.  That does not do any damage to Osmo?

Instead of plain deleting it is more cautious to just rename the file.
Anyhow, Osmo will generate an all new config.xml with default values.

I then used Meld to graphically compare both files and change back the settings that have nothing to do with spell checking nor locales.

---

### Post by M_Mynaardt on 2012-09-13
> **on4aa said:**
> Instead of plain deleting it is more cautious to just rename the file.
Anyhow, Osmo will generate an all new config.xml with default values.

I then used Meld to graphically compare both files and change back the settings that have nothing to do with spell checking nor locales.

Okay, I'll try to check that out.  Thanks...

---

### Post by M_Mynaardt on 2013-03-25
ARGH!!  I stumbled onto the problme with OSMO not starting up properly for me in Lubuntu.  It was a simple typing error in my **~/.config/autostart/osmo.desktop** file!

The error was this line:
**Exec=/usr/bin/osmo&**
I deleted the "&" and it works just fine.

Silly mistake!
#-o

---

