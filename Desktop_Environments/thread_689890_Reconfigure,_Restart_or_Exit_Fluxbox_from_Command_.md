---
title: "Reconfigure, Restart or Exit Fluxbox from Command Line?"
date: 2008-02-06
forum: Desktop Environments
---

### Post by mbsullivan on 2008-02-06
Hi All,

I have yet another question for the Fluxbox users... Does anybody know how to restart, reconfigure, or exit Fluxbox from the command line or from a script? In other words, I want to invoke the same action as "Reconfigure", "Restart" and "Exit" from the menu, only without using the menu.

Anybody know? Thanks!
Mike

---

### Post by cknight on 2008-02-07
The easiest way to do this is to use the fluxbox-remote command.  For example, to reconfigure fluxbox use the following:
```
fluxbox-remote "Reconfigure"
```

To use this command you have to edit your init file and enable session.screen<N>.allowRemoteActions first.  You can replace "Reconfigure" with the equivalent menu entries in your menu file (e.g. for exit and restart).

Alternatively, for reconfiguring without allowing remote actions, use this command:
```
kill -s USR2 `xprop -root _BLACKBOX_PID | awk '{print $3}'`
```

Good luck!

---

### Post by mbsullivan on 2008-02-07
Nice! Thanks a lot.

Mike

---

### Post by mbsullivan on 2008-02-12
> 
The easiest way to do this is to use the fluxbox-remote command. For example, to reconfigure fluxbox use the following:
Code:

fluxbox-remote "Reconfigure"

To use this command you have to edit your init file and enable session.screen<N>.allowRemoteActions first. You can replace "Reconfigure" with the equivalent menu entries in your menu file (e.g. for exit and restart).

Alternatively, for reconfiguring without allowing remote actions, use this command:
Code:

kill -s USR2 `xprop -root _BLACKBOX_PID | awk '{print $3}'`

Good luck!

Okay... in my experience, reconfigure works with fluxbox-remote, but restart does not.  The documentation for fluxbox-remote is essentially non-existent, so I may be doing it wrong. That being said, I can get almost all Fluxbox commands to operate through fluxbox-remote, but restart is not one of them.

However, the following will work for "Restart" from the command line:

```
kill -SIGHUP $(xprop -root _BLACKBOX_PID | awk '{print $3}')
```

or, equivalently (but slightly better behaved in scripts):

```
kill -1 $(xprop -root _BLACKBOX_PID | awk '{print $3}')
```

Hope this helps somebody.
Mike

---

### Post by cknight on 2008-02-13
Yes, unfortunately, fluxbox-remote has no documentation.  For those looking for more info on this, #fluxbox on IRC is your best bet.  And thanks for the restart tip.

---

