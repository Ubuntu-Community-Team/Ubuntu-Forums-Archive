---
title: "Bitvise xterm SSH Client not able to open Remote Desktop"
date: 2013-09-01
forum: Desktop Environments
---

### Post by Peter_Sotos on 2013-09-01
*hrumph*

Bitvise xterm SSH Client not able to open Remote Desktop. All that happens when I try to Remote Desktop connect is that I get a shell as I would when I normally use Bitvise in terminal mode. When I do an startx from the bitvise SSHed in terminal, it launches the Desktop on the linux box (I can see the monitor from my PC station). LOL

I tried this:
[COLOR=#000000][FONT=Verdana]The problem is with debian default setup. It sets it up so that only root can log into X. In order to change this you need to edit the /etc/X11/Xwrapper.config file. For the syntax of that, check out the man page for 'Xwrapper.config'. All you need to add is the 'allowed_users=anybody' option.[/FONT][/COLOR]

I also tried this:

[LIST=1]
[*]sudo stop lightdm (or kdm or gdm instead if you installed kubuntu or GNOME shell)
[*]sudo Xorg -configure
[*]sudo start lightdm (or kdm or gdm instead if you installed kubuntu or GNOME shell)
[/LIST]
:(

I have some more info:
I see these errors in the Bitvise command window:
02:28:57.906 Auto opening xterm terminal session.
02:28:57.906 Auto opening Remote Desktop session.
02:28:57.911 Listening for Remote Desktop client-2-server connection on 127.0.0.1:19593 succeeded.
02:28:57.914 Remote Desktop Connection launched successfully.
02:29:05.899 Accepted Remote Desktop client-2-server connection from 127.0.0.1:64857 to 127.0.0.1:3389.
02:29:05.901 Server rejected our attempt to open a Remote Desktop client-2-server connection - reason: SSH_OPEN_CONNECT_FAILED, description: Connection refused.
02:29:05.906 Closing Remote Desktop client-2-server connection from 127.0.0.1:64857 to 127.0.0.1:3389, sent: 0, received: 0.
02:29:34.864 Closing xterm terminal session.


Any help would be greatly appreciated!

Peter

---

### Post by Peter_Sotos on 2013-09-01
Anyone? Anyone? Bueller? :)

I have made progress! I am able to login via XMing I get single windows but no Desktop client. I think I was successful with XMing because I specified Display "1" instead o "0". There is no such setting in bitvice. I would REALLY like to see the entire desktop. Anyway, I KNOW there is an X11 guru on here! Want to help me solve this challenge? I am close!

----------------

New update:
I am getting this from Bitvise:
Xming :0 -clipboard 


XdmcpRegisterConnection: newAddress 10.0.x.xx
winCheckDisplayNumber - Xming is already running on display 0


Fatal server error:
InitOutput - Duplicate invocation on display number: 0.  Exiting.


winDeinitMultiWindowWM - Noting shutdown in progress
-------------------------------
Another update:
Here is a view of my Xming widow. I am getting something just missing the rest of the desktop. I am launching a single program xterm, and then launching graphical apps from there but I am missing the whol desktop background and docking bar. I think I am close, please help! So tired! I have been working on this thing since yesterday. :(
[IMG]http://Fireballmm.com/X11_launching_problem.png[/IMG]
[IMG]http://Fireballmm.com/MissingFont.png[/IMG]

Again any help is much appreciated!

Peter

---

