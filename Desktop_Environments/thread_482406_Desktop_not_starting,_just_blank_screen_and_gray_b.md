---
title: "Desktop not starting, just blank screen and gray box"
date: 2007-06-23
forum: Desktop Environments
---

### Post by pepsi_max2k on 2007-06-23
[COLOR="Red"]SOLVED: See final post.[/COLOR]


Got a pretty big problem with 7.04 + gnome: when it starts up, soon as I login in, instead of the regular "loading xyz..." box then the desktop, I just get my wallpaper and eventually a gray box in the top left, and nothing else. Any ideas what might be up?

The last thing I remember doing is running synaptic and updating about 10 lib... packages, last night things were a bit weird (little slowdown, taskbar seemed to freeze for a bit, had problems in the network config panel and when i opened something that would ask for password without closing every other window first it'd give an error about X something and not show it... anyway, after a reboot i got nothing.

Help.. anyone... at all? I've tried gnome-failsafe, same thing, i'll try a apt-get update but other than that I haven't got a clue... **EDIT:** nothing to upgrade :( is there a way to uninstall the last installed packages from command line? also tried restarting in safemode, startx from root was fine...


**EDIT 2:** whipped the network plug out, restarted in normal mode, started up fine.

I think it was something to do with dhcp network, had seen stuff like "could not resolve network address, d3efaulting to 127.0.0.1" or somesuch when turning off, so i don't think it was getting an ip from router, also the fact that when things started getting weird earlier i'd tried to change network settings, and wired properties had ended up in roaming enabled and no dhcp option. also had a problem like this in suse when no ip could get assigned and it hung at boot, but never on the desktop...

still have a strange problem with firefox suddenly deciding to show all the toolbars. and now network settings isn't loading at all... something's up anyway :| ... meh


**EDIT 3:** localhost webserver not loading, mythtv not accessing database.... it's ye olde linux hell ain't it? when will someone build an OS that don't eat itself once in a while :(

**EDIT 4:** hmm... see below.

---

### Post by pepsi_max2k on 2007-06-23
k now i'm hitting a whole load of problems, seems the whole system's messed up.

the load issues seem primarily down to the system not picking up an ip by dhcp and hanging, but there's oh so much more...

i managed to get this text out of the gray box that was loading at start (by removing the network cable when it had hung and having everything load, mostly...)

> There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in.

then got an error about the temp sensor demon not starting for the task panel.

also have problems getting the gksu login box to appear for things, got this when trying to run from a command prompt:

> (network-admin:6641): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

local webserver still doesn't seem to be loaded. 



hannngg on... /dev/hda5... 99% full... 20mb left... thiiink i may have found the problem ;)...hang while i try delete stuff..

---

### Post by {spitFire} on 2007-06-23
IMHO, from the error it seems more like a dbus start-up problem. I would suggest to look into that as well.

---

### Post by pepsi_max2k on 2007-06-23
haven't changed any dbus packages for a while but...

deleting 10 copies of the linux source code :rolleyes: from the recycle bin and freeing up 50% of hd doesn't seem to have solved too much, still with the login problems. and gksu password problems... 

is there anything i could do about that dbus stuff? there's no seperate packages to try downgrading to, and i haven't changed any config files. the whole thing's just gone pear shaped without me doing anything. i knew ubuntu's reign without hastle it was too good to last :(

---

### Post by pepsi_max2k on 2007-06-23
Solved all the problems. Hopefully. And all due to the lack of a loopback address.

Must've happened when I was messin about with the network manager, which messed up my /etc/network/interfaces file, which looked slightly anemic with just a "auto eth0" and "iface eth0 inet dhcp" line in, and "ifconfig -a" from a command line showed no ip for the loopback. anyway, changing the interfaces file to the following seems to have made everything a lot nicer:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
```

got my localhost/mythweb page back too. no password problems so far. i've only booted once though... :|

seems like there might be a bug in network-manager or something, cos theres a few people on the boards posting about the same problem. needless to say i won't be using it too much in the future :p

---

### Post by NorthernSuze on 2007-07-15
I too, had this problem and it appears to be caused by my first *fix* <grin> to get network connections working

1. new Fiesty load - unable to connect to internet to get the updates:
In order to configure my network to work with the static IP address, I had to #comment out the Loopback Network section in the /etc/network/interfaces file.

2. downloaded and installed update packages, rebooted and recieved the dreaded  blank bronze screen and little grey box!  :o

3.  It eventually  finished loading and let me get at the terminal - I had to go back and uncomment the Loopback Network section in the /etc/network/interfaces file, reboot and everybody seems happy.

So It took a lot of staring, reading and trying, but I can state this worked for me! It would be nice if someone with more experience could make an easier to find documentation file explaining the whys and where fores . . . but much thanks to each of you who explained my two separate problems!

Suzanne

---

