---
title: "Problems with krdp"
date: 2005-06-24
forum: Desktop Environments
---

### Post by ethnicman on 2005-06-24
I am trying to connect to some windows servers using krdp.  However, when I do I do not have use of the keyboard.  I can use rdesktop from the commandline and have it work but only with sudo.  I can use krdp for vnc:// but not rdp://

Any help would be appreciated.

Raoul

---

### Post by dejitarob on 2005-06-24
[QUOTE=ethnicman]I am trying to connect to some windows servers using krdp.  However, when I do I do not have use of the keyboard.  I can use rdesktop from the commandline and have it work but only with sudo.  I can use krdp for vnc:// but not rdp://

Any help would be appreciated.

Raoul[/QUOTE]
 What remote connection software/protocol are your window's boxes using? You could also try the GTK tsclient in the repos.

---

### Post by ethnicman on 2005-06-24
[HTML]
What remote connection software/protocol are your window's boxes using?[/HTML] 

Remote Desktop.  Like I said if I enter sudo rdesktop -a 16 <servername> it works fine.  However, when I use krdp with rdp://servername I connect fine however, I can not use my keyboard in that window.

---

### Post by cwaldbieser on 2005-06-24
One minor point first-- On my installation, the program is called krdc, so I hope we are talking about the same program.

I installed Ubuntu on two different desktop machines.  On my primary, I have no problem using krdc.  On the second, I have a strange problem similar to what you describe.

When the login dialog comes up, I can click the mouse in it, but the keyboard does not produce and characters (so I can't log in).  However, if I click on the fullscreen/window button, I can type again.  The down side of this is that if I try to set the window back to full screen mode, the window just maximizes, it doesn't take up the full screen (so kicker is still showing for example, and I still have to use scroll bars to see the entire remote desktop).

---

