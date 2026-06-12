---
title: "KDE/Plasma does not start automatically anymore"
date: 2011-06-13
forum: Desktop Environments
---

### Post by Monika|K on 2011-06-13
[COLOR=#000000][FONT=Ubuntu]After upgrading my husband's laptop to 11.04, KDE does not start automatically anymore. kdm (the log-in screen) appears. I select "KDE Plasma Desktop". But instead a kind of terminal appears in the top left corner. This console does not have window decoration. When I type **startkde** into it, KDE starts completely normally.[/FONT][/COLOR]

 [COLOR=#000000][FONT=Ubuntu]The same happens with a newly created user, so a misconfiguration in .kde cannot be the cause.[/FONT][/COLOR]
 
 [COLOR=#000000][FONT=Ubuntu]/usr/share/xsessions/kde-plasma.desktop is correct:[/FONT][/COLOR]
 
```
[Desktop Entry]
 Encoding=UTF-8
 Type=XSession
 Exec=/usr/bin/startkde
 TryExec=/usr/bin/startkde
 Name=KDE Plasma Workspace
 Comment=The desktop made by KDE
```[COLOR=#000000][FONT=Ubuntu]The metapackage kubuntu-desktop is installed.[/FONT][/COLOR]

 [COLOR=#000000][FONT=Ubuntu]I have tried reconfiguring and reinstalling various packages that I or others thought might be responsible:[/FONT][/COLOR]
```
 sudo dpkg-reconfigure kdm
 sudo dpkg-reconfigure upstart
 sudo dpkg-reconfigure xserver-xorg
 sudo apt-get install --reinstall kdm
 sudo apt-get install --reinstall plasma-desktop
```[COLOR=#000000][FONT=Ubuntu]GNOME was installed on the same computer, too, and caused some problems after the upgrade (instead of KDE being the default session, it was Unity, but no menus or control bars loaded). After trying all the things mentioned above, I uninstalled all GNOME/Unity-related packages to rule out they were causing the problem (according to that list: [http://wiki.ubuntuusers.de/Desktopumgebung_deinstallieren](http://wiki.ubuntuusers.de/Desktopumgebung_deinstallieren) ). It did not help, even though for two packages messages appeared that sounded like they might make a difference:[/FONT][/COLOR]
 
```
christoph@intellibook:~$ sudo apt-get remove gnome-session
 [...]
 Entfernen von gnome-session ...
 update-alternatives: /usr/bin/startkde wird verwendet, um /usr/bin/x-session-manager (x-session-manager) im Auto-Modus bereitzustellen.
 [...]
  christoph@intellibook:~$ sudo apt-get remove metacity
 [...]
 Entfernen von metacity ...
 update-alternatives: /usr/bin/kwin wird verwendet, um /usr/bin/x-window-manager (x-window-manager) im Auto-Modus bereitzustellen.
 [...]
```I compared with
```
sudo update-alternatives --config x-session-manager
sudo update-alternatives --config x-window-manager
```with my other two computers that work fine after the upgrade to 11.04, they also use startkde and kwin.

Any thoughts what else to try?

---

### Post by Monika|K on 2011-06-24
Any logs I could attach for analysis?

---

### Post by dabl on 2011-06-24
You could try

```
sudo apt-get update && sudo apt-get install --reinstall plasma-desktop
```

No guarantees, of course.

---

### Post by Monika|K on 2011-06-25
See the original posting, I already tried this.

---

### Post by Zorael on 2011-06-25
From what I can tell that should work.

You could try adding some debug statements to the files in **/etc/X11/Xsession.d/**. You want to make sure each file is sourced, and put particular interest in what value **$STARTUP** has before executing it, in **99x11-common_start**.

There was a bug in the 4.6 betas where none of those files were being sourced at all, with key stuff duplicated in **/etc/kde4/kdm/Xsession** instead.

Anyway, from what I can tell the order of execution is;
[list=1][*]**/usr/bin/X**
[*]**/etc/X11/default-display-manager**
[*]**/usr/bin/kdm**
[*]**/etc/kde4/kdm/Xsession** (**Xwilling** and **Xsetup** get run before, but eh)
[*]**/etc/X11/Xsession**
[*]**/etc/X11/Xsession.d/***
[*]**/etc/X11/Xsession.d/99x11-common_start**
[list][*]executes **$STARTUP**, which is **/etc/alternatives/x-session-manager** if everything is as it should, otherwise **/etc/alternatives/x-terminal-emulator**[/list]
[*]**/etc/alternatives/x-session-manager** (**/usr/bin/startkde**)
[*][...][/list]
So make some of the files append a piece of text to a log file in **/tmp** or so, so you can follow the chain.

(Where **/usr/share/xsessions/*** come into play I have no idea. Perhaps it's just there for compatibility reasons?)

---

### Post by Monika|K on 2011-06-25
I don't understand your instructions, can you explain in more detail?

---

### Post by Zorael on 2011-06-25
Oh, hum. By 'adding debug statements' I mean, modify the startup scripts to produce a log about what it's doing, so we can see what's happening and where things go wrong. Let's see...

To the top of **/etc/X11/Xsession**, add a line like this one;
```
#!/bin/sh
#
# /etc/X11/Xsession
#
# global Xsession file -- used by display managers and xinit (startx)

# $Id: Xsession 967 2005-12-27 07:20:55Z dnusinow $

set -e

**[COLOR="Green"]echo "$(date) --- Now in Xsession" >> /tmp/startup.log *#MONIKA*[/COLOR]**

PROGNAME=Xsession

*[...]*
```
At the bottom of the same file;
```
*[...]*

# use run-parts to source every file in the session directory; we source
# instead of executing so that the variables and functions defined above
# are available to the scripts, and so that they can pass variables to each
# other
SESSIONFILES=$(run-parts --list $SYSSESSIONDIR)
if [ -n "$SESSIONFILES" ]; then
  set +e
  for SESSIONFILE in $SESSIONFILES; do
    **[COLOR="green"]echo "Sourcing $SESSIONFILE..." >> /tmp/startup.log *#MONIKA*[/COLOR]**
    . $SESSIONFILE
  done
  set -e
fi

exit 0

# vim:set ai et sts=2 sw=2 tw=80:
```

In **/etc/X11/Xsession.d/50x11-common_determine-startup**;
```
# $Id: 50x11-common_determine-startup 305 2005-07-03 18:51:43Z dnusinow $

# This file is sourced by Xsession(5), not executed.

# If no X session startup program was passed to the Xsession script as an
# argument (e.g., by the display manager), or if that program was not
# executable, fall back to looking for a user's custom X session script, if
# allowed by the options file.

**[COLOR="green"]echo "Now in 50x11-common_determine-startup" >> /tmp/startup.log *#MONIKA*[/COLOR]**

if [ -z "$STARTUP" ]; then
  if has_option allow-user-xsession; then
    for STARTUPFILE in "$USERXSESSION" "$ALTUSERXSESSION"; do
      if [ -e "$STARTUPFILE" ]; then
        **[COLOR="green"]echo "Found user startupfile $STARTUPFILE" >> /tmp/startup.log *#MONIKA*[/COLOR]**
        if [ -x "$STARTUPFILE" ]; then
          STARTUP="$STARTUPFILE"
        else
          shell=${SHELL:-sh}
          STARTUP="$shell $STARTUPFILE"
        fi
        break
      fi
    done
  fi
fi

# If there is still nothing to use for a startup program, try the system
# default session manager, window manager, and terminal emulator.
if [ -z "$STARTUP" ]; then
  **[COLOR="Green"]echo "Setting STARTUP to..." >> /tmp/startup.log *#MONIKA*[/COLOR]**
  if [ -x /usr/bin/x-session-manager ]; then
    [COLOR="green"]**echo "$(readlink /usr/bin/x-session-manager)" >> /tmp/startup.log *#MONIKA***[/COLOR]
    STARTUP=x-session-manager
  elif [ -x /usr/bin/x-window-manager ]; then
    **[COLOR="green"]echo "$(readlink /usr/bin/x-window-manager)" >> /tmp/startup.log *#MONIKA*[/COLOR]**
    STARTUP=x-window-manager
  elif [ -x /usr/bin/x-terminal-emulator ]; then
    **[COLOR="green"]echo "$(readlink /usr/bin/x-terminal-emulator)" >> /tmp/startup.log *#MONIKA*[/COLOR]**
    STARTUP=x-terminal-emulator
  fi
fi

*[...]*
```

In **/etc/X11/Xsession.d/99x11-common_start**;
```
# $Id: 99x11-common_start 305 2005-07-03 18:51:43Z dnusinow $

# This file is sourced by Xsession(5), not executed.

**[COLOR="Green"]echo "Now in 99x11-common_start and $STARTUP is about to be executed" >> /tmp/startup.log *#MONIKA*[/COLOR]**
exec $STARTUP

# vim:set ai et sts=2 sw=2 tw=80:
```
Then save and reboot or otherwise restart kdm. The startup process should now produce a neat log at **/tmp/startup.log** which should tell us what's going on. :3

The worst thing that can happen is that a typo makes the startup scripts fail and X refuses to start. Nothing gets irrevocably broken; it just malfunctions slightly. Since we added *[COLOR="Green"]#MONIKA[/COLOR]* to the end of all our added lines, you can find them by doing a simple textual search and scour them for typing errors. This also makes it easy to revert our changes.

---

### Post by Monika|K on 2011-06-25
Thanks, I will try this.

---

### Post by Monika|K on 2011-08-30
Hi,

I added the debug statements and rebooted the computer. The startup.log file in the tmp folder is not being created :confused:

```
christoph@intellibook-laptop:/tmp$ ls
akonadi-christoph.5s7XHb  ksocket-christoph   virt_1111
kde-christoph             pulse-hEcaYatja7ka  virtuoso_hX1410.ini
kde-root                  pulse-PKdhtXMmr18n
```

I looked at the files again and compared them to what you wrote ... it all looks exactly like in your posting.

```
christoph@intellibook-laptop:/tmp$ cat /etc/X11/Xsession
#!/bin/sh
#
# /etc/X11/Xsession
#
# global Xsession file -- used by display managers and xinit (startx)

# $Id: Xsession 967 2005-12-27 07:20:55Z dnusinow $

set -e

echo "$(date) --- Now in Xsession" >> /tmp/startup.log #MONIKA

PROGNAME=Xsession

message () {
...

```

So what does this tell us? Everything is completely broken, nothing gets called? 
But such a thing should have been fixed by the reconfiguring and reinstalling of kdm etc. I did, shouldn't it?

---

### Post by Zorael on 2011-08-31
Do you have write permissions in **/tmp**? That could otherwise explain much.

```
$ touch /tmp/writetest
$ mount | grep /tmp
```

---

### Post by Monika|K on 2011-08-31
> **Zorael said:**
> Do you have write permissions in **/tmp**? That could otherwise explain much.

```
$ touch /tmp/writetest
$ mount | grep /tmp
```
Yes, I have write permississions in /tmp. touch /tmp/writetest creates a file named writetest in /tmp. ls -l shows drwxrwxrwt for /tmp and the name is underlayed in green ... not sure what the green background color means, but it looks the same way on my other computers.
The output of mount | grep /tmp is empty (like on my other computers that work correctly after the upgrade).

---

### Post by Monika|K on 2011-09-02
Does it make sense to add debug statements to some of the other files mentioned, or is that useless because if /etc/X11/Xsession is not reached nothing is?

---

### Post by Monika|K on 2011-11-01
I upgraded to 11.10. The problem persists. Any ideas?

---

### Post by Monika|K on 2011-11-20
Anyone any idea?

---

