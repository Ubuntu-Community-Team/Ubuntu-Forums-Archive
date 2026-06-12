---
title: "How to setup remote X clients"
date: 2009-02-12
forum: General Help
---

### Post by aajax on 2009-02-12
Can anyone point me to instructions on how Ubuntu ought to be setup for permitting the use of remote (located on another machine on my own LAN) X clients?

---

### Post by geirha on 2009-02-12
Could you be more specific? do you want to run an X application on the remote computer? do you want to login graphically on the remote computer? do you want to take over a running session? 

if you want to run an X application remotely, log in with ssh with X11 forwarding enabled
```
ssh -X user@host
xeyes
```

You can also make X11 forwarding default by setting "ForwardX11 yes" in /etc/ssh/ssh_config (on the client)

---

### Post by aajax on 2009-02-12
I have several Linux systems running on my network using processors that lack the horsepower to run an Ubuntu Desktop.  They've been built from Debian mostly Sarge (3.1).  I have an X-server installed on some of them but would prefer to rely primarily   on the one on the Ubuntu Desktop computer I am now building.  You could think of them as servers.  Some are production and some are test.  One is an Internet gateway (router if you prefer) that provides print, name, DHCP and firewall services.  I'd like to be able to run X client applications in windows on the Ubuntu Desktop.  For the most part these applications know nothing about GNOME or KDE.  I've experimented, in the past prior to Ubuntu, with different window managers and the software I'm using seems to work pretty well with all of the ones I've tried.

I think I know enough about Linux and Debian that I could hack my way around and might be able to make it work but would prefer to do it the way Ubuntu intends it to be done.  Of course this presumes that Ubuntu does intend such.  I've found no evidence yet which is the reason for this post.  I would think it should since this is one area where Linux and X11 is far superior to MS Windows.

---

### Post by geirha on 2009-02-12
I see, then I think my previous post should be what you want. You don't need to have a running xserver on your other computers, you only need an xserver on your desktop computer. The other computers don't even need to have an xserver installed, only the needed x libraries and of course the applications you want to run from them. Have you given it a try?

---

### Post by aajax on 2009-02-15
Yes, I have tried even though I have enough experience with X11 that I was not optimistic about it working.  What I've done is boot up my Ubuntu Desktop, which uses a different display manager and window manager than I've previously experienced.  Then I ssh to another computer that has working X applications.  This includes some with and some without an X server.  Then I invoke the application and it fails.  I've used a variety of means for designating the display address and have pretty good confidence that this is not the problem.  I suspect the problem has to do with with the basic notions of X authority (i.e., XHOSTS, magic cookies, etc.).  Like I said, I'm pretty sure that I can hack my way around and make something work.  However, I expected that a system as dependent on X11 as Ubuntu Desktop would have thoughtfully prescribed suggestions about how to go about exploiting this capability, which more than anything else, makes Linux genuinely distinct from MS Windows.  To my surprise, I'm beginning to come to the conclusion that for all the effort put into Ubuntu this aspect has been ignored.

---

### Post by Who on 2009-02-15
We have a set up here where the powerful computer is running as an XDMCP server (that can be configured in the GDM configurator, which shows up as the 'Login Window' options in System-->Administration

Then (assuming firewalls don't block things), you can choose 'remote host via xdmcp' in the GDM ' Actions' Menu and that should scan for the hosts available.

Log in (as if you were sitting at the computer that is the server) and most things should work. Playing DVDs didn't on our computer with 4mb gfx memory. We weren't very surprised :P

Sound doesn't get forwarded - so all sounds come out of the main computer :(
Good luck

---

### Post by geirha on 2009-02-16
EDIT: Err, I need to read the whole threads before I post. When you log in to a remote host with x forwarding enabled, what does the DISPLAY variable say?
```
echo $DISPLAY
```

Also note that you need to use capital x in -X, not -x which turns X11 forwarding off.

---

### Post by aajax on 2009-02-20
> **Who said:**
> We have a set up here where the powerful computer is running as an XDMCP server (that can be configured in the GDM configurator, which shows up as the 'Login Window' options in System-->Administration

Then (assuming firewalls don't block things), you can choose 'remote host via xdmcp' in the GDM ' Actions' Menu and that should scan for the hosts available.

Log in (as if you were sitting at the computer that is the server) and most things should work. Playing DVDs didn't on our computer with 4mb gfx memory. We weren't very surprised :P

Sound doesn't get forwarded - so all sounds come out of the main computer :(
Good luck

I'm only trying to run 1 X server.  I think xdm/gdm/kdm involve the situation where you have some number of X servers and want to have centrally controlled logon (and possibly window management).  My remote computers have X capable client applications such as editors and file managers installed.  I want to start them on the remote computer and have them use the   DISPLAY on the local computer that is running the X server.  I am not trying to run multiple X servers.

> **geirha said:**
> EDIT: Err, I need to read the whole threads before I post. When you log in to a remote host with x forwarding enabled, what does the DISPLAY variable say?
```
echo $DISPLAY
```

Also note that you need to use capital x in -X, not -x which turns X11 forwarding off.

I haven't yet tried to use X11 forwarding.  That seems like a bit of overkill for my local LAN.

From past experience I recalled that Debian defaults to starting the X server in a mode that does NOT listen for connections from remote machines.  Therefore, I changed /etc/X11/xinit/xserverrc to remove the "-nolisten tcp" option on machine running Ubuntu Desktop.  I also executed "sudo xhost +".

When I scan the machine running Ubuntu Desktop (i.e., the X server) I find that there is no server listening (i.e., port open) for X connections.  I think the X server has to open the port before I can make any connections but how is this controlled on Ubuntu Desktop?

Here is what i found -

- changing /etc/X11/xinit/xserverrc to remove the "-nolisten tcp" option has no effect.  Implication is that this script is not used when starting X (Xorg) on Ubuntu.
- with gdm (Ubuntu) there is a GUI called gdmsetup which shows a security tab which contains a checkbox that is used to specify whether or not the X server listens for TCP connections.  Changing the setting is effective.
- with gdm (Ubuntu) there is also a file, /etc/X11/gdm/gdm.conf, where an option called DisallowTCP may be used (also seems to be the default) for preventing the X server from listening for TCP connections.
- with kdm (Kubuntu) there is a configuration file, /etc/kde3/kdm/kdmrc, which contains a statement with an option called "ServerArgsLocal=-nolisten tcp".  Commenting this statement was ineffective but explicitly setting the option to null (ServerArgsLocal=) does cause the X server to listen for TCP connections.

---

