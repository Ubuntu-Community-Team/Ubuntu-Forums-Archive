---
title: "Cannot start openoffice - &quot;undefined symbol&quot;"
date: 2005-01-10
forum: General Help
---

### Post by spin on 2005-01-10
For some reason ooffice won't start at all on my Ubuntu Laptop.

When run from gnome-terminal, this is the result given:

root@ubuntu-dell:~ # ooffice
OpenOffice.org for Debian - see /usr/share/doc/openoffice.org/README.Debian.gz
running openoffice.org setup...
/usr/lib/openoffice/program/setup.bin: relocation error: /usr/lib/openoffice/program/libsvt645li.so: undefined symbol: ataWrappert
setup failed (code 0).. abort
---- Please read /usr/share/doc/openoffice.org/README.Debian.gz for known problems -----

I couldn't find anything in the README file that helped. I have also double-checked that I only have one language pack installed (initially I installed 3 different ones, but removed 2 of them when I managed to google a slightly similar ooffice bug).

I'd be grateful for any help.

---

### Post by wallijonn on 2005-01-10
Why are you running / opening it from a terminal window? Did you break sudo and gave the root its own password?

---

### Post by spin on 2005-01-10
Hm. There goes my reputation in this forum, I guess :)

The reason for running ooffice as root in the first place was I thought I might just try it, in case some file permissions had been screwed up or something like that (I don't like to consider myself a complete newbie, but admittedly, my Linux capabilities are highly limited...). And when I copy-pasted the terminal output, that very session happened to be the one open. The reason for running it from a terminal window was just to get a bit more verbose output than when I run it from the gnome menu (or a Run command window), since when I do, *nothig at all* (apparently) happens.

(Regarding sudo, sometimes I just prefer to do sudo bash since that's the way I'm used to Linux, I guess (in Debian I used to just su into root mode). I haven't given root its own pw.)

---

