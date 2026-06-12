---
title: "Multi Gnome Terminal"
date: 2007-02-20
forum: Desktop Environments
---

### Post by CarlosinFL on 2007-02-20
I installed "Multi-Gnome-Terminal" using APT as a replacement for Gnome terminal and it installed fine with no dependencie problems. My question now is how do I start using this application?

[http://multignometerm.sourceforge.net/](http://multignometerm.sourceforge.net/)

I ran the following command:

```
carlos@lptp:~$ sudo update-alternatives --config x-terminal-emulator

There are 6 alternatives which provide `x-terminal-emulator'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/xterm
          2    /usr/bin/uxterm
          3    /usr/bin/koi8rxterm
          4    /usr/bin/lxterm
 +        5    /usr/bin/gnome-terminal.wrapper
*         6    /usr/bin/multi-gnome-terminal.wrapper

Press enter to keep the default[*], or type selection number:
```

As you can see "6" is my default now with the change but I still don't see it. Do I need to reboot?

---

### Post by Jeremy23 on 2007-02-21
I would imagine all you need to do is go to System > Preferences > Preferred Applications and select your new terminal in one of the options there.

---

