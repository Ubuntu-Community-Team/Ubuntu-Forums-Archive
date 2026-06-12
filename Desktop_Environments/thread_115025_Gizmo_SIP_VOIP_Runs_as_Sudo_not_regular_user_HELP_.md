---
title: "Gizmo SIP VOIP: Runs as Sudo not regular user HELP THE NOOB -  1 Hour Ago
Please help"
date: 2006-01-09
forum: Desktop Environments
---

### Post by bennettg on 2006-01-09
I wanted to use the gizmoproject sip/voip (like skype). I followed the directions on their page for debian install:

To install Gizmo Project on Debian, the following Debian packages must be installed in order:

1. Bonjour - A networking library from Apple. More information can be found here.
2. libsipphoneapi - This is the main library for Gizmo Project, it is common to all of our versions.
3. gizmo-project - This file is specific to the Linux version, and contains the User Interface

I used the sudo ppkd -i XXXXXXX.deb command

After installing the 3 files, I try to run gizmoproject as a regular user and I get this error:

KDEInit could not launch 'audiowrapper'.:
Could not find 'audiowrapper' executable.


But when I run gizmo as root, the program launches just fine.


what am i doing wrong. please help this nooob. i tried to search the forum, but didnt find an answer. the forums on the gizmoproject site did not help either,

---

### Post by souki on 2006-01-09
same problem

the command defined by the shortcut is:
audiowrapper --oss-native gizmo
but the audiowrapper command is missing

I've tried to launch gizmo from a terminal and it is working: account, sound ok
I didn't try with someone yet, so I don't know if full dulpex is working

---

### Post by bennettg on 2006-01-10
[QUOTE=souki]same problem

the command defined by the shortcut is:
audiowrapper --oss-native gizmo
but the audiowrapper command is missing

I've tried to launch gizmo from a terminal and it is working: account, sound ok
I didn't try with someone yet, so I don't know if full dulpex is working[/QUOT

problem solved.  add gizmo shortcut to the desktop or panel.  right click to configure and goto command.  change audiowrapper --oss-native gizmo  to just gizmo.  it works

---

