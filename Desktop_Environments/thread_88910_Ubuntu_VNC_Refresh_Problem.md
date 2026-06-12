---
title: "Ubuntu VNC Refresh Problem"
date: 2005-11-11
forum: Desktop Environments
---

### Post by firefly2442 on 2005-11-11
Hello. Under "System", "Preferences", "Remote Desktop" on Ubuntu... there's a nice little window to setup VNC. This works great except when I login there's refresh problems. I'll open things and move windows around and nothing will show up or it will be messed up. I believe it's a refresh issue but I'm not sure how to fix it. Could it be the fact that I'm using tightvncserver? Thanks in advance.

---

### Post by Teutons on 2006-02-16
I have the exact same problem... Where you able to fix it?

---

### Post by [HUN]Levente on 2006-02-16
Same problem here.
No advanced Ubuntu user had a problem like this? :)

---

### Post by QwizzTest on 2006-02-16
[QUOTE=firefly2442]Hello. Under "System", "Preferences", "Remote Desktop" on Ubuntu... there's a nice little window to setup VNC. This works great except when I login there's refresh problems. I'll open things and move windows around and nothing will show up or it will be messed up. I believe it's a refresh issue but I'm not sure how to fix it. Could it be the fact that I'm using tightvncserver? Thanks in advance.[/QUOTE]



What client are you using?

---

### Post by [HUN]Levente on 2006-02-16
[QUOTE=QwizzTest]What client are you using?[/QUOTE]

realvnc, winxp

---

### Post by simon0t7 on 2006-02-18
hm. I have the same problem too

---

### Post by ronmarley1 on 2006-02-18
I use the TightVNC client, Fast Compression and it works fine into Redhat ES4 and Ubuntu Breezy.

---

### Post by simon0t7 on 2006-02-18
will try that ....

---

### Post by simon0t7 on 2006-02-18
tried tightvnc as my viewer, no difference

---

### Post by [HUN]Levente on 2006-03-06
Noone can solve this problem? It's very annoying...

---

### Post by QwizzTest on 2006-03-13
[QUOTE='[HUN]Levente']Noone can solve this problem? It's very annoying...[/QUOTE]

What are your connection speeds (local and remote)?  

What are your realVNC viewer settings?

---

### Post by [HUN]Levente on 2006-03-14
[QUOTE=QwizzTest]What are your connection speeds (local and remote)?  

What are your realVNC viewer settings?[/QUOTE]

Which is local and which is remote? :)

So, where the VNC server runs: 2560/512kbit/s
Where the VNC client is: 100/100mbit/s

I don't think the connection speed could be the problem...

I tried to set VNC viewer to lower color depth and no wallpaper, but it didn't help...

---

### Post by Divide By Zero on 2006-08-28
I'm having the same problem.  Trying to control my office computer (Ubuntu - Dapper) with the living room laptop (WinXP RealVNC or TightVNC) over 10/100.  It used to work on a previous installation of Dapper between these machines.  I didn't muck with VNC on the Dapper machine this time before it broke.  I've tried color depths, etc.  Requesting screen refreshes through both clients doesn't do any good.

---

### Post by _hannu on 2006-09-12
My VNC infact did worked OK, but then I installed Ati video drivers (becauce of resume problems). After that I have the same problem...
-Hannu

---

### Post by Alcopops on 2007-02-06
similar problem here, I can establish a session, my remote desktop is displayed, but it will not refresh, even if you prompt it to in the client.

I've tried the default edgy vnc server and tightvnc server (from repositories) i get the same each time. I've also tried it from the same box via gome-rdp and accross the internet from an xpbox using tightvncviewer; same result.

I have nvidia drivers installed and beryl if that makes a difference.

Possibly there is an incompatibility somewhere but, being a noob, i wouldn't know where to start looking

hope theres some experts who can help.

peace out,

Jaime

---

### Post by Alcopops on 2007-02-08
Update to my last post,

Vnc server at least the default edgy one (Libvncserver?) will not work with beryl desktop manager. If you have it running and don't get screen updates but do get a connection. Try switching back to metacity. Worked for me!!

Libvncserver is dead slow though so I will give tightvncserver a go since it performed well on win32.

cheers,

Jaime

---

### Post by martinitime1975 on 2007-03-09
It's not perfect, but I think I have an answer.  I have the exact same problems with remote desktop on my ubuntu dapper box, and trying to connect to it using realvnc from windows.  The problem is with the :0 desktop (the one you see if you're using the machine directly).  Try this:

In ubuntu, run this at the command prompt:

realvncserver -geometry 1280x1024 -depth 16

You may be prompted to specify a password, if not it's either yours or the root password (you'll need this when you connect with the vnc viewer).  You should get some output that lists the new vnc session server name, i.e.  server:1  (instead of the default, server:0)

Using a vnc viewer, connect using that new server name   server:1  (1 is the session number.  Every time you invoke vncserver, it creates a new unique session, until you kill them with vncserver -kill :1 or whatever session you need to kill).  

You should get a clean desktop and the refresh problem goes away.  Let me know what you think.

---

### Post by [HUN]Levente on 2007-03-10
Thanks, this helped for me.

---

