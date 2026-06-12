---
title: "Xming - can't connect to 8.10"
date: 2009-03-02
forum: General Help
---

### Post by tiger.woods on 2009-03-02
I'm trying to connect to my Ubuntu box 8.10 from my XP box using xming but all I get I can get is a terminal window no actual desktop?

I'm guessing I want to connect using XDMCP but frankly am unsure of what the choices represent?

Any help would be appreciated.

Thanks.

TW,

---

### Post by km4hr on 2009-03-03
Tiger,

I have not tried using Xming with Ubuntu but I have not been able to get it to work with a CentOS 5 Linux server either.

XDMCP is a great choice if you want to log in to your Ubuntu server from a Windows PC. When using XDMCP you will get a GUI login screen on your PC just like the one you have when you are sitting at the local Ubuntu console. After you log in you won't know that you're not actually sitting at the system console. I have used Xming/XDMCP in past years and it worked very well. But I suspect something is now broken.

I haven't been able to find anyone that currently uses XDMCP with Xming. It seems everyone is using VNC instead. I can't even confirm that Xming works with XDMCP because I haven't found a single user on several forums. This applies not only to Xming but to other x-servers including cygwin/x and X-Win32, a commercial Xserver. None of these works on my Windows XP machine

XDMCP is typically easy to set up. Since I haven't done it on an Ubuntu machine I can't give you the exact steps. In CentOS there is a GUI setup screen for activating XDMCP. I presume it's the same for Ubuntu. CentOS also has a screen for opening the ports you mentioned.

I'll be very interested to find out if you get this to work. It appears that something in the Windows XP networking environment is blocking the connections that Xming requires. I've worked with it for days with no luck.

I hope you get it to work. If not you may have to do what I'm about to do. That is, give up on Xming/XDMCP and try VNC instead.

---

### Post by Slim Odds on 2009-03-03
> **km4hr said:**
> I haven't been able to find anyone that currently uses XDMCP with Xming. It seems everyone is using VNC instead. I can't even confirm that Xming works with XDMCP because I haven't found a single user on several forums. This applies not only to Xming but to other x-servers including cygwin/x and X-Win32, a commercial Xserver. None of these works on my Windows XP machine

I use cygwin/x and it works fine.

I put a pretty complete cygwin on my windows machines (makes it almost useable).

---

### Post by km4hr on 2009-03-04
> **Slim Odds said:**
> I use cygwin/x and it works fine.

I put a pretty complete cygwin on my windows machines (makes it almost useable).

Are you using XDMCP with cygwin/x?

---

### Post by Slim Odds on 2009-03-04
> **km4hr said:**
> Are you using XDMCP with cygwin/x?

Yes....

I have had times where GDM acted strange. In those cases, I used KDM.

---

### Post by HermanAB on 2009-03-04
Usually, Xming is used together with PuTTY to connect to a SSH server.

Xming on its own is just a console - it doesn't actually 'do anything', until you connect to a Linux machine using PuTTY and run gnome-panel or something.

Cheers,

Herman

---

### Post by Slim Odds on 2009-03-04
> **HermanAB said:**
> Usually, Xming is used together with PuTTY to connect to a SSH server.

Xming on its own is just a console - it doesn't actually 'do anything', until you connect to a Linux machine using PuTTY and run gnome-panel or something.


Not with XDMCP. It gives you the entire experience (i.e., almost just like logging in at the console).

---

### Post by tiger.woods on 2009-03-04
Well I never got Xming to work and ultimately tried vnc and ultravnc, I've currently stuck with ultravnc since it allows scaling.

The box I'm connecting to has a different screen resolution and on my Windows box I had to use the scrollbars which sucked.

I've got to tell you that I don't know what the difference is between XDMCP and VNC, I assume they are different. Since I was able to connect with UltraVNC I believe I installed the VNCServer at some point.

TW,

---

### Post by dbcomp on 2009-04-20
What you want is Xlaunch, which is part of XMing. 
0. I'm assuming you have XDMCP enabled on your Ubuntu box?
1. launch XLaunch
2. select "1 window", next
3. "Open session via XDMCP", next
4. Connect to host <enter your hostname or IP here>, next
5. (don't change anything on this screen), next
6. Save configuration, probably using the name of the server you're connecting to.
7. select "Finish" and it will launch a full desktop GUI

At step 4, you can also search for willing to host a session, but I've always specified where I want to go.

Good luck.

David

---

