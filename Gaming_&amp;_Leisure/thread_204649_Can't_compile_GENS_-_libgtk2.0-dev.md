---
title: "Can't compile GENS - libgtk2.0-dev"
date: 2006-06-27
forum: Gaming &amp; Leisure
---

### Post by lpsavoie on 2006-06-27
Hi,

I'm currently trying to compile GENS, a Sega Genesis emulator. build-essential, gcc-3.4 and nasm installed just fine, however, when I try to install libgtk2.0-dev, it gives the following errors :

```
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
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.10.0-2) but it is not going to be installed
                 Depends: libcairo2-dev but it is not going to be installed
                 Depends: libxcursor-dev but it is not going to be installed
                 Depends: libxfixes-dev but it is not going to be installed
E: Broken packages

```

Should I file a bug against libgtk2.0-dev ? I'm running Ubuntu Dapper with main, universe, multiverse and restricted components enabled.

---

### Post by Greg2 on 2006-06-27
[QUOTE=lpsavoie]
Should I file a bug against libgtk2.0-dev ?[/QUOTE]
Always search the Ubuntu bug tracker first. I’ve done a search for you this time... Please check it and add any info you have:
[https://launchpad.net/distros/ubuntu/+source/gtk+2.0/+bug/49220](https://launchpad.net/distros/ubuntu/+source/gtk+2.0/+bug/49220)

---

### Post by daveg on 2006-06-28
[QUOTE=lpsavoie]Should I file a bug against libgtk2.0-dev ? I'm running Ubuntu Dapper with main, universe, multiverse and restricted components enabled.[/QUOTE]What do you get when you run [FONT="Courier New"]apt-cache policy libgtk2.0-dev[/FONT]? Sounds like there's a conflict with another non-ubuntu repo.

---

