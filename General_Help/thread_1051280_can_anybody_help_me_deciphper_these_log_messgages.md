---
title: "can anybody help me deciphper these log messgages"
date: 2009-01-26
forum: General Help
---

### Post by Post Monkeh on 2009-01-26
```
Jan 26 20:27:32 will-laptop gdm[5310]: pam_unix(gdm:session): session closed for user will
Jan 26 20:28:41 will-laptop gdm[5276]: pam_unix(gdm:session): session opened for user will by (uid=0)
Jan 26 20:28:41 will-laptop gdm[5276]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Jan 26 20:28:41 will-laptop gdm[5276]: gnome-keyring-daemon: couldn't lookup keyring component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Jan 26 20:28:41 will-laptop gdm[5276]: Autolaunch error: X11 initialization failed.
Jan 26 20:28:41 will-laptop gdm[5276]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Jan 26 20:28:41 will-laptop gdm[5276]: Autolaunch error: X11 initialization failed.
Jan 26 20:28:41 will-laptop gdm[5276]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Jan 26 20:28:41 will-laptop gdm[5276]: Autolaunch error: X11 initialization failed.
Jan 26 20:28:41 will-laptop gdm[5276]: )
Jan 26 20:29:08 will-laptop sudo: pam_unix(sudo:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=will
Jan 26 20:33:01 will-laptop sudo:     will : TTY=unknown ; PWD=/home/will ; USER=root ; COMMAND=/usr/sbin/firestarter
Jan 26 20:34:12 will-laptop sudo:     will : TTY=pts/0 ; PWD=/home/will ; USER=root ; COMMAND=/sbin/ifup -a
Jan 26 20:34:18 will-laptop sudo:     will : TTY=pts/0 ; PWD=/home/will ; USER=root ; COMMAND=/sbin/ifdown -a
Jan 26 20:34:22 will-laptop sudo:     will : TTY=pts/0 ; PWD=/home/will ; USER=root ; COMMAND=/sbin/ifup -a
Jan 26 20:34:29 will-laptop gdm[5276]: pam_unix(gdm:session): session closed for user will
Jan 26 20:35:52 will-laptop gdm[5278]: pam_unix(gdm:session): session opened for user will by (uid=0)
Jan 26 20:35:52 will-laptop gdm[5278]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Jan 26 20:35:52 will-laptop gdm[5278]: gnome-keyring-daemon: couldn't lookup keyring component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Jan 26 20:35:52 will-laptop gdm[5278]: Autolaunch error: X11 initialization failed.
Jan 26 20:35:52 will-laptop gdm[5278]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Jan 26 20:35:52 will-laptop gdm[5278]: Autolaunch error: X11 initialization failed.
Jan 26 20:35:52 will-laptop gdm[5278]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Jan 26 20:35:52 will-laptop gdm[5278]: Autolaunch error: X11 initialization failed.
Jan 26 20:35:52 will-laptop gdm[5278]: )
Jan 26 20:36:19 will-laptop sudo: pam_unix(sudo:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=will
Jan 26 20:36:31 will-laptop sudo: pam_unix(sudo:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=will
Jan 26 20:36:43 will-laptop sudo:     will : TTY=unknown ; PWD=/home/will ; USER=root ; COMMAND=/usr/sbin/firestarter
```

that is my auth log for a start/shutdown/restart.  the firestarter entrys were manually activated by me.  let me explain.  

i've been having several different issues over the past couple of days, and to be honest i can't remember in which order they came in.

i had installed kubuntu/xubuntu desktops to try, but decided to stick with ubuntu for a while, so i removed them.  unfortunately, some part of the kde desktop was running and at some point during the removal procedure my computer just froze (admittedly i did select the option to continue myself thinking it would be some background service or would complete the uninstallation following a reboot)

also i was trying to figure a way to be able to use sudo from any account with the same password (ie everyone has their own password, but to use sudo one common password could be used from within the terminal), and decided after some advice to set up another admin account that i could "su" into from a terminal in any account without having to give out my own password.  unfortunately i decided to name this account "admin", so i then stuffed up my own permission settings.  i managed to get in and select all the permission "check" boxes to give me my permissions back, but in my panic i forgot to take down the default settings.
plus i've no idea if me making the admin account stuffed up the admin group.  i have added my own main account (will) to the will group and admin groups (both tick boxes for my user were unchecked before and i'm afraid to put them back to that way now :D)

long story short, the main problem i'm having is that when i load up my computer, i cannot access the internet. my network connects ok, but i can't do anything (even ping my router) until i load a firewall program (i've tried gufw & firestarter, both work ok, even if i immediately disable them once loaded). once a firewal program is loaded, everything works ok.

i've asked about the internet problem in the network forums, and the permissions problems in the security forums, but i'd just like someone to explain the logs to me in case i've got yet another problem.

a re-install might be called for :(

---

