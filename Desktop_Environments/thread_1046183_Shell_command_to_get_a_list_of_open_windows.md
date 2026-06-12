---
title: "Shell command to get a list of open windows?"
date: 2009-01-21
forum: Desktop Environments
---

### Post by rrwo on 2009-01-21
If there a shell command that will query the list of open windows (akin to the X11::XTops perl module)?

I am trying to write a script that runs the terminal with a different colour scheme depending on how many windows are already open.  

I currently use a hack to check processes, but it requires that each window be a spearate process, and it cannot differentiate between workspaces. (I only care about the number of open windows in a specific workspace.)

I'd rather use an existing command or package that write my own.

---

### Post by kaibob on 2009-01-21
I am not knowledgeable on this topic, but I use wmctrl for a somewhat similar purpose. The following is a part of the description of this command:

> wmctrl  is a command that can be used to interact with an X Window manager that is  compatible  with  the  EWMH/NetWM  specification. wmctrl  can  query  the window manager for information, and it can request that certain window management actions be taken.

The following is an example of the output with the -l option:

> kaibob@dell:~$ wmctrl -l
0x00e00003 -1 dell Bottom Expanded Edge Panel
0x00e00029 -1 dell Top Expanded Edge Panel
0x0120001e -1 dell Desktop
0x020000bc  0 dell Ubuntu Forums - Search Results - Mozilla Firefox
0x012000df  0 dell autosave - File Browser
0x02400003  0 dell default.ncd - NoteCase 1.7.9 [/home/kaibob/documents/default.ncd]
0x0280004b  0 dell Untitled1 - OpenOffice.org Writer 
0x02200021  0 dell kaibob@dell: ~

BTW, wmctrl does distinguish between different "desktops." If this is different from workspaces, then perhaps wmctrl will not be of help. Also, wmctrl is not installed by default in Hardy but is in the repo's.

---

### Post by rrwo on 2009-01-21
Thanks! That should do the trick.

I found 'xlsclients' but it doesn't seem to give as much information.

---

