---
title: "Remote Desktop Viewer"
date: 2008-12-13
forum: General Help
---

### Post by Law506 on 2008-12-13
Hi,

I have a server setup running Ubuntu 8.10 32-Bit Server and I installed the ubuntu desktop onto it for a gui.

When I go to connect to the server through my desktop, which is running Ubuntu 8.10 64-Bit Desktop, I can see the server and connect to it but I just get a black screen.

When I run the command in terminal, "vinagre HomeServer:0" it displays this error,

Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `GtkStatusbar::shadow-type' of type `GtkShadowType' from rc file value "((GString*) 0x1223280)" of type `GString'

I haven't the faintest clue to what this is, anyone else seen this or know what actions I need to take to resolve this? 

Thanks.

---

### Post by jpkotta on 2008-12-15
Do you have a VNC server running on the remote host?  That's the way I've always done it.  Here is a script I use to start a server with ssh and then tunnel the vnc traffic through ssh.  You need openssh-server and x11vnc on the remote host.
```
#!/bin/bash

usage="$0 [user@]remote_host [<DISPLAY>]"

login="$1"
if [ -z "$login" ] ; then
    echo $usage
    exit 1
fi

disp="$2"
if [ -z "$disp" ] ; then
    disp=:0
fi

ssh "$login" "x11vnc -localhost -display '$disp' -scale 4/5 -bg" 
vncviewer -via "$login" localhost"$disp"
```

---

### Post by Law506 on 2008-12-16
Actually, yesterday I was reading around and saw someone mention the Login Window properties and it clicked my head, duh, go look at the remote tab, didn't even think about this when I went to the remote desktop selection on Preferences.

Well, enabled remote logins there as well, and bam, works likes a charm.

Thanks for the script. I'll look at it, but as of now I got GnomeRDP and its working great for my windows connections and my Ubuntu Server. which I got using VNC.

Also, Remote Desktop Viewer works as well, so I am good now on all fronts.

Thanks for the help though.

---

