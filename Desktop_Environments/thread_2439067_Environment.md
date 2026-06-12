---
title: "Environment?"
date: 2020-03-22
forum: Desktop Environments
---

### Post by xcfstarflight1 on 2020-03-22
Yo
What is ment by environment? 
Currently I am just using the Wayland with Ubuntu. 
I do have Kodi and Cinnamon as a choice when I log in, just don't understand why my screen just flicker when I select it and then 
just jumps back to login screen.

I want to try out xUbuntu but I am not sure if that will overwrite the OS of Ubuntu or just add the environment (like colors, buttons and menues).

If anyone has a reply to my question and also the stuff about xUbuntu, please do take contact.

To put it in another way. Is xUbuntu a Distro?

---

### Post by Autodave on 2020-03-22
Xubuntu is a distro: it is what I use on all of my 12 machines.  IF you are going to try it, I would recommend a clean install and get rid of all the other distros that you are using.  While it is possible to run many from the same install, problems can and will arise from that.

---

### Post by Frogs Hair on 2020-03-22
There is good explanation in this forum's sticky. 
[https://ubuntuforums.org/showthread.php?t=2415676](https://ubuntuforums.org/showthread.php?t=2415676)

---

### Post by ipv on 2020-03-22
> **xcfstarflight1 said:**
> Is xUbuntu a Distro?

xubuntu is a distro primarily for older machines which are low on hardware specifications especially ram, since xubuntu uses fewer system resources. 

> **Autodave said:**
> get rid of all the other distros that you are using.

seriously? 

why not let the op decide which distro he prefers ?

---

### Post by webaake on 2020-03-22
The DE in Xubuntu is Xfce and there are very few problems to have Xfce as a DE - Desktop Environment parallell to other DE:s. Just choose at login. It's not ideal but it works well enough. In Ubuntu just install xubuntu-desktop - log out and login to the new DE.

BUT, one of your DE:s doesn't start. You can login to the console instead by :```
Open a text-only virtual console by using the keyboard shortcut Ctrl + Alt + F3 .
At the login: prompt type your username and press Enter .
At the Password: prompt type your user password and press Enter 
```

If F3 doens't work, try F1, F2 and so on.

From the console you can check the logs for problems with the DE that doesn' start. Checkout dmesg and juornalctl.

---

### Post by ajgreeny on 2020-03-22
I'm with Autodave when he advises a clean install.

You appear to already have two DEs and to add a third will I suspect cause more problems than it solves.

You have not told us which version of Ubuntu you are using; 16.04, 18.04 or 19.10 are the only three versions currently supported so I hope it's one of those, but that aside, a clean install of Xubuntu will undoubtedly be the best option for you in my opinion.

You can always look at Xubuntu 19.10 or 18.04 as a live system to investigate the desktop environment. Xubuntu has been my preferred system for several years now, since gnome 2 disappeared, and is not just for older machines with low resources, it's also for those.like me who want to use the resources they have for useful things other than just pointless eye-candy.

---

### Post by xcfstarflight1 on 2020-03-22
It looks soo nice but I have spent so much time setting up my Ubuntu.. :( Sadly.. Some time!

---

### Post by xcfstarflight1 on 2020-03-22
Cinnamon is available at login, also Kodi. But when I select anything but Ubuntu and Wayland, the screen flickers and i cannot log in.. 
So if there are no way to be using both then I will just stick with it.

Have a good day/evening/night depending on where you are! :-)

The cinnamon/KODI etc appear on the wheel beside login......

---

### Post by webaake on 2020-03-23
Yes, several DE's in the same installation can cause problems. But problems in Linux are "opportunities". Like why did the screen flicker and you were bounced back to the login screen? Very interesting indeed. The findings you can get from this are opportunities to learn, and possibly even report bugs to the programmers. In theory you could have Lubuntu, Xubuntu and Kubuntu desktops installed in paralell. And decide which one is for you. I recommend this approach solely from a learning perspective. In the end you will gain knowledge about the console, terminal commands and desktop environments (at least). So, when you're bounced out next time start the console and begin the journey. :D

PS Ahh, du är från Norge? Då kan vi nästan köra på våra modersmål!

---

### Post by xcfstarflight1 on 2020-03-25
Jepp norsk her
Bare skjønner ikke hvorfor jeg ikke kan kjøre en "flavour" over Ubuntu uten noe ny distro.. Men har gnome-tweaks og sånn da :) Skulle gjerne hatt ett alternativ til dockingen der applikasjonene ligger.
Har du peiling på noe sånt? 
Salute fra Norge ;)

[COLOR="#FF0000"]EDIT:
Translation from Google-translate for non-Norwegian speakers.[/COLOR]
> Yep Norwegian here
Just don't see why I can't run a "flavor" over Ubuntu without some new distro .. But have gnome tweaks and stuff like that Should have had one alternative to the dock where the applications are located.
Do you have a clue about something like that?
Salute from Norway

---

### Post by Frogs Hair on 2020-03-25
You can install multiple desktops if you like and select any of them during login. The problem is clutter and duplicate application because different desktops use different default applications. This can result in broken packages during update.

---

### Post by TheFu on 2020-03-25
"Environment" can mean multiple things.  What everyone above seemed jump onto is the "Desktop Environment", which is almost universally abbreviated as "DE". The context provided with the question lead them in that direction, correctly.

Server people talk about "environments", meaning the general way everything in a system fits into a larger world.  "Tell me about your environment" is a common request when I first talk with a client.  The answer might be about 1 computer or hundreds.  Just depends.  

Tell me about your "networking environment" could result in "we use wifi" or they could send over 10 pages of network architecture diagrams with a different network zone for each page. Those zones are firewalled off from each other with normal users having access only to 1 network zone. VPN access for different groups might be included between zones or from the public internet, depending on the user's VPN login too.

In these forums, when I say "cron doesn't provide much environment", I'm specifically talking about _environment_ variables.  Type 
```
$ env
```
to see them.  They will be different for every userid and also depend on whether an interactive shell is being used or a batch login is.  

Here's a non-interactive shell connection to a system named "hadar", the env:
```
$ ssh hadar env
XDG_SESSION_ID=4460
GVFS_DISABLE_FUSE=1
SHELL=/bin/bash
SSH_CLIENT=172.22.22.11 34334 22
USER=tf
MAIL=/var/mail/tf
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
PWD=/home/tf
LANG=en_US.UTF-8
SHLVL=1
HOME=/home/tf
LOGNAME=tf
SSH_CONNECTION=172.22.22.11 34334 172.22.22.6 22
XDG_RUNTIME_DIR=/run/user/1000
_=/usr/bin/env

```

OTOH, for an interactive shell on hadar:

```
$ env
XDG_VTNR=7
PERLBREW_SHELLRC_VERSION=0.86
MANPATH=/home/tf/perl5/perlbrew/perls/perl-5.29.7/man:/usr/local/man:/usr/local/share/man:/usr/share/man
SSH_AGENT_PID=23609
XDG_SESSION_ID=c4
PERLBREW_VERSION=0.86
XDG_GREETER_DATA_DIR=/var/lib/lightdm-data/tf
GPG_AGENT_INFO=/home/tf/.gnupg/S.gpg-agent:0:1
GVFS_DISABLE_FUSE=1
PERLBREW_PERL=perl-5.29.7
SHELL=/bin/bash
TERM=xterm
QT_LINUX_ACCESSIBILITY_ALWAYS_ON=1
WINDOWID=12582927
OLDPWD=/home/tf
GTK_MODULES=gail:atk-bridge
USER=tf
XTERM_SHELL=/bin/bash
QT_ACCESSIBILITY=1
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:
XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session1
XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0
SSH_AUTH_SOCK=/tmp/ssh-pDIkQwQfpbq1/agent.23547
DEFAULTS_PATH=/usr/share/gconf/openbox.default.path
LIBVIRT_DEFAULT_URI=qemu:///system
PERLBREW_ROOT=/home/tf/perl5/perlbrew
XDG_CONFIG_DIRS=/etc/xdg/xdg-openbox:/etc/xdg
DESKTOP_SESSION=openbox
PATH=/home/tf/perl5/perlbrew/bin:/home/tf/perl5/perlbrew/perls/perl-5.29.7/bin:/home/tf/bin:/home/tf/bin:/home/tf/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
XDG_SESSION_TYPE=x11
PWD=/home/tf/bin
LANG=en_US.UTF-8
MANDATORY_PATH=/usr/share/gconf/openbox.mandatory.path
GDM_LANG=en_US
PERLBREW_HOME=/home/tf/.perlbrew
GDMSESSION=openbox
XTERM_VERSION=XTerm(322)
XTERM_LOCALE=en_US.UTF-8
XDG_SEAT=seat0
SHLVL=2
HOME=/home/tf
LANGUAGE=en_US
PERLBREW_MANPATH=/home/tf/perl5/perlbrew/perls/perl-5.29.7/man
LOGNAME=tf
XDG_SESSION_DESKTOP=openbox
PERLBREW_PATH=/home/tf/perl5/perlbrew/bin:/home/tf/perl5/perlbrew/perls/perl-5.29.7/bin
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-2BkdjkW5DB,guid=7cad3cd52080dbce682d3f695e7628b8
XDG_DATA_DIRS=/usr/share/openbox:/usr/local/share/:/usr/share/
LESSOPEN=| /usr/bin/lesspipe %s
XDG_RUNTIME_DIR=/run/user/1000
**DISPLAY=:0**
LESSCLOSE=/usr/bin/lesspipe %s %s
XAUTHORITY=/home/tf/.Xauthority
_=/usr/bin/env
```

Just a wee bit more stuff and I'm not running any DE at all. I prefer a lean GUI.

cron will have even less "environment" than a batch login.  Environment variables control how programs run, where they look for stuff, where they are allowed to access stuff and pretty much anything a programmer wants to be quickly controlled, overridden, by the user.  The PATH and LD_LIBRARY_PATH are critical environment variables for most Linux computers. The PATH works on Linux like it does on Windows, DOS, OSX, Unix ... it provides the shell with a set of directories to search for programs which can be executed without providing the /full/path/to/the/program   Because /bin/ is included in all our PATH variables, any programs in that directory can be run without saying /bin/ls.  ls is located in /bin/ls.  But env is /usr/bin/env, so for that program to work without the full patch, /usr/bin must be in my PATH too. Is it?

---

