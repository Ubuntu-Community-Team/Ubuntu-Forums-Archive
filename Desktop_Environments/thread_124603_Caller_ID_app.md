---
title: "Caller ID app?"
date: 2006-02-01
forum: Desktop Environments
---

### Post by Didjit on 2006-02-01
Looking for a simple GUI caller ID App like YAC ([http://sunflowerhead.com/software/yac/)](http://sunflowerhead.com/software/yac/)). Anything exist for Linux?

I dug around, but what I found was not very current...

Tx

Dijdit

---

### Post by newOldUser on 2006-03-14
If you're running KDE I think there is a tray app called Kaller

A different piece of software called NCID/NCIDD is what I use with Ubuntu.  More info at [http://ncid.sourceforge.net/](http://ncid.sourceforge.net/) 

Basically you run a "Caller ID Server", thats the NCIDD program and then all you machines on the network can run "Caller ID Clients", the NCID program to display caller info.  This works well if you have multiple machines (or TIVOs) but only one has a caller ID modem.  Run NCIDD on the one with the good modem and NCID clients on the others.

---

### Post by milliman on 2008-02-02
I'm running NCID and it works great, but I was wondering if anyone had developed any client applications that create a pop-up in the panel or on the entire screen?  I nice little client would sit in the background in the panel and create a full-screen or balloon pop-up when someone calls.  Does anyone know if such and application exists?

---

### Post by yogibayer on 2008-03-08
Let me start by saying I am new to Ubuntu/Linux.  So this may be a stupid question.

I have installed NCID and don't see it running in System Monitor after reboot.  I don't see it in my Applications list.  I see all of the files that were supposed to be installed in etc, etc/init.d, usr/sbin, usr/share, but cannot figure out how to launch the gui or why it doesn't show up in my list of running programs, since it's in the init.d directory.

Any help or insight would be appreciated.

---

### Post by milliman on 2008-03-08
NCID is a client/server application which means that there is the ncidd program that retrieves the caller ID information from the modem and provides an API to any client application on the same machine or network.  ncid is the client application that runs on your Linux box.  It will display the caller ID information when someone calls.  It is a very basic example of what can be done with NCID.  I have a Windows version of the client that creates a pop-up in the systray when someone calls.  I have this client installed on all computers in the house so we can see who is calling without getting up to look at the phone.  How's that for lazy?  I believe that all of the programs are available on the Sourceforge project site for NCID.

The NCID daemon runs as root so you won't see it in your System Monitor.  The daemon should be running when you boot the machine.  You can check with the command:
```

ps -aef |grep ncid

```
This command will show you all NCID related processes.  You should see the ncidd program running with a parent ID of root and this the command.  If you had the client running, it would appear too.

I hope that this helps you a bit.

---

### Post by yogibayer on 2008-03-08
> **milliman said:**
> 

...
```

ps -aef |grep ncid

```
This command will show you all NCID related processes.  You should see the ncidd program running with a parent ID of root and this the command.  If you had the client running, it would appear too.

I hope that this helps you a bit.

Thanks for your help.  I see the processes running now...that makes me happy.  I forgot to mention that I have YAC running on all of my other boxes, which are running windows.  One of those computers is the YAC server and I'm not receiving the caller ID info on this computer.  I do not see yac2ncid running when I run grep, but yac2ncid shell script is in my init.d directory.  I will remove ncidd from there, because i'm not looking to use this machine as a server.  I'll keep playing and any more hints would be appreciated.

---

### Post by milliman on 2008-03-08
yogibayer:

I use ncidpop and not yac so there isn't much I can help you.  Yac2ncid probably has some configuration options to specify the ncidd server name or address.  Make sure that these devices can recognize each other.

---

### Post by jlc46 on 2008-04-02
> **yogibayer said:**
> I forgot to mention that I have YAC running on all of my other boxes, which are running windows.  One of those computers is the YAC server and I'm not receiving the caller ID info on this computer.  I do not see yac2ncid running when I run grep, but yac2ncid shell script is in my init.d directory.  I will remove ncidd from there, because i'm not looking to use this machine as a server.  I'll keep playing and any more hints would be appreciated.
Yac2ncid is a gateway that receives the Caller ID from a YAC server, converts it to NCID format and sends it to ncidd for distribution.  You need to configure the YAC server, give it the IP address of the computer running yac2ncid.  It acts like a YAC Listener.

You also need to make sure you uncomment this line in ncidd.conf: ```
set noserial = 1
```

You can manually start ncidd and yac2ncid.  You can also check the status:
```

sudo invoke-rc.d ncidd start
sudo invoke-rc.d sip2ncid start
sudo invoke-rc.d ncidd status
sudo invoke-rc.d sip2ncid status

```
You can also set them to autostart at boot:
```

sudo update-rc.d ncidd defaults
sudo update-rc.d yac2ncid defaults

```
> **milliman said:**
> I'm running NCID and it works great, but I was wondering if anyone had developed any client applications that create a pop-up in the panel or on the entire screen? I nice little client would sit in the background in the panel and create a full-screen or balloon pop-up when someone calls. Does anyone know if such and application exists?

NCD version 0.70 has a new output module called ncid-popup.  The init script is called ncid-popup.  You would start it, as above, using invoke-rc.d, with the name ncid-popup.  All output module names are now in init.d so you can start any or all of them the same way.

All output modules are simple shell scripts.   You can read them to see how they do their magic, and you can make your own using /usr/share/ncid/ncid-skel as a example.  If you want the popup to cover the whole screen, you can configure it to do so in ncidmodules.conf.  It uses  kdialog to create the popup.

There is now a [INSTALL-Ubuntu]("http://ncid.sourceforge.net/ncid/INSTALL-Ubuntu.txt") page that gives instructions on how to get started.

---

