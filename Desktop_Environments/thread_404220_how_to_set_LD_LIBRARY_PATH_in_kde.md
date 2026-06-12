---
title: "how to set LD_LIBRARY_PATH in kde?"
date: 2007-04-08
forum: Desktop Environments
---

### Post by Jens7677 on 2007-04-08
Hello,

I have some additional variables I want to set for kde. I have created a .kde/env/variables.sh script where I add some dirs to PATH and LD_LIBRARY_PATH. I can see the changes in PATH but not the ones for LD_LIBRARY_PATH. It seems it gets unset somewhere during loading the desktop via gdm. Does anyone has an idea how I can set LD_LIBRARY_PATH for the desktop?

(I know about .bashrc and that works fine for a terminal, but I want that for the desktop as well.)

Regards,
Jens

---

### Post by ynnhoj on 2007-04-08
could there be any other scripts (maybe ~/.xsession or something in a hidden configuration folder in ~/) that are also being executed when you log in?  you might want to poke around in your home directory if you haven't already.

failing that idea, can you post your script?  maybe there's a little mistake in it you've missed..?

---

### Post by Jens7677 on 2007-04-08
Thank you very much for taking the time to answer.

My ~ folder is clear I guess, I don't have a .xsession or .xinitrc script. I do think that my script is fine, because I just pasted most of the stuff from my .bashrc, but I could have indeed missed something:

```

#!/usr/bin/env bash
xsetwacom set stylus Button2 3
xsetwacom set stylus Button3 2

export PATH=$PATH:/opt/svn/bin:/opt/jdk/bin:/opt/mono/bin:~/usr/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/svn/lib:/opt/jdk/lib:/opt/mono/lib:~/usr/lib
export LIBRARY_PATH=$LD_LIBRARY_PATH

export MOZILLA_FIVE_HOME=/usr/lib/firefox
export SCUMMVM_PORT=17:0

```

If I run the 'set' command inside K->Run command [run in terminal] I can see the following output:

```

COLORTERM=''
DBUS_SESSION_BUS_ADDRESS='unix:abstract=/tmp/dbus-0xQd3JH53z,guid=4e481946d929970994f20735c6563700'
DESKTOP_SESSION='kde'
DISPLAY=':0'
GDMSESSION='kde'
GDM_XSERVER_LOCATION='local'
GS_LIB='/home/jpeters/.fonts'
HOME='/home/jpeters'
IFS='
'
KDE_FULL_SESSION='true'
KDE_MULTIHEAD='false'
KDE_NO_IPV6='TRUE'
KONSOLE_DCOP='DCOPRef(konsole-6772,konsole)'
KONSOLE_DCOP_SESSION='DCOPRef(konsole-6772,session-1)'
LANG='en_US.UTF-8'
LANGUAGE='en_US:en_GB:en'
LIBRARY_PATH=':/opt/svn/lib:/opt/jdk/lib:/opt/mono/lib:~/usr/lib'
LOGNAME='jpeters'
MOZILLA_FIVE_HOME='/usr/lib/firefox'
OPTIND='1'
PATH='/opt/kde3/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/opt/svn/bin:/opt/jdk/bin:/opt/mono/bin:~/usr/bin'
PPID='6772'
PS1='$ '
PS2='> '
PS4='+ '
PWD='/home/jpeters'
SCUMMVM_PORT='17:0'
SESSION_MANAGER='local/wkst01:/tmp/.ICE-unix/5421'
SHELL='/bin/bash'
SSH_AGENT_PID='5366'
SSH_AUTH_SOCK='/tmp/ssh-ThVSHT5316/agent.5316'
TERM='xterm'
USER='jpeters'
USERNAME='jpeters'
WINDOWID='44040199'
XAUTHORITY='/home/jpeters/.Xauthority'
XCURSOR_THEME='Human'
XDG_CONFIG_DIRS='/opt/kde3/etc/xdg/'
XDG_DATA_DIRS='/opt/kde3/share/'
  
```

As you can see everything is there, expect LD_LIBRARY_PATH.
Any ideas

---

### Post by Jens7677 on 2007-04-10
any ideas?

---

### Post by mukau on 2008-04-01
one year later, and nobody has an answer to this silly little problem that now bugs me too?

---

### Post by artfwo on 2008-04-01
This problem bugs many people, me included :) after some research (a year ago as well) I've found out that something well hidden in Debian/Ubuntu unsets LD_LIBRARY_PATHs, exported from ~/.bashrc/profile for extra security... To workaround this, I either:
[LIST=1]
[*]Compile with LDFLAGS=-Wl,-rpath,/path/to/libraries
[*]Include LD_LIBRARY_PATH in executions scripts (e.g. for games)
[*]Write my own wrapper scripts that set LD_LIBRARY_PATH and run the application :)
[/LIST]

By the way, exporting LD_LIBRARY_PATH in ~/.bashrc makes it appear in Terminal environments (AFAIK), but not in the "toplevel" GNOME session, so you can run your application from the GNOME terminal, if that does not trouble you :)

---

