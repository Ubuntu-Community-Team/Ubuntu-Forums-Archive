---
title: "Compiz *directly* on startup"
date: 2007-11-09
forum: Desktop Effects &amp; Customization
---

### Post by flip79 on 2007-11-09
Hello!

I got Compiz Fusion working in KDE, on my Dell Laptop ^_^

I'd like to have Compiz start as default window decorator, without having to boot in kwin and then replacing it with **compiz-fusion --replace** . It would be speedy and nice (the screen flickers when the system is replacing kwin with compiz) and it should fix the famous problem of adept_notifier popping-out of the systray.

Someone know how to do it? :)

Thank you in advance and excuse me for my english!!!

---

### Post by flip79 on 2007-11-11
Please :/

---

### Post by TadH on 2007-11-11
go to system preferences and sessions, and ad it to the list ;)

---

### Post by FuturePilot on 2007-11-11
I haven't used KDE in a while, but I think you need to make a script and put it in your .KDE/autostart/ directory.
Probably something like
```
#! /bin/bash
exec compiz --replace
```
Save it as something like start_compiz.sh 
Then do a ```
chmod +x start_compiz.sh
```
on it to make it executable.

---

### Post by flip79 on 2007-11-12
Doesn't this make compiz "replace" kwin? I'd like to make it start as the initial windows decorator... :/

---

### Post by Zorael on 2007-11-12
Yes, doing that will only make it launch and replace kwin.

What if you replaced it, then saved your session, and set it up to always load that one?

That failing, there's an interesting comment in /usr/bin/startkde.

```
# finally, give the session control to the session manager
# see kdebase/ksmserver for the description of the rest of the startup sequence
# [b]if the KDEWM environment variable has been set, then it will be used as KDE's
# window manager instead of kwin.
# if KDEWM is not set, ksmserver will ensure kwin is started.[/b]
# kwrapper is used to reduce startup time and memory usage
# kwrapper does not return usefull error codes such as the exit code of ksmserver.
# We only check for 255 which means that the ksmserver process could not be 
# started, any problems thereafter, e.g. ksmserver failing to initialize, 
# will remain undetected.
test -n "$KDEWM" && KDEWM="--windowmanager $KDEWM"
kwrapper ksmserver $KDEWM 
if test $? -eq 255; then
  # Startup error
  echo 'startkde: Could not start ksmserver. Check your installation.'  1>&2
  xmessage -geometry 500x100 "Could not start ksmserver. Check your installation."
fi
```

man page for startkde, empasized parts in bold:
```
startkde(1)                                                               startkde(1)

NAME
       startkde - Starts up the KDE Desktop Environment

SYNOPSIS
       startkde

DESCRIPTION
       This manual page documents briefly the startkde command.  This manual page was
       written for the Debian distribution because the original program does not have
       a manual page.

       The  startkde  script starts up the K Desktop Environment and is typicaly exe&#8208;
       cuted by your login manager (e.g. xdm, gdm, kdm, wdm or from  your  X  startup
       scripts).  startkde in turn launches ksmserver, which will load your last ses&#8208;
       sion, or a default session that includes the standard KDE programs if no saved
       session is available.

       startkde,  with ksmserver, is a standard X11R6 session manager that can manage
       any X11R6 SM compliant program.

       startkde and ksmserver use the contents of the ~/.kde directory  for  starting
       previously saved sessions. [b]Source scripts found in ~/.kde/env/*.sh can be used
       to define environment variables that will be available to all KDE programs.[/b]

       For anything else (that doesn&#8217;t set env vars, or that needs a window manager),
       better use the ~/.kde/Autostart folder.

       At  the  end  of  a session, the scripts found in ~/.kde/shutdown will be exe&#8208;
       cuted.
```

I haven't tried this, but wouldn't it be possible to place a script in ~/.kde/env/*.sh that set the environment variable $KDEWM to a compiz startup script?

---

### Post by shivathreya on 2008-01-04
I don't know whether you have got the answer for this.

I have an ATI mobility radeon X1600 with AIGLX. I use the following in .kde/env/kdewm.sh

#!/bin/bash
export LIBGL_ALWAYS_INDIRECT=1
export KDEWM=/usr/bin/compiz

And it works perfectly.

I added this to /usr/bin/compiz

COMPIZ_OPTIONS="--replace --sm-disable --ignore-desktop-hints ccp --indirect-rendering"

Shiva

---

