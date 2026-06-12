---
title: "xfwm4 window manager crash"
date: 2011-06-08
forum: Desktop Environments
---

### Post by garethfoxwilliams on 2011-06-08
Many times now when I boot up, xfwm4 seems to crash, leaving me with a static desktop.

I can open a terminal and type:  

**xfwm4**

and it restarts with all its compositing loveliness.

Can anyone please suggest how I can investigate the cause of this and fix it?

---

### Post by Toz on 2011-06-08
There maybe some information in ~/.xsession-errors that might pinpoint the problem. Can you post a copy of the file after a crash?

---

### Post by garethfoxwilliams on 2011-06-08
[FONT=Arial]I had a look at the bug reports for XFCE and saw a suggestion of stopping [/FONT]...
xfwm4-tweaks-settings 
[FONT=Arial]
[/FONT][FONT=System][FONT=Arial]from starting, which maybe I had selected as a useful looking component from Synaptic at one time.

My session seems to start properly now, but I've no idea why that should have been a problem!!
[/FONT][/FONT]

---

### Post by neu5eeCh on 2011-06-08
I've been having the same problem with Xubuntu. To be honest, I don't get the whole session manager business. It doesn't seem to work? Whatever session I try to save, XFCE seems to arbitrarily ignore or follow. It's the one fairly significant flaw in an otherwise ideal DE (for me).

---

### Post by jerrrys on 2011-06-08
auto save session acts erratically for me too, guess its not my Xalpha acting up

---

### Post by neu5eeCh on 2011-06-08
I wonder if the solution is to write a simple script to be executed at startup: xfwm4.

---

### Post by Toz on 2011-06-08
You can add it to the startup applications (Settings Manager->Session and Startup->Application Autostart). 

Have a look in your ~/.cache/sessions folder. There will be a file there called something like **xfce4-session-<your_hostname>:0**. It lists all the saved sessions there. I have xfwm4 listed there. There also might be some backup files in there as well, one that might have a system-specific entry to start xfwm4.

Just noticed there is also a xfwm4 state file there as well. Interesting, it identifies more session startup entries.

---

### Post by neu5eeCh on 2011-06-08
> **Toz said:**
> You can add it to the startup applications (Settings Manager->Session and Startup->Application Autostart). 

Have a look in your ~/.cache/sessions folder. There will be a file there called something like **xfce4-session-<your_hostname>:0**. It lists all the saved sessions there. I have xfwm4 listed there. There also might be some backup files in there as well, one that might have a system-specific entry to start xfwm4.

Just noticed there is also a xfwm4 state file there as well. Interesting, it identifies more session startup entries.

XFWM is "supposed" to start immediately according to the session manager, but frequently doesn't. I'm going to file a bug report.

---

### Post by garethfoxwilliams on 2011-07-13
I appear to have "fixed" the problem by removing Nautilus. I have an idea that Nautilus does something "session-y" which seems to conflict on boot up with something "session-y" to do with Thunar.  You can see I'm very technical !

Nautilus crept into my machine when I installed Dropbox. However, Dropbox does still work fine without Nautilus. You don't get the sync status marks on the icons in Thunar, but I can live without that. It also beats waiting those five seconds or so for Nautilus to start each time!!

---

### Post by kosach on 2011-08-28
hi garethfox,

i have encountered exactly the same problem with dropbox. 
it seems that some synaptic cleanup and invocation of xfwm4 resolved the issue.
i wasn't paying attention, but it is possible that nautilus creeps inside on dropbox install.
nautilus is understandable, but this conflict is not, and should be resolved.

---

### Post by yannigc on 2012-03-15
I also experience a xubuntu window manager crash. here are the symptoms :
no more mouse cursor, or just a cross
no more title bar
no more possibility to bring a window from background to foreground
only one desktop, although it is set to 3 in the settings.

looking deeper :
in the xfce settings, the window manager and window manager tweaks sections are empty.

So, can someone help me, or to reinstall xfwm, on a stable way because the owner of the machine probably won't be able to do it when i'm away,
or to install openbox as a wm in the xfce environment. i like openbox, too.

already thanks,

yannig,

---

### Post by yannigc on 2012-03-15
wll, i'll make questions and answer :

i've clicked "run program" in the menu,

tiped xfwm4

been in sttings, sessions, and saved session. disabled all automatic session saving.

and it works ... nearly but i open a new thread for the new problem, about session manager.

---

