---
title: "Can't unlock Login Screen (gdmsetup)"
date: 2012-04-03
forum: Desktop Environments
---

### Post by santosh83 on 2012-04-03
Hello all,

Running Ubuntu 10.10 64-bit.

I've just noticed that the Login Screen window (System->Administration->Login Screen) does nothing when I attempt to click 'Unlock' for making modifications.

As per directions in a 2 year old thread in this forum where someone had the same issues, I've tried 'gksu gdmsetup', 'sudo gdmsetup', and 'ck-launch-session gdmsetup', all with equally futile results.

I'm including below the messages gdmsetup prints to screen when started from a terminal emulator, when I invoke it simply as 'gdmsetup.' I'm sorry it's such a verbose output, but I've highlighted the specific message which is output when I click 'Unlock.'

```
santosh@santosh-desktop:~$ gdmsetup

** (gdmsetup:22107): WARNING **: Error calling GetSoundEnabled(): The name org.gnome.DisplayManager was not provided by any .service files

** (gdmsetup:22107): WARNING **: Error calling GetFaceBrowserEnabled(): The name org.gnome.DisplayManager was not provided by any .service files

** (gdmsetup:22107): WARNING **: Error calling GetValue('daemon/TimedLoginEnable'): The name org.gnome.DisplayManager was not provided by any .service files

** (gdmsetup:22107): WARNING **: Error calling GetValue('daemon/TimedLoginDelay'): The name org.gnome.DisplayManager was not provided by any .service files
** (gdmsetup:22107): DEBUG: init delay=30
** (gdmsetup:22107): DEBUG: "/usr/share/xsessions/une-efl-guest-restricted.desktop" is hidden or contains non-executable TryExec program

** (gdmsetup:22107): DEBUG: "/usr/share/xsessions/guest-restricted.desktop" is hidden or contains non-executable TryExec program

** (gdmsetup:22107): DEBUG: "/usr/share/xsessions/une-guest-restricted.desktop" is hidden or contains non-executable TryExec program


** (gdmsetup:22107): WARNING **: Error calling GetValue('daemon/DefaultSession'): The name org.gnome.DisplayManager was not provided by any .service files
** (gdmsetup:22107): DEBUG: Init default session found:'(null)'
** (gdmsetup:22107): DEBUG: GdmUserManager: Found current seat: /org/freedesktop/ConsoleKit/Seat1
** (gdmsetup:22107): DEBUG: GdmUserManager: running 'ck-history --frequent --seat='Seat1' --session-type='''
** (gdmsetup:22107): DEBUG: GdmUserManager: explicitly skipping user: nobody
** (gdmsetup:22107): DEBUG: GdmUserManager: user icon changed
** (gdmsetup:22107): DEBUG: adding monitor for '/home/santosh/.face'
** (gdmsetup:22107): DEBUG: Getting list of sessions for user 1000
** (gdmsetup:22107): DEBUG: Found 1 sessions for user santosh
** (gdmsetup:22107): DEBUG: GdmUser: adding session /org/freedesktop/ConsoleKit/Session1
** (gdmsetup:22107): DEBUG: GdmUserManager: sessions changed user=santosh num=1
** (gdmsetup:22107): DEBUG: GdmUserManager: added session for user: santosh
** (gdmsetup:22107): DEBUG: GdmUserManager: history output: santosh  930

** (gdmsetup:22107): DEBUG: GdmUserManager: history output: nobody   16

** (gdmsetup:22107): DEBUG: GdmUserManager: excluding user 'nobody'
** (gdmsetup:22107): DEBUG: GdmUserManager: history output: root     2

** (gdmsetup:22107): DEBUG: GdmUserManager: excluding user 'root'

** (gdmsetup:22107): WARNING **: Error calling GetValue('daemon/AutomaticLoginEnable'): The name org.gnome.DisplayManager was not provided by any .service files

** (gdmsetup:22107): WARNING **: Error calling GetValue('daemon/TimedLoginEnable'): The name org.gnome.DisplayManager was not provided by any .service files

** (gdmsetup:22107): WARNING **: Error calling GetValue('daemon/TimedLogin'): The name org.gnome.DisplayManager was not provided by any .service files
** (gdmsetup:22107): DEBUG: init user='(null)' auto=False

**** (gdmsetup:22107): WARNING **: Failed to unlock: The name org.gnome.DisplayManager was not provided by any .service files**
santosh@santosh-desktop:~$ 

```

The same error (The name org.gnome.DisplayManager was not provided by any .service files) seems to occur almost throughout... 

Can anyone suggest what I should do further? Thanks for the help!

---

