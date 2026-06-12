---
title: "Smoother remote desktop"
date: 2005-11-16
forum: Desktop Environments
---

### Post by mikko.ohtamaa on 2005-11-16
Hi,

Gnome built-in remote desktop support (VNC) doesn't always work smoothly (graphics drawing is too slow) and it's hard to customize. Here is a trick I use to get a better remote desktop support. My first shot was to make real remote X11 session, but I couldn't get it to work with Cygwin XServer and Gnome :(

With this trick, you get
- Smoother remote desktop graphics
- Different settings for remote desktop and local desktop
- Smaller resolution and color depth than in normal desktop usage

1. Create a new user for remote desktop sessions

2. Install Tightvnc package. Tightvnc creates a new X session for a remote desktop, so it doesn't conflict with normal desktop usage. Tightvnc required a bit customization for Ubuntu

In /etc/vnc.conf, put

> 
$XFConfigPath = "/etc/X11/xorg.conf"


Otherwise you get "no fixed font found" erros in your ~homedir/.vnc/log file when you try to start VNC session.

You can also tweak geometry and pixel depth settings (less graphical data to transfer makes graphics drawing faster):

> 
$geometry = "800x600";
$depth = "16";


3. Run Tightvnc server under a newly created user. This way desktop settings don't collide with your local desktop user.

4. Connect to your Tightvnc server. The port might not be the default VNC port. Port numbering starts from 5001 (5001 for the first tightvnc, 5002 for second, etc...)

5. You should be able to login to X-session with one terminal window open. Type "gnome-session" to launch Gnome.

6. Disable the wallpaper (speeds up VNC quite a lot, since bitmap image transfering is expensive)

If you want to start tightvnc server remotely (it's not always running), you can install OpenSSH daemon and use SSH to connect to your box to launch tightvnc

---

### Post by jdong on 2005-11-16
Also consider FreeNX (see seveas.ubuntulinux.nl for .deb packages) -- it provides acceptable remote desktop performance even on dial-up connections!

---

### Post by VR6Pete on 2005-11-16
FreeNX does indeed rock!

---

### Post by wbeck85 on 2005-11-16
I'll support the statements above about freenx. Not to take away from your helpful hint concerning tightvnc, but try out freenx Definately pretty cool

---

### Post by jrennard on 2005-11-17
Greetings!

Not meaning to hijack this thread, but how would I go about getting FreeNX to work going from a Windows (Gasp) PC to my Ubuntu box?

I use my Ubuntu box for all my web servers, databases, etc.  It is in my rackmount and I get sick of having to walk back there to do stuff...

I'm getting somewhat familiar with command line, so it isn't a huge problem, but sometimes I like to get on the desktop to go do downloads and that sort of thing.

And/Or if you could shoot me a location of commands for command line tasks that would be great too!  Thanks!

---

### Post by Roman27 on 2005-11-17
[QUOTE=jrennard]... how would I go about getting FreeNX to work going from a Windows (Gasp) PC to my Ubuntu box?
...[/QUOTE]

Try this...
[http://freenx.berlios.de/clients.php](http://freenx.berlios.de/clients.php)

---

### Post by LinuxWiz83 on 2005-12-06
doesn't it use the same password as the user your login with because my password keeps being rejected?

---

### Post by puccaso on 2005-12-28
is there anyway to get freenx to connect to a currently running vnc session and still out preform the others?

i can close the vnc client and re-connect whenever i like
i cant do that with freenx, so what gives?

---

