---
title: "How to set LXTerminal default size?"
date: 2011-11-30
forum: Desktop Environments
---

### Post by _vov_ on 2011-11-30
Hi,
I would like to define the default size for all LXTerminal windows (launched from menu, short-keys etc ).
There is no appropriate option in LXTerminal Preferences.
I assume it could be done by explicit editing of some configuration files.
Would appreciate any solution.
Thanks.

---

### Post by gmargo on 2011-11-30
There's a command line option.
```

lxterminal --geometry=80x50

```You could either edit /usr/share/applications/lxterminal.desktop or copy that file to $HOME/.local/share/applications/ and edit appropriately.

Here's a minimal $HOME/.local/share/applications/lxterminal.desktop
(with all the locale strings removed)
```

[Desktop Entry]
Encoding=UTF-8
Name=LXTerminal
GenericName=Terminal
Comment=Use the command line
TryExec=lxterminal
Exec=lxterminal --geometry=80x50
Icon=lxterminal
Type=Application
Categories=GTK;Utility;TerminalEmulator;

```

---

### Post by _vov_ on 2011-12-01
Thank for tip, but it doesn't work if I launch LXTerminal by shortcut or from another terminal.
Seems it works only(?) if I run terminal from Menu.
I am looking for the way to define the default window size (like 80x25 now) for all LXTerminal instances.
It probably should be done somehow using default X configuration.

---

### Post by raztus on 2011-12-04
@_vov_ I had the same thing where it worked in the Menu, but not the "Application Launch Bar."  I had to go into the settings for the launch bar and delete and re-add "lxterminal" for the launcher to pick up the settings.  To run it from another terminal, you'll always have to call it as 
```
lxterminal --geometry=80x25
```
If you'd like, you could add an alias to your .bashrc (or wherever else you liek to set custom aliases.)  Something like:
```
alias lxterminal='lxterminal --geometry=80x25'
```
Finally, to configure the shortcut (default Ctrl+Alt+T) you'd edit [S]/home/<user>/.config/openbox/lxde-rc.xml[/S] [**Update:** modify ~/.config/openbox/lubuntu-rc.xml instead] and change
[HTML]<command>lxterminal</command>[/HTML]
to
[HTML]<command>lxterminal --geometry=80x25</command>[/HTML]
(You may have to restart openbox [log out] for this to take effect.)

---

