---
title: "Title bar disappears"
date: 2010-11-29
forum: Desktop Environments
---

### Post by DawgMan on 2010-11-29
10.04 on a Dell D830 4 GB ram NVIDIA video card.

For some reason, every once in a while, I lose the title bar on all my windows.  I can't click and drag any windows anywhere. I have to re-boot to fix this problem.  (it happens maybe once a week)

Any ideas?

---

### Post by stinkeye on 2010-11-29
Don"t know how to fix your problem but
Alt+F2
```
gtk-window-decorator --replace
```
should bring your titlebar and border back without a need to reboot.

---

### Post by DawgMan on 2010-11-29
Thanks.  I'll try that next time.

---

### Post by matt_symes on 2010-11-29
Hi

I remember reading a post on here of a person that had the same problem as you.

Their solution was to install fusion-icon and add it as a start up program. 

Or you could try adding the command by the previous poster as a start up command.

Maybe one will work.

I seem to remember both solutions were proposed.

Kind regards

---

### Post by stinkeye on 2010-11-29
> **matt_symes said:**
> Hi

I remember reading a post on here of a person that had the same problem as you.

Their solution was to install fusion-icon and add it as a start up program.
Yes, I forgot about fusion-icon.
May solve it.
On previous releases of Ubuntu I used **fusion-icon -n** as the command in
startup applications.
The **-n** option tells it not to load a window manager as it should boot into your last used window manager anyway.

On Maverick, however I started using just **fusion-icon** as the command in
startup applications for the very reason you describe.
Has never failed to load the gtk-window-decorator.

Once you've got fusion-icon installed and running, right click on the tray
icon and select compiz as the window manger.

Then check in compizconfig-settings-manager > Effects > Window Decoration
that you have this in the **Command** box.
```
gtk-window-decorator --replace
```

---

### Post by DawgMan on 2010-11-29
Thanks,  I added fusion-icon. 

I upgraded from 9.10 to 10.04 last week. I figured I had Thanksgiving week off so if something went wrong I would have all week to fix it.

Of course, many things went wrong.  Now I have left to fix all my desktop stuff like compiz and widgets etc.  Every time I upgrade it seems grub gets hosed and I lose my customs. I purposely waited until 10.10 was out before upgrading to 10.04.  Oh well...... ;) 

I'll get there.

Thanks for the help.

---

