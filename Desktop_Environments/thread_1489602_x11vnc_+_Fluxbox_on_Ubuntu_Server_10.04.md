---
title: "x11vnc + Fluxbox on Ubuntu Server 10.04"
date: 2010-05-21
forum: Desktop Environments
---

### Post by brodyh on 2010-05-21
This is the first time I've tried setting up anything like this before, and I'm not too familiar with X11, etc on Linux so please have patience. :D

I am running Ubuntu 10.04 and would like to have access to Fluxbox over VNC, but would prefer that the x11vnc server not be displayed on the local computer (instead, just show the default command-line). I've searched the Internet and haven't found anything that clearly outlines how to do this.

So far I've installed x11vnc but that's it. What steps do I need to take to get this up and running? I am only looking for a simple GUI to log into, with a web browser, etc.

---

### Post by krunge on 2010-05-21
Maybe you want to use vncserver/Xvnc instead of x11vnc?  That will create a virtual X server that can only be viewed via a vnc viewer (i.e. it won't show up on the physical display.)

---

### Post by brodyh on 2010-05-21
Would I just need to install that as my X server and then install Fluxbox from there?

---

### Post by T.E.N. on 2010-05-21
> **brodyh said:**
> This is the first time I've tried setting up anything like this before, and I'm not too familiar with X11, etc on Linux so please have patience. :D

I am running Ubuntu 10.04 and would like to have access to Fluxbox over VNC, but would prefer that the x11vnc server not be displayed on the local computer (instead, just show the default command-line). I've searched the Internet and haven't found anything that clearly outlines how to do this.

So far I've installed x11vnc but that's it. What steps do I need to take to get this up and running? I am only looking for a simple GUI to log into, with a web browser, etc.An **unsafe** way to get it running with just one line:

Put your password for remote logon into /home/user/.vnc/x11vnc.passwd (unlike -unixpw this will not additionally ask for a user name).

Assign a root password ("mere mortal" users still can't run port 80/443 services on Linux?) using
> sudo passwd root
Set up a /home/user/.vnc/x11vnc.sh which contains
> echo yourrootpassword|sudo -S x11vnc -ssl -rfbport 443 -http_ssl -loop -passwdfile /home/user/.vnc/x11vnc.passwd
Now add /home/user/.vnc/x11vnc.sh to the fluxbox equivalent of GNOME's System/Preferences/Startup Applications, and make sure (haven't checked how this is done in fluxbox rather than GNOME) the system does not require a local logon (so it will fall back on its feet giving you remote desktop access even after a reboot).

Everyone else please chime in with explanations on how to secure this...

---

### Post by krunge on 2010-05-21
> **T.E.N. said:**
> 
Everyone else please chime in with explanations on how to secure this...
I guess there isn't a need to run it on the default https port 443.  E.g. suppose he used "-rfbport 5910", this gets rid of the need for sudo (or similar things.) Then on the viewer side in a java enabled web browser one would use the URL: "https://machinename:5910" instead of "https://machinename".

One should also run "chmod 600" on the /home/user/.vnc/x11vnc.passwd file (to guard against naughty local users; hopefully there are none.)

With both of those I think your scheme is pretty safe.  Do you see anything I am missing?

However, I believe the OP didn't want the X session to appear on the physical monitor (did I understand that correctly?) So that is why I steered toward vncserver/Xvnc.

Of course "x11vnc -create" can emulate vncserver/Xvnc if the "xvfb" package is installed, but it can be a little tricky to set up (especially for a beginner.)  I will be happy to help with that too.

---

### Post by brodyh on 2010-05-21
Yes, I did want to set it up so nothing would display on the physical monitor.

The above posts make sense, but which packages do I need to install prior to doing this (installing Fluxbox, etc.). I have never installed a GUI without having it display on the local physical monitor.

---

### Post by krunge on 2010-05-21
> **brodyh said:**
> 
The above posts make sense, but which packages do I need to install prior to doing this (installing Fluxbox, etc.). I have never installed a GUI without having it display on the local physical monitor.
I won't give you the package names (unless I know them), but rather the command names and let you do the exercise of finding which package.

I will show two ways: one with vncserver/Xvnc and the other with x11vnc/Xvfb

VNCSERVER METHOD:

Get the package with the command 'vncserver'.  Run these commands as your userid:
```

vncserver :1
vncserver -kill :1

```
That should have created ~/.vnc/xstartup.  Edit it with a text editor, and remove a line that looks like
```

twm &

```
and replace it with with
```

fluxbox &

```
Then run this again (still as your userid)
```

vncserver :1

```
This should have started fluxbox in a virtual X server (i.e. not on the monitor) for you.  You can access it from the viewer-side machine via:
```

vncviewer machinename:1

```
where "machinename" is the name of the computer running vncserver.

X11VNC METHOD:

Install the "x11vnc" and "xvfb" packages.  Then run this command as your userid:
```

x11vnc -create -rfbport 5902 -env FD_PROG=/usr/bin/fluxbox -forever

```
Then connect to this vncserver from the viewer-side machine:
```

vncviewer machinename:2

```

When you connect it should create your fluxbox session and show it to you.

Note that I set the X11VNC to run on vnc display 2 so you could have both it and VNCSERVER (on vnc display 1) running at the same time so you could try them out together and without them interfering with eachother.

Depending on your Xvfb version it may fail because (for some silly reason) they removed the '+kb' option to Xvfb.  So if the x11vnc/Xvfb command fails just ask and I will tell you what to try as a workaround.

---

### Post by brodyh on 2010-05-23
The second method failed upon attempting to connect, what's the issue there?

I also tried the first method with vnc4server, and the startup file did not contain a line with fwm. Does that method require a different version of vncserver?

---

### Post by krunge on 2010-05-23
> **brodyh said:**
> The second method failed upon attempting to connect, what's the issue there?
Probably what I mentioned above that they removed the '+kb' option from Xvfb and your x11vnc is still calling Xvfb with this option.  This was fixed in x11vnc 0.9.10. I suppose one could create an Xvfb wrapper script that removes +kb.
> 
I also tried the first method with vnc4server, and the startup file did not contain a line with fwm. Does that method require a different version of vncserver?
maybe paste it here

---

### Post by T.E.N. on 2010-05-23
> **brodyh said:**
> which packages do I need to install prior to doing this (installing Fluxbox, etc.). I have never installed a GUI without having it display on the local physical monitor.If you may have to paste clipboard contents to the VNC server at some point, you might want to "sudo apt-get install autocutsel" to make sure you can (GNOME at least seems to need it, except for just exporting the server's clipboard via VNC).

Also check whether the Alt Gr and Compose keys work for you over VNC before the machine is physically out of reach if you want connect over a WAN.

---

### Post by T.E.N. on 2010-05-26
Deep inside the docs lies this important piece of information at [http://karlrunge.com/x11vnc/x11vnc_opts.html#opt-sslGenCert](http://karlrunge.com/x11vnc/x11vnc_opts.html#opt-sslGenCert):
> Tip: if you know the fully-qualified hostname other people will be connecting to, you can use that as the CommonName "CN" to avoid some applications (e.g. web browsers and java plugin) complaining that it does not match the hostname.
Some clients don't even complain but just stop connecting without comment once the VncClient.jar has been downloaded.

So for SSL one could use something like the following:
> sudo x11vnc -sslGenCA
sudo x11vnc -sslGenCert server self:yourhost.dyndns.org(The Cert invocation, on which you specify not to use a prompt-provoking passphrase if you want x11vnc to autostart later on, requires the CA one to have run, even if you will not be using it.)

In /home/user/.vnc/x11vnc.sh, once you have made sure there is a usable /home/user/.vnc/certs/server-self:yourhost.dyndns.org.sem, replace -ssl with -ssl SAVE-self:yourhost.dyndns.org (NB: the parameter is only the middle part of the file name between and without server- and .pem).

---

