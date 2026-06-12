---
title: "Use RDP (Terminal Services) to connect to ubuntu"
date: 2006-08-22
forum: Desktop Environments
---

### Post by fermulator on 2006-08-22
Hello!

So I've been working at this for several hours now, and I'm hoping that someone here might help me find what I'm looking for.


_My Scenario:_
**Server** - *ubuntu 6.06 server* (With ubuntu-desktop installed)
**Client** - *Windows XP Pro* (SP2)

I'm looking for "Remote Desktop" abilities to manage my ubuntu server using X (The GUI).

_Options:_
[LIST=1]
**VNC** (using any VNC client) - Works.  But requires an X session to already be started.  I know you can have the server auto-login a user, then lock screen immediately...but this solution really isn't ideal compared to NX and RDP.
[*]**NX** (freenx, nxserver) ([www.nomachine.com](www.nomachine.com)) - Works!  But requires the Windows client to install nxclient.
[/LIST]


Is there a way to have the Windows client connect to ubuntu using the RDP protocal?

i.e.  Using "mstsc" in Windows, seemlessly remote desktop to the ubuntu server without installation additional software on the client side?

I hope I've explained what I'm looking for well enough.

---

### Post by revertex on 2007-01-08
to manage a server?

ssh, surelly you don't need more than CLI, just download putty on windoze.

---

### Post by Rhubarb on 2007-01-08
You can get vnc to work at the gdm login screen on your server:
[http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

---

### Post by dcstar on 2007-01-08
> **fermulator said:**
> Hello!

So I've been working at this for several hours now, and I'm hoping that someone here might help me find what I'm looking for.


_My Scenario:_
**Server** - *ubuntu 6.06 server* (With ubuntu-desktop installed)
**Client** - *Windows XP Pro* (SP2)

I'm looking for "Remote Desktop" abilities to manage my ubuntu server using X (The GUI).
........

This looks to still be in Beta:

[http://sourceforge.net/projects/xrdp](http://sourceforge.net/projects/xrdp)

---

### Post by trinaryouroboros on 2007-02-13
I can't believe noone's come up with a solution to this one...

What's the big idea? 

I mean, we have rdesktop for linux, which connects to RDP enabled Windows workstations, why can't we get things working in reverse?

[insert I.T. admins strike poster here]

:-k

---

### Post by Jabran Asghar on 2007-02-13
> **dcstar said:**
> This looks to still be in Beta:

[http://sourceforge.net/projects/xrdp](http://sourceforge.net/projects/xrdp)

I have been using this one and its pretty good. Only that the default keyboard is US and I cann't change that to other. You use standard MS Terminal Server client to connect to Ubuntu Box. Installation of XRDP is pretty simple. The underlying is XVNC though (I think ...). Therefore, will be heavy over the Internet, but on LAN its nearly flawless :-)

---

### Post by localzuk on 2007-02-13
What do you need to do with the graphical front end on this server? :S

---

### Post by revertex on 2007-02-13
> **trinaryouroboros said:**
> 

[insert I.T. admins strike poster here]

:-k

with ssh, screen, fish protocol, fuser, nfs, sshfs, keychain, and all these overkill tools(toys), why do you need rdesktop?

---

### Post by fermulator on 2007-02-13
Firstly...."why" isn't really important is it?
...but...since some people want to know, i shall answer!

The biggest issue is portability.
The majority of 'public' systems available are Windows based.

If I have a Linux server, in order to remotely connect to it we need to download tools (be it vnc client, ssh, etc.).  This is 'inconvenient' to say the least.

Imagine if we could use the built in "mstsc" (Remote Desktop Application) that is built in with all Windows (XP or later) and immediately connect to the graphical system of Linux!

We all know of the other ways of doing this, but the most efficient and convenient way is really to use the remote desktop appilcation.

No matter what system we go to, as long as it's Windows XP or later, we're good to go!
[LIST]
* "Windows Key"+"R"
* "mstsc"
* Press Enter
[/LIST]
Bing!  And there we have it, a session with a Linux machine.

Makes sense yes?
Now that we've addressed the "why", perhaps we can move on to the "how"!

---

### Post by dcstar on 2007-02-13
> **fermulator said:**
> Firstly...."why" isn't really important is it?
...but...since some people want to know, i shall answer!
.........
Makes sense yes?
Now that we've addressed the "why", perhaps we can move on to the "how"!

The "how" has already been answered, and by someone who is actually using it.

---

### Post by revertex on 2007-02-14
I'm just asked "why" because i'm curious about your reason to use mstsc.
Unless you are in your lan, RDP is only usable if you get a pretty fast internet  connection on both sides.

At least for me it's not so usable, most part of time i can't do some work without getting nervous with the slowness.

Not count that i need to close all apps that are using internet (both client and server side), and connect to  only one remote desktop at time.

on the other hand with ssh i can connect to a bunch of servers without a need  to close my downloads, radio or p2p.

---

### Post by trinaryouroboros on 2007-02-14
> **Jabran Asghar said:**
> I have been using this one and its pretty good. Only that the default keyboard is US and I cann't change that to other. You use standard MS Terminal Server client to connect to Ubuntu Box. Installation of XRDP is pretty simple. The underlying is XVNC though (I think ...). Therefore, will be heavy over the Internet, but on LAN its nearly flawless :-)

It sounds fun, but, busy as I am I haven't had a moment to investigate a Real how-to for ubuntu regarding this one...

> **localzuk said:**
> What do you need to do with the graphical front end on this server? :S

What do you need rdesktop for with Windows? I think this is a moot question.

> **revertex said:**
> with ssh, screen, fish protocol, fuser, nfs, sshfs, keychain, and all these overkill tools(toys), why do you need rdesktop?

Boy, am I glad I bumped this one!

> **fermulator said:**
> Firstly...."why" isn't really important is it?
...but...since some people want to know, i shall answer!

The biggest issue is portability.
The majority of 'public' systems available are Windows based.

If I have a Linux server, in order to remotely connect to it we need to download tools (be it vnc client, ssh, etc.).  This is 'inconvenient' to say the least.

Imagine if we could use the built in "mstsc" (Remote Desktop Application) that is built in with all Windows (XP or later) and immediately connect to the graphical system of Linux!

We all know of the other ways of doing this, but the most efficient and convenient way is really to use the remote desktop appilcation.

No matter what system we go to, as long as it's Windows XP or later, we're good to go!
[LIST]
* "Windows Key"+"R"
* "mstsc"
* Press Enter
[/LIST]
Bing!  And there we have it, a session with a Linux machine.

Makes sense yes?
Now that we've addressed the "why", perhaps we can move on to the "how"!

Actually, let me clarify the "why" - you see, people get so busy in life they just die for a lazy way out of things. That's me right now. I'm being lazy, and instead of installing any software on every single Windows computer I go to, just to see my own ubuntu desktop on the LAN...I'd rather have one program that emulates RDP perfectly.

I've yet to find a how-to on this, that fits the bill, and I find it hard to believe XRDP is still in Beta a year later...

> **dcstar said:**
> The "how" has already been answered, and by someone who is actually using it.

Not really.

> **revertex said:**
> I'm just asked "why" because i'm curious about your reason to use mstsc.
Unless you are in your lan, RDP is only usable if you get a pretty fast internet  connection on both sides.

At least for me it's not so usable, most part of time i can't do some work without getting nervous with the slowness.

Not count that i need to close all apps that are using internet (both client and server side), and connect to  only one remote desktop at time.

on the other hand with ssh i can connect to a bunch of servers without a need  to close my downloads, radio or p2p.

Yes, if you are working with a connection that is weaker than 128kbps...your RDP will probably be as useful as a moldy potato. Fortunately I'm dealing with LAN / high-speed connections here in New York, so I'm trying to focus on RDP to simplify my across-platform access.

XRDP seems a proper way...but, I'll be damned if I can get it even compiled right. It would be nice if there was a package for this...oops, that's me being a lazy *** again.

----

By the way, off topic, I just got beryl working on a machine, and this is strange: rdesktop and gnome-rdp is like...transparent. Which is cool! At the same time, however, it's annoying because you can't control the transparency value.

I don't know how I accomplished this...but, I'll pop whatever config files you want to examine up for review.

---

### Post by Jabran Asghar on 2007-02-14
"How":
[http://ubuntuforums.org/showthread.php?p=1851701](http://ubuntuforums.org/showthread.php?p=1851701)

---

### Post by catchmeifyoutry on 2008-01-19
Hi, this is how I used to do it, it requires SSH login to your linux (ubuntu) box with X11 forwarding enabled and running a low-weight X server on your windows machine.
So it's not exactly RDP, but it does enable you to use graphical applications, and start a desktop session if you start nautilus.

Download Xming server for windows:
[http://sourceforge.net/projects/xming](http://sourceforge.net/projects/xming)

also download Putty (you can get it at the xming downloads I believe).
When the Xmin server is installed, start it and it will show up as a tray icon. You don't notice anything else yet because no graphical X11 applications have been connected to it yet.

Now start Putty, and enter the address of your linux machine, BUT before you connect, go to Connection -> SSH -> X11 and check the "Enable X11 forwarding" checkbox.
Then, save your session. Next time loaded, it will automatically set the X11 forwarding option again.

When you now use the SSH session and start an X11 application, the graphical stuff will be forwarded over the secure SSH connection to the Xming server running in windows.
If you start nautilus& in the terminal it will give you a desktop.

Unfortunately, I'm not really sure how you can connect to a running X session, to continue an existing desktop session. Maybe some guru on the forums knows?
I guess you can also start gnome-panel, etc. in the putty SSH session.

Hope it is of some help,
cheers.

---

### Post by jikonen on 2008-06-05
I myself use FreeNX with the java applet client.

I haven't yet setup this on ubuntu but I have a job for a company that wanted a ubuntu freenx/nx based server using the java applet as client. This would atleast make the client installation transparent. Also the client parameters are provisioned from the server so the only thing u need to type in is the webaddress then login and password to logon

You might want to lookup this... the information to setup the java applet is on nomachine website. almost all things work fine in combination with FreeNX server part.

This works fine atleast here in .no and .se since all clients have java installed by default.

Br
Jouni Ikonen

---

