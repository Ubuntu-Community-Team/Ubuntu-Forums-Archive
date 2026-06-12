---
title: "other Window Managers (TWM, JWM etc.)"
date: 2014-06-14
forum: Desktop Environments
---

### Post by oui on 2014-06-14
using Ubuntu I also will use Debian menu.

it generates menu files for divers window managers (TWM, JWM etc.)

the maintainer in Debian did organize the work of Debian menu so that for example menu generates and actualize a file

debian=menu

in the dir

/etc/jwm

where you also find a file system.jwmrc containing an include command as following:

> <Include>/etc/jwm/debian-menu</Include>.

All that works correctly (with JWM as well as with TWM).

Difficult is if you extend your window manager configuration and will use the other abilities of your window manager!

if you requires, it have to open your favorite file manager, for example Dolphin, with the command in JWM:

```
   <StartupCommand>
      gkrellm & 
      dolphin &
      firefox
   </StartupCommand>
```

in the file system.jwmrc

at the next start you get the message

> Le fichier de configuration « /home/f/.kde/share/config/dolphinrc » n'est pas inscriptible.
Veuillez contacter votre administrateur système.

(this means: your configurations file « ... » is not writable. Pls contact your system administrator)

I am my system administrator  :oops:  ; what a silly dilly help message  :mrgreen: !

After an hit on the «ok» key, the start process continue apparently normal. Your lovely file manager opens as you did require but

if you hit in it on the «Home» icone, it tries to open /root and not your real home subdir under your root user name in /home!

it seems to happen following error: as the command came from a file out /etc it considere that you have to be root at starting time :roll: .

(it is completely wrong: I never be "root" on my system but have a user name having root right und will never be user of the dir /root as person (I know that the system has files in it).

what ist to change to get an friendly use of such window manager like TWM, JWM etc.?

kind regards

---

### Post by TREESofRIGHTEOUSNESS on 2014-07-25
Hi,
You are NOT supposed to edit the system.jwmrc file.
You are supposed to create a .jwmrc file in your $HOME directory
I suggest trying out this program:
[https://launchpad.net/jwm-settings-manager](https://launchpad.net/jwm-settings-manager)

You can add this PPA
[https://launchpad.net/~israeldahl/+archive/ubuntu/torios](https://launchpad.net/~israeldahl/+archive/ubuntu/torios)
Which contains the program.... it is under development right now, but works well enough for me.
File bugs, etc... if you find any.
An Ubuntu distro using JWM is in the works.... torios.org

The reason your startup programs were having issues, was you are running them as root from the /etc part, rather than from ~/

---

