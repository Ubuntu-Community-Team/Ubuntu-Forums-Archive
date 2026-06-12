---
title: "xfce4-keyboard-shortcuts shortcuts stop working after some time"
date: 2017-03-08
forum: Desktop Environments
---

### Post by leozinho29_eu on 2017-03-08
Hello

I am using Xubuntu 16.04.2 on my notebook and, after some event which I don't know what is, the keyboard shortcuts configured for xfce4-keyboard-shortcuts and multimedia keys of xfce4-volumed stop working. With this problem, I am not able to open the terminal with Ctrl+Alt+T or mute the volume with the Mute key for example. 

The keyboard shortcuts configured with xfwm4 are not affected. 

This happens with every Xubuntu version I have tested (14.04+) on every computer I have tested. This may happen after 30 minutes, may happens after 60 hours (tested it). Happens when using xfwm4 mixing lxde and xfce4 too, tested on another computer. To solve it on both cases, I have to finish the session and enter the session again. 

Syslog, dmesg and .xsession-errors had no error messages specific to any element of the xfce4, or it is not shown. 

This is pretty annoying and I have found nothing like this when searching on internet, so I am asking here. 

Is there one particular application that, if I restart, restore the xfce4-keyboard-shortcuts shortcuts? Is there something I can do to prevent this error on xfce4 sessions and sessions with xfce4 elements?

Thank you.

---

### Post by Habitual on 2017-03-09
Did you try utilizing Ctrl+Alt+F[123456] as well?
The desktop may be locked up or busy, but the console should respond.

If you save sessions on logout, I'd  open a terminal and clean them using
```
rm -fr ~/.cache/sessions/
```
and logout and back in as your usual self.
Observe keyboard...
If that fails to produce satisfactory results,

Create a new user on the system and login as the new user.
Observe and report.
This should give the keyboard some "defaults" that you can measure.
This will tell us if it's the system or the user and one of their ~/.config file settings.

---

### Post by leozinho29_eu on 2017-03-18
The Ctrl+Alt+Fnumber shortcuts works, as the xfwm4 shortcuts (as Alt+Tab). The only ones that don't work are the ones configured with the xfce4-keyboard-shortcuts and the multimedia keys (xfce4-volumed). I don't save my sessions, and how it happens after a significant time after the boot, I believe it's not a error loading information from cache, but even choosing to not save, there were files in .cache/sessions.

When I log out and return, the keyboard shortcuts go back to normal, but my goal would be:

Ideally: no bug happens;

Not ideal but interesting: one program which I restart and the shortcuts work again, with no need to log out.

Logging out is not always a option.

Regarding the new user: even a new user can experience this problem. It happens after some event on the system, which I don't know which one is, as I have found nothing related on any logs. The most strange thing I have seen soon after I noticed the shortcuts stopped working were some LightDM messages after a cron task on journalctl. 

I will try to read again the log files after the error happens, to see exactly what messages appears. Is there a log specific to xfce informations somewhere?

Thank you.

---

