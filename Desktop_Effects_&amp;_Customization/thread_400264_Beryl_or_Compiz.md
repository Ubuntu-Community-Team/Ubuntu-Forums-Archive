---
title: "Beryl or Compiz"
date: 2007-04-03
forum: Desktop Effects &amp; Customization
---

### Post by Fillibuster on 2007-04-03
I'm a new user, and I've been trying for the last couple days to get Beryl or Compiz going.  I had beryl at first and it worked fine, until I restarted the computer.  Then whenever I tried opening beryl-manager, the computer would lock up and not respond.  So I removed Beryl and tried Compiz.  Now that I have Compiz I got to open compiz.tray.icon and get the following...

```
alex@Fillibuster:~$ compiz-tray-icon

(compiz-tray-icon:5489): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:5489): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(compiz-tray-icon:5489): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:5489): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
```

I have a 7800GTX and have the "nvidia" driver.  Any ideas on why neither of these want to work?

---

### Post by H3g3m0n on 2007-04-03
Make sure that opengl is correctly enabled with 'glxinfo | grep -i direct', it should say yes.

I keep having to reinstall the nvidia drivers when the kernels update but I'm using the official nvidia drivers from the nvidia site not the Ubuntu repo ones which are more likely to autoupdate without problems.

When x locks up, try hitting 

Alt+SysRq+R
Alt+F1
which will switch you to a terminal.

or if that doesn't work
Alt+SysRq+R
Alt+SysRq+K
Alt+F1
should preform a fatality on xorg and drop you to a terminal, so you can restart xorg without restarting all of Ubuntu '/etc/init.d/gdm restart'

You might also take a look at the logs while in the terminal to see if anything of interest shows up.

(SysRq is also the Print Scr key)

---

### Post by Fillibuster on 2007-04-03
I ran that command in my terminal and it came back 'No'.  How do I go about enabling that?

---

### Post by Fillibuster on 2007-04-03
I uninstalled Compiz and was able to reinstall Beryl and it's working fine.  Thanks guys.

---

