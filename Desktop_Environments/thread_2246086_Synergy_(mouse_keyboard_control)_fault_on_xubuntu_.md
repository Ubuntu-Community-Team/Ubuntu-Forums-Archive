---
title: "Synergy (mouse keyboard control) fault on xubuntu 14.04"
date: 2014-09-28
forum: Desktop Environments
---

### Post by aspidistra on 2014-09-28
tried synergy from 14.04 was working to 12.04 client

command from server is 'synergys" (with synergy.conf file set up)

command from client is 'synergyc   <ip address>

get message "[COLOR=#333333][FONT=monospace]2014-04-24T15:40:17 INFO: Synergy 1.4.12 Client on Linux 3.14.0-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]031400-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]generic #201403310035 SMP Mon Mar 31 04:36:23 UTC 2014 x86_64[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace] /build/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]buildd/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]synergy-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]1.4.12/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]src/lib/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]synergy/[/FONT][/COLOR][COLOR=#333333][FONT=monospace]CClientApp.[/FONT][/COLOR][COLOR=#333333][FONT=monospace]cpp,164"

synergy doesn't communicate

appears to be a bug [/FONT][/COLOR]https://bugs.launchpad.net/ubuntu/+source/quicksynergy/+bug/1312184

the report says this -- unhelpful (what update????)

I updated everything on 14.04 problem still exists.  

whats "mir" .. this hasn't been addressed .. synergy must be used by multiple users

[COLOR=#333333][FONT=Ubuntu][TABLE]
[TR]
[TD][Yura (ykuchinskiy)]("https://launchpad.net/~ykuchinskiy") wrote on 2014-06-09:[/TD]
[TD="class: bug-comment-index"][#6]("https://bugs.launchpad.net/ubuntu/+source/quicksynergy/+bug/1312184/comments/6")[/TD]
[/TR]
[/TABLE]

[FONT=monospace]I should say that after the following update of my ubuntu 14.04 system, everything gets back to normal!
[/FONT]

[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu][TABLE]
[TR]
[TD][Václav Šmilauer (eudoxos)]("https://launchpad.net/~eudoxos") wrote on 2014-06-10:[/TD]
[TD="class: bug-comment-index"][#7]("https://bugs.launchpad.net/ubuntu/+source/quicksynergy/+bug/1312184/comments/7")[/TD]
[/TR]
[/TABLE]

[FONT=monospace]I resolved the issue by installing all *mir* packages -- I noticed in ps -A that Xorg was run with some mir option. After uninstalling all libraries related to mir, everything works smoothly again. (Keyboard lag was also resolved by that, which is not a part of this bugreport).
This report should be kept open (perhaps re-assigned to mir) until it is resolved properly, though.
[/FONT]

[/FONT][/COLOR]

---

### Post by aspidistra on 2014-09-28
i may be able to fix this in about 10 minutes


have been looking at (changed), wrong configuration  file)


will report back

its not an "error message" (although somebody has reported it as a bug (?))

the server issues similar messages .. just referring to a line of the script

---

### Post by aspidistra on 2014-09-28
was my problem change host in cofiguration file - sorry

---

