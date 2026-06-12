---
title: "problemas instalando wine  winetricks NOVATO"
date: 2020-07-11
forum: Comunidad
---

### Post by beugeste on 2020-07-11
[COLOR=#000000][FONT=Verdana]quiero seguir los pasos pero me salta este error en la terminal[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]dpkg --add-architecture i386[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]dpkg: error: unable to create new file '/var/lib/dpkg/arch-new': Permission denied[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]y ademas[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]sudo apt update[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Hit:1 [/FONT][/COLOR][http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb)[COLOR=#000000][FONT=Verdana] stable InRelease[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Hit:2 [/FONT][/COLOR][http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu)[COLOR=#000000][FONT=Verdana] focal InRelease                      [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Hit:3 [/FONT][/COLOR][http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu)[COLOR=#000000][FONT=Verdana] focal-updates InRelease              [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Hit:4 [/FONT][/COLOR][http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu)[COLOR=#000000][FONT=Verdana] focal-security InRelease    [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Ign:5 [/FONT][/COLOR][http://ppa.launchpad.net/morphis/anbox-support/ubuntu](http://ppa.launchpad.net/morphis/anbox-support/ubuntu)[COLOR=#000000][FONT=Verdana] focal InRelease[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Hit:6 [/FONT][/COLOR][http://ar.archive.ubuntu.com/ubuntu](http://ar.archive.ubuntu.com/ubuntu)[COLOR=#000000][FONT=Verdana] focal-backports InRelease            [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Err:7 [/FONT][/COLOR][http://ppa.launchpad.net/morphis/anbox-support/ubuntu](http://ppa.launchpad.net/morphis/anbox-support/ubuntu)[COLOR=#000000][FONT=Verdana] focal Release      [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]  404  Not Found [IP: 91.189.95.83 80][/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]E: The repository '[/FONT][/COLOR][http://ppa.launchpad.net/morphis/anbox-support/ubuntu](http://ppa.launchpad.net/morphis/anbox-support/ubuntu)[COLOR=#000000][FONT=Verdana] focal Release' does not have a Release file.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]N: Updating from such a repository can't be done securely, and is therefore disabled by default.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]N: See apt-secure(8) manpage for repository creation and user configuration details.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]y desoues[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]sudo apt install wine:i386[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Reading package lists... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Building dependency tree      [/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Reading state information... Done[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]Package wine:i386 is a virtual package provided by:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]  wine 5.0-3ubuntu1[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]  wine 5.0-3ubuntu1[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]  wine-development 5.5-3ubuntu1[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]You should explicitly select one to install.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]E: Package 'wine:i386' has no installation candidate[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]carlos@carlos-Lenovo-IdeaPad-S400:~/Desktop$ sudo apt wine 5.0-3ubuntu1[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]E: Invalid operation wine[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]carlos@carlos-Lenovo-IdeaPad-S400:~/Desktop$ sudo apt wine 5.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]E: Invalid operation wine[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]carlos@carlos-Lenovo-IdeaPad-S400:~/Desktop$[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]despues instalo con exito el wine 5.0 pero al tratar de instalar winetricks me dice[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]carlos@carlos-Lenovo-IdeaPad-S400:~/Desktop$ sudo apt winetricks[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana][sudo] password for carlos:[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]E: Invalid operation winetricks[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]carlos@carlos-Lenovo-IdeaPad-S400:~/Desktop$ sudo apt winetricks[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]E: Invalid operation winetricks[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]carlos@carlos-Lenovo-IdeaPad-S400:~/Desktop$[/FONT][/COLOR]

---

### Post by guiverc on 2020-07-12
A number of your errors are correct

[COLOR=#000000][FONT=Verdana]E: Invalid operation wine
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana][COLOR=#000000][FONT=Verdana]E: Invalid operation winetricks

ie. `wine` and `winetricks` you would have meant as packages, but were attempted to be operated on as if operands.

You possible meant to use 
```
`sudo apt install wine`
```
  (ie. telling `apt` to "install" the package "wine").[/FONT][/COLOR]

From `man apt` you get
```
       apt [-h] [-o=config_string] [-c=config_file] [-t=target_release] [-a=architecture] {list | search | show | update | install pkg [{=pkg_version_number | /target_release}]...  |
           remove pkg...  | upgrade | full-upgrade | edit-sources | {-v | --version} | {-h | --help}}
```
telling you need a command, ie. one of "list | search | show | install" which is followed by the package|pkg.
[/FONT][/COLOR]

---

