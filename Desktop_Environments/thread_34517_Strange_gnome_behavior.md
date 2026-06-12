---
title: "Strange gnome behavior"
date: 2005-05-15
forum: Desktop Environments
---

### Post by exile on 2005-05-15
Hi all something that I can't work out is happening.

Some background - been running Ubuntu 5.04 since it came out. Everything is great and smooth. Currently using KDE as my desktop.

Yesterday my machine hung (don't know why yet - mouse moved but everything else was frozen solid even the capslock key etc.). I rebooted and noticed in my boot up that it failed to start my network (eth0 cat5 DHCP rather simple setup). Once I got into the system I activated eth0, network goes on everything is fine. I then launch evolution - nothing happens. I try launching from the prompt all I get was "es menu class init". Anyway I try to launch it a number of different ways, no luck. I pop in a CD to fire up grip - it comes up with a blank window, no buttons, text, menus etc.

I start to think that something strange is going on. I start up a few KDE apps (kopete and k3b) and they launch pretty much immediately.

Suddenly, 5 copies of evolution come up - like a 10 minute delayed start. Once evo is loaded it works fine. I fire up OO Writer and Firefox. Firefox responds immediately and Writer sits at 100% on the splash screen.

By now Grip has come to and is working fine.

Eventually writer starts.

I log out and start a gnome session (something I only did a few days ago) - it sits with just the GDM background - no starting splash screen or anything else happens.

I jump to another terminal and check top and ps aux everything seems fine, no rogue processes, memory usage normal etc.

I kill X and start it back up and log back into kde. Once again all the apps I just mention take 5 or 6 minutes to start up. GIMP and Firefox work fine however.

Am I goping mad? I don't really want to reinstall everything. I uninstalled grip and evolution and reinstalled them - no changes.

Has anyone else seen this before? What can I do? It seems to me that the GTK or gnome libraries are some how waiting on something to time out before they start.

Nothing in dmesg or the logs. No unsual error messages - as far as the system is concerned everything is working fine but just loading gnome apps very slowly.

Suggestions?
 ](*,) 

Thanks.

---

### Post by Alexander Kirillov on 2005-05-16
[QUOTE=exile]Hi all something that I can't work out is happening.

Some background - been running Ubuntu 5.04 since it came out. Everything is great and smooth. Currently using KDE as my desktop.

Yesterday my machine hung (don't know why yet - mouse moved but everything else was frozen solid even the capslock key etc.). I rebooted and noticed in my boot up that it failed to start my network (eth0 cat5 DHCP rather simple setup). Once I got into the system I activated eth0, network goes on everything is fine. I then launch evolution - nothing happens. I try launching from the prompt all I get was "es menu class init". Anyway I try to launch it a number of different ways, no luck. I pop in a CD to fire up grip - it comes up with a blank window, no buttons, text, menus etc.

I start to think that something strange is going on. I start up a few KDE apps (kopete and k3b) and they launch pretty much immediately.

Suddenly, 5 copies of evolution come up - like a 10 minute delayed start. Once evo is loaded it works fine. I fire up OO Writer and Firefox. Firefox responds immediately and Writer sits at 100% on the splash screen.

By now Grip has come to and is working fine.

Eventually writer starts.

I log out and start a gnome session (something I only did a few days ago) - it sits with just the GDM background - no starting splash screen or anything else happens.

I jump to another terminal and check top and ps aux everything seems fine, no rogue processes, memory usage normal etc.

I kill X and start it back up and log back into kde. Once again all the apps I just mention take 5 or 6 minutes to start up. GIMP and Firefox work fine however.

Am I goping mad? I don't really want to reinstall everything. I uninstalled grip and evolution and reinstalled them - no changes.

Has anyone else seen this before? What can I do? It seems to me that the GTK or gnome libraries are some how waiting on something to time out before they start.

Nothing in dmesg or the logs. No unsual error messages - as far as the system is concerned everything is working fine but just loading gnome apps very slowly.

Suggestions?
 ](*,) 

Thanks.[/QUOTE]
 It is likely to be  a networking problem - maybe something wrong with /etc/hosts or /etc/resolv.conf. This causes gnome to wait forconnection until it times out. Since Evo and grip are gnome program, it affects them; GIMP and Firefox are not. 

Check these files, and search the forums -- it had been discussed many times.

---

### Post by neighborlee on 2005-05-16
[QUOTE=Alexander Kirillov]It is likely to be  a networking problem - maybe something wrong with /etc/hosts or /etc/resolv.conf. This causes gnome to wait forconnection until it times out. Since Evo and grip are gnome program, it affects them; GIMP and Firefox are not. 

Check these files, and search the forums -- it had been discussed many times.[/QUOTE]
----------
is this only a GNOME problem ( clearly by his kde apps starting I would guess it is ) meaning that if running kde and network goes down that the computer wont freeze like gnome is doing ?

I have no idea since I dont use kde..

cheers
neighborlee

---

### Post by exile on 2005-05-17
Thanks for the replies.

/etc/hosts and /etc/resolv.conf are fine and very vanilla.

The problem is only occuring with gnome apps. All the kde apps are fine.

On boot the network fails saying it could not determine a network interface however when I run network-admin and activate eth0 the network is fine.

One more interesting behaviour - when the system starts up and the network has failed evolution and gnome apps load straight away. Once the network goes up any gnome app takes 5 to 6 minutes to start. 

The route is normal, both primary and secondary DNS entries are there and working. Epiphany won't start but konqueror and firefox will. Why does the network, which should be common to both affect gnome so differently?

---

### Post by exile on 2005-05-20
the problem seems to be fixed by:

sudo ifconfig lo 127.0.0.1

why the localhost isn't coming up for I don't know yet.

---

### Post by exile on 2005-12-31
[QUOTE=exile]the problem seems to be fixed by:

sudo ifconfig lo 127.0.0.1

why the localhost isn't coming up for I don't know yet.[/QUOTE]

Has anyone been able to work out why loopback doesn't come up by default.

I've checked /etc/network/interfaces and the file is identical to my other machine (which works fine).

To recap on the behaviour - Any breezy machine that I've installed from scratch (2 desktops and a laptop) have this same problem. Boot up and the network fails to reach the DHCP server. If I run dhclient it goes until it times out. I then unplug the cat 5 cable and plug it back into exactly the same port, then run dhclient again and it finds an IP straight away.. but then all the gnome apps take 5 minutes to start up (as they wait for the loop back connection to time out) then I have to run 
sudo ifconfig lo 127.0.0.1 and the box is back to normal.

The one breezy box that does work fine without any fiddling around is an upgrade. On the other computers with the network problem work fine (network wise) in both WinXP and Mandriva.

This is very frustrating since the problem seems completely localised to Breezy.

Any advice would be appreciated. Thanks

---

