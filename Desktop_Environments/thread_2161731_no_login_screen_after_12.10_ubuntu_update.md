---
title: "no login screen after 12.10 ubuntu update"
date: 2013-07-11
forum: Desktop Environments
---

### Post by msinfo on 2013-07-11
[COLOR=#333333][FONT=UbuntuRegular]i am running dual boot os machine including windows7 and ubuntu. few days back, i did update to 12.10 version, and at that time i was using gnome fallback desktop environment.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]while doing update, i could see in remove obsolete packages, it removed some gnome related files. and at that time i was using gnome fall-back desktop environment with clear looks theme, because i did not like unity much.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]
when i restarted machine, it gave me option to select Ubuntu / windows7, when i selected ubuntu, it showed me ubuntu logo, but from that point, only black screen would remain there, and no login screen would come, no matter how far i waited.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]using advance options in menu (and askubuntu/ubuntu forums) i tried following methods, but to no avail.[/FONT][/COLOR]

[LIST=1]
[*]booting to old kernel 3.5 and 2.6/2.4.
[*]dpkg-reconfigure gdm(and both lightdm), setting it to lightdm. and restarting lightdm
[*]sudo /usr/lib/lightdm/lightdm-set-defaults -s ubuntu-2d (no use)
[*]chown username:username .Xauthority (its already on my username)
[*]/etc/X11/default-display-manager to say /usr/sbin/lightdm (it was already there)
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]and one more doubt:[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]some solutions suggest to install and reinstall packages, for e.g[/FONT][/COLOR]

sudo apt-get install --reinstall ubuntu-desktop
[COLOR=#333333][FONT=UbuntuRegular]
how do i install packages even after enabling networking, if i need a manual login, on web page provided by my ISP for starting internet connection.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]
machine: 32bit, intel pentium 4CPU 3.2 Ghz, Standard VGA Graphics Adapter, 1GB RAM[/FONT][/COLOR]

---

### Post by msinfo on 2013-07-17
After trying above methods and various online suggestions, (which failed, in my case), I formatted only / (root) drive by installing fresh 12.04 LTS edition. This didn't deleted my /home and other data, and nothing was lost except few installed programs (which i installed later on).

---

