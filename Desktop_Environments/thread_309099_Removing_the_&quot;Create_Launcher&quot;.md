---
title: "Removing the &quot;Create Launcher&quot;"
date: 2006-11-29
forum: Desktop Environments
---

### Post by tigershark on 2006-11-29
Hi

When I rightclick on the desktop, can I remove the option "Create Launcher" from the list?

I know that you can do a similar thing in winxp with tweakui, I hope you know what I mean and that you can help me :neutral:

---

### Post by suoko on 2007-12-10
I'm interested in this issue too..
Any way to do it?

---

### Post by suoko on 2007-12-10
this is the last thing I need to do to lockdown a workstation for kiok user after I applied the following:

Hide filesystem to nautilus:
 - Open a terminal and execut "ls -1 / | sudo tee /.hidden"
 - Do "sudo chmod a+r .hidden"

Disable CTRL+ALT+BACKSPACE adding the following to xorg.conf:
Section	"ServerFlags"
Option	"DontZap"	"yes"
EndSection

Disable all shortcuts:
gnome-keybinding-properties

Disable log-out, swtich user,:
gconf-editor -> apps -> gnome-session -> logout-prompt

[SIZE="5"][COLOR="Red"]UPDATE:
I found the solution:[/COLOR][/SIZE] [SIZE="1"](thanks to alex found on #nautilus in gimpnet irc channel.)[/SIZE]
modify  /usr/share/nautilus/ui/nautilus-desktop-icon-view-ui.xml    
and add *hidden="true" * to line:
<menuitem name="New Launcher" action="New Launcher Desktop"/>

in this way:
<menuitem name="New Launcher" action="New Launcher Desktop" hidden="true"/>

---

