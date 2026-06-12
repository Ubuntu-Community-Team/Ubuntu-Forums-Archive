---
title: "Xfce &quot;xfce4-notes-plugin&quot; missing on upgrade to Xubuntu 23.04"
date: 2023-07-25
forum: Desktop Environments
---

### Post by Saptarshi_Roy on 2023-07-25
[COLOR=#000000][FONT=&quot]Dear Xubuntu Team[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Recently, I've upgraded to Xubuntu 23.04 from Xubuntu 22.04 using the 'software updater' tool.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Post upgrading, the "xfce4-notes-plugin" is missing from the list of applications, and as a result it can also not be added to the panel.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]My computer details are as follows:[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Xfce 4.18
GTK version: 3.24.37
Kernel version: 6.2.0-25-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Please redress this with the highest priority.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Thank you![/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]--[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Kind regards,
Saptarshi Roy[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2023-07-25
First off this is a user forum, no members of development look here.
Secondly:
```
apt policy xfce4-notes-plugin
xfce4-notes-plugin:
  Installed: 1.9.0-1
  Candidate: 1.9.0-1
  Version table:
 *** 1.9.0-1 500
        500 http://archive.ubuntu.com/ubuntu lunar/universe amd64 Packages
        100 /var/lib/dpkg/status

```
```
uname -r
6.2.0-26-generic

```
Did you look first:
```
apt search xfce notes
Sorting... Done
Full Text Search... Done
xfce4-goodies/lunar 4.18.0 amd64
  enhancements for the Xfce4 Desktop Environment

xfce4-notes/lunar 1.9.0-1 amd64
  Notes application for the Xfce4 desktop

xfce4-notes-plugin/lunar 1.9.0-1 amd64
  Notes plugin for the Xfce4 desktop

```

---

