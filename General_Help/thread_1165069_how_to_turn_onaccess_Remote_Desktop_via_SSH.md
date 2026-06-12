---
title: "how to turn on/access Remote Desktop via SSH"
date: 2009-05-20
forum: General Help
---

### Post by TMcKSmith on 2009-05-20
I'm running Ubuntu Server 8.10.  Last night I installed the "gnome-core" package because I had to run some software via GUI.  After I ran the command "startx" I started up the software and left it running all night.  When I woke up this morning I forgot to check the status of the program so I was wondering if there's a way I can SSH into my server (I already do this regularly), turn on "Remote Desktop" and then view my screen from my laptop at work.  Please note:  I am running Ubuntu 9.04 here at work.  Any help would be appreciated

---

### Post by TMcKSmith on 2009-05-20
hmm, I've made some progress:

I SSH'd into my server and ran this command:
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true

Then on my work laptop, I went to Applications > Internet > Remote Desktop Viewer

When I try to access my server, it says myserver:5900 closed.

I'm thinking because port 5900 is blocked here at work, but I'm not 100% sure.  I'm aware of what ports are open, how can I change which port it uses?

---

### Post by HermanAB on 2009-05-20
Howdy,

You are being way too complicated.  Simply do this:
$ ssh -X -C -c blowfish user@server "gedit /etc/fstab"

or this:
$ ssh -X -C -c blowfish user@server gnome-panel

and go click happy.

---

### Post by geirha on 2009-05-20
Have a look at [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

### Post by TMcKSmith on 2009-05-20
> **HermanAB said:**
> Howdy,

You are being way too complicated.  Simply do this:
$ ssh -X -C -c blowfish user@server "gedit /etc/fstab"

or this:
$ ssh -X -C -c blowfish user@server gnome-panel

and go click happy.

I ran these commands from my work laptop...

the first one just brought up my server's fstab file
the second just replaced my laptop's bottom panel with an old grey-looking one (which my server's xserver coincidentally has) - but it didn't have any of the programs my server is running, just my local terminal

---

### Post by jameshogan on 2009-06-12
Wow!  Just installed NXserver on an Ubuntu 9.04 machine, and the nx client on a Windows XP machine, an after following the Ubuntu instructions, the two programmes work like a dream.  I've got my Ubuntu system running like I'm RDPing to it from my XP machine.  The full desktop, and all the works.  Excellent!

---

