---
title: "What happened to gdmflexiserver?"
date: 2009-10-30
forum: Desktop Environments
---

### Post by valadil on 2009-10-30
Hi.  I use a shell script instead of the user switch applet to switch between mine and my fiancee's accounts.  I just upgraded to karmic and now I get "no longer supported" errors when I run my script.  There's no manpage and the help option is notably pathetic:

```

~$ gdmflexiserver -help
Usage:
  gdmflexiserver [OPTION...] - New GDM login

Help Options:
  -h, --help                Show help options

Application Options:
  -c, --command=COMMAND     Ignored - retained for compatibility
  -n, --xnest               Ignored - retained for compatibility
  -l, --no-lock             Ignored - retained for compatibility
  -d, --debug               Debugging output
  -a, --authenticate        Ignored - retained for compatibility
  -s, --startnew            Ignored - retained for compatibility
  --monte-carlo-pi          
  --version                 Version of this application

```

For what it's worth I use gdmflexiserver for three commands:
```

gdmflexiserver -c CONSOLE_SERVERS
gdmflexiserver -a -l -c "FLEXI_XSERVER"
gdmflexiserver -a -l -c "SET_VT $VT"

```

Is there another way to get gdmflexiserver to run these commands?  How about another program that accomplishes the same thing?  We just want userswitching without passwords that doesn't depend on gnome-panel (or any other panel to hold an applet).  Oh and yes I already know about ctrl-alt-f7/8.  I haven't been able to convince her to use it though.

Thanks!

---

