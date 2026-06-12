---
title: "Long Term Support"
date: 2023-01-20
forum: Desktop Environments
---

### Post by Geoff_Lane on 2023-01-20
Curious folks, I understand [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS) the LTS versions are supported for 3 years for Desktops and 5 years for the server versions.  A few users will install a server then load a light windows manager to the system, how do the updates work then if it goes beyond 3 years?  Probably in practice this would seldom occur but am wondering.  Geoff

---

### Post by ajgreeny on 2023-01-20
The default Ubuntu LTS versions have a 5 year support time but most, if not all the other DE versions, eg Xubuntu which I use, Kubuntu, Lubuntu, and I think all the others are supported for 3 years only. The interim versions between those LTS versions have 9 months only of support.
The server editions have no GUI and are supported either for 5 years or just 9 months depending on the number version.

If I've got those different DE versions' support periods wrong I'm sure someone will tell us.

---

### Post by TheFu on 2023-01-20
No updates of programs that aren't part of the main Gnome Ubuntu release happen. That's the risk.  If you run Gnome stuff, you can get lucky if the main Gnome DE used by the primary Ubuntu Desktop which has 5 yrs of support uses a program. Those will be part of the Ubuntu main repo.

I load a server release, then add a window manager for my desktops to avoid bloat from 90% of the programs that I'll never use. I don't load any DE, just fvwm.  fvwm has been around since 1995 and really hasn't changed significantly since around 2005.  So, the lack of support for it doesn't really bother me.   I don't like the network integration in the GUI.  Networking should be on and working, even when no user is logged in.  I have to admit, that I did modify fvwm menus to add simple volume control.

However, after the 3 yr period ends, many other programs that I load will become unsupported.  So, I need to consider the risks involved.  For high risk tools, I'll create a virtual machine with a supported release and use remote X11 to run those programs, but have them displayed on my local, stable,  system.  For example, this browser and thunderbird are high-risk programs.  They are running on a 20.04 system, but there are many things in 20.04 desktops that I dislike (too many snaps), so I prefer to use non-snap programs locally.  It is about time to move that 20.04 desktop to 22.04 and load the high-risk programs there.
Here's how I run Thunderbird:
$ more ~/bin/thunderbird.sh 
```

#!/bin/bash
FJ_OPTS="--dns=172.22.22.80 --rlimit-as=3500000000 --ignore=seccomp --ignore=protocol"
TB_OPTS="-no-remote "

# limit RAM VSS to 4G
/usr/bin/ssh -X  regulus /usr/bin/firejail $FJ_OPTS /usr/bin/thunderbird $TB_OPTS $@ & 
exit;

```

Running firefox is similar.  I have 2 scripts for that. One allows access to $HOME and one doesn't allow any file system access at all, for more privacy.  

There are other strategies.  Some people use Linux Containers to run their high-risk programs.  I haven't tried to get GUI programs working under a container for display on my local system.   Breaking the OS <--> Container X11 barrier scares me a little. Maybe it is just my ignorance.

I'm sure there are 20 other strategies.

---

### Post by guiverc on 2023-01-20
I'll just add you should read the *release notes* or *release announcements* carefully.  I'll use 18.04 as example.

Link: [https://fridge.ubuntu.com/2018/04/27/ubuntu-18-04-lts-bionic-beaver-released/](https://fridge.ubuntu.com/2018/04/27/ubuntu-18-04-lts-bionic-beaver-released/)

> Maintenance updates will be provided for 5 years for Ubuntu Desktop,  Ubuntu Server, Ubuntu Cloud, and Ubuntu Core. Ubuntu Studio will be  supported for 9 months. All the remaining flavours will be supported for  3 years.

Lots of people just assumed Ubuntu Studio 18.04 was a LTS release (*based purely on 18.04*), but nowhere did it actually state that, in fact the Ubuntu Studio team warned it wasn't (*in release notes*) and gave reasons why. In the end they did provide the equivalent of LTS support via PPA for 18.04 (*that PPA now dropped as 18.04 isn't supported by flavors*), but I still suggest you read the release notes of whatever system you use.  The team members & others read & review them to ensure they're as accurate as they can be.

---

### Post by Geoff_Lane on 2023-02-24
> **TheFu said:**
> 
I load a server release, then add a window manager for my desktops to avoid bloat from 90% of the programs that I'll never use. I don't load any DE, just fvwm.  fvwm has been around since 1995 and really hasn't changed significantly since around 2005.  So, the lack of support for it doesn't really bother me

I actually did that for the first time after a hard drive failure forced a reinstall, I installed ubuntu server then just iceWM so at boot it puts me in terminal.  startx boots up the window window manager.

Previously I generally went with gnome but am currently exploring Plasma on a different distro.

Geoff

---

