---
title: "wireless gui"
date: 2006-01-11
forum: General Help
---

### Post by blu.gecko on 2006-01-11
I am looking for a GUI wifi tool that I will be able to connect to any wireless type b/g plus I need to be able to connect to any encryption type. I have a laptop and I need to be able to use it when I go from client to client.

I have ndiswrapper loaded and working fine, but I need to be able to change connections, types of connections on the drop of a dime.

the company I work for has many of clients, if I cannot find a answer I will have to load windows. blah:confused:

---

### Post by Zelut on 2006-01-11
I found something that may work for you.. (at least I hope so.  I'd hate to lose you back to windows!)

sudo apt-get install wifi-radar

It'll show a list of available SSID, signal strength, mode (managed, unmanaged), and broadcast type (b/g).  I don't use WEP thru my AP so I'm not sure if that is configurable but take a look..

---

### Post by Zelut on 2006-01-11
Edit: Accidental Duplicate Post

---

### Post by scpike on 2006-01-12
personally i have found the Network-Manager applet to be the best.  it will automatically configure a wired network when plugged in, as well as show available wireless networks when you are roaming.

to install it from synaptic:
> sudo apt-get install network-manager

im assuming you are using gnome, so you will want to set it up to run every time you start gnome by going to:
System -> Preferences -> Sessions -> Startup Programs  tab
and clicking add, then type **nm-applet** as the command and click ok

now log out and back in and it should be running

---

### Post by Zelut on 2006-01-12
Well I'm glad I subscribed to this thread.  Network-Manager is great!  Thanks for the tip.  Here I was thinkin' I knew a good solution and you had an even better.

---

### Post by Dr. Nick on 2006-01-12
wifi-radar looks great but i had bad luck, also had bad luck with network-manager but its been awhile so I may try nm-applet again. Thanks for remining me :)

---

### Post by closeyourwindows on 2006-01-12
there is however one that works for me.  gtkwifi.  the newest version is 1.09, however I have not had much success with that one, I am using 1.06
[http://prdownloads.sourceforge.net/g...6.deb?download](http://prdownloads.sourceforge.net/g...6.deb?download)
dpkg -i gtkwifi-1.06.deb
a good thread I found on this was [http://ubuntuforums.org/showthread.php?t=34645](http://ubuntuforums.org/showthread.php?t=34645)

if you are brave enough to try the latest version it can be found here
[http://sourceforge.net/projects/gtkwifi/](http://sourceforge.net/projects/gtkwifi/)

---

### Post by kingsidy on 2006-01-12
fire up the terminal and  type in
> gtkwifi run-in-window
you can also create an icon for it so u can launch it with a click

---

### Post by thava on 2006-01-12
Hi

I ust reinstall my ubuntu 5.10, and I try to install network-manger, then i got this error:

> $ sudo apt-get install network-manager
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  network-manager: Depends: bind9 but it is not going to be installed
E: Broken packages


then i try to install from [http://bootlab.org/~j/NetworkManager-breezy/](http://bootlab.org/~j/NetworkManager-breezy/) it will also not install the network-manager for me.

> 
Setting up network-manager (0.5.1-0ubuntu1) ...
 * Stopping Network connection manager daemon:                                                                                                        [ ok ]
 * Starting Network connection manager daemon: chown: `bind:bind': invalid user
dpkg: error processing network-manager (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 network-manager
E: Sub-process /usr/bin/dpkg returned an error code (1)

Anyone know whats wrong here? and pls reply, thank you

---

### Post by nocturn on 2006-01-12
I looked at most of the wireless GUI's but found problems with many of them.

I documented things here: [http://ubuntuforums.org/showthread.php?t=114750](http://ubuntuforums.org/showthread.php?t=114750)

You can look over it to see which one offers the functionality you want.

---

### Post by thava on 2006-01-12
thanks nocturn

nou I intalled gtkwifi its work fine.

/ Thava

---

### Post by socrazy143 on 2006-01-12
I gave network-manager a try out of curiosity and it seemed to slow things down.  :confused:

---

### Post by Dr. Nick on 2006-01-12
[quote=socrazy143]I gave network-manager a try out of curiosity and it seemed to slow things down. :confused:[/quote]
 
lucky you, I tried it and it killed my wireless connection :) I am on dapper which may be part of the reason though. The thing with network manager is that it is always running as a background process constantly looking for new networks it can connect to, This may have been what led to your slowdown, I didnt think the slowdown would be real noticeable but maybe it is then.

---

### Post by scpike on 2006-01-12
[QUOTE=Dr. Nick]lucky you, I tried it and it killed my wireless connection :) I am on dapper which may be part of the reason though. The thing with network manager is that it is always running as a background process constantly looking for new networks it can connect to, This may have been what led to your slowdown, I didnt think the slowdown would be real noticeable but maybe it is then.[/QUOTE]

you can make the network manager stop searching for networks by right clicking the system tray icon and clicking never search or search only when disconnected under "Wireless Network Discovery" 
its stable under breezy idk it might get all screwy with dapper

---

### Post by Dr. Nick on 2006-01-12
[quote=scpike]you can make the network manager stop searching for networks by right clicking the system tray icon and clicking never search or search only when disconnected under "Wireless Network Discovery" 
its stable under breezy idk it might get all screwy with dapper[/quote]

Now that you mention that I remember seeing that option awhile ago, I blame my problems on Dapper since the applet gave errors on loading, So anyone out their with breezy dont let my comments scare you from trying it :)

---

### Post by blu.gecko on 2006-01-12
well the one thing I asked for neither of these applications were able to do.
what I need is an application to be able to go from wep to wpa-psk2........
wep is fine, but if I go to a clients business and I cant connect, they are going to ask why and so will my boss, I simply cant have that happen...........

---

### Post by Fr33d0m on 2006-01-24
[QUOTE=scpike]you can make the network manager stop searching for networks by right clicking the system tray icon and clicking never search or search only when disconnected under "Wireless Network Discovery" 
its stable under breezy idk it might get all screwy with dapper[/QUOTE]


Hmmm, I'm on breezy and it had no right-click functionality.  I wonder what universe I got stuck in.

---

### Post by danish_demon on 2006-01-24
thanks for the network manager tip, i loaded it and i think it will help me out.

---

### Post by Fr33d0m on 2006-01-25
[QUOTE=Fr33d0m]Hmmm, I'm on breezy and it had no right-click functionality.  I wonder what universe I got stuck in.[/QUOTE]

I reloaded it and still no right-click functionality.  Am I missing something?

---

