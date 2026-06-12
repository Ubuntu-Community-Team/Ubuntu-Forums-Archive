---
title: "Synergy disconnects after upgrading to 8.10"
date: 2009-01-15
forum: General Help
---

### Post by strayhud on 2009-01-15
Hello,

I've looked everywhere for a post/solution to this problem, but can't find one if it exists.   Please point me to it if it does...

I just upgraded from 7.04 to 8.10 and all is well except for Synergy.   I use it to share a mouse and keyboard on a mac, and it was working fine under 7.04.  The server is on the mac and ubuntu is running the client.  Now it constantly connects and disconnects with the following messages:

From the client side (ubuntu):
NOTE: synergyc.cpp,247: connected to server
NOTE: CServerProxy.cpp,316: server is dead
WARNING: synergyc.cpp,265: failed to connect to server: server is not responding
DEBUG: synergyc.cpp,237: retry in 1 seconds

From the server side (OSX):
NOTE: accepted client connection
NOTE: client "cobra" has connected
NOTE: client "cobra" has disconnected

As you can see it makes the connection ok, but disconnects a few seconds later.

I'm running ubuntu 8.10 on a AMD64 platform with kernel 2.6.27-9-generic.   The mac is running Leopard (OSX 10.5).  Synergy is 1.3.1 on both platforms (package install for intrepid).  Not running a firewall.   Connection is stable.   Can ssh into the box and do everything else otherwise.    

Any ideas?   I thought I read about a possible race condition with Synergy introduced with the latest kernel upgrade, but can't seem to find the post now.

Any help greatly appreciated.

Thanks,
Steve

---

### Post by MC_LA on 2009-03-29
Hi, I'm having a similar problem. Synergy seems to work fine, but periodically (about every 30 minutes) it loses connection. About 10-20seconds later it comes back and works fine again. Did you find a solution to your problem ? Thanks

---

### Post by strayhud on 2009-03-29
Unfortunately I had to switch things around and make ubuntu the server and osx the client.   Not ideal, but I don't have any connection issues this way.    Wish I had better news...

---

### Post by MC_LA on 2009-04-11
here's more info on my problem, not sure if it's the same. Any help would be greatly appreciated. Thanks.

I've been using synergy for a while and never had any problems. I recently started having periodic lost connects only on my Ubuntu machine after upgrading to 7.10 and then again on Intrepid 8.10.

I have 3 machines at home: OSX, Ubuntu, and Windows. OSX is my server. Both the Ubuntu and Windows machines connect fine, but periodically the Ubuntu machine will lose connection for about 30 seconds and then will automatically reconnect without any issues. The Windows machine never loses connection. This problem happens even if the Windows machine is turned off (which it usually is).

On the OSX (the synergy server), I see this message when the connection is lost: WARNING: error writing to client "X" , where X is the name of my Ubuntu machine.

This is very annoying, so any suggestions would be greatly appreciated.

---

### Post by MC_LA on 2009-04-18
So I figured out my problem. For some reason, a wireless router that is connected to a switch is causing problems with my synergy. The router isn't causing any other network problems, so it's strange that only synergy periodically losses connection.

---

### Post by julianchick on 2010-03-03
Found the same problem on 9.10 Karmic, but was able to stop the repeated disconnects by disabling the GNOME Remote Desktop Server  that auto starts on boot up. (vino-server)

---

