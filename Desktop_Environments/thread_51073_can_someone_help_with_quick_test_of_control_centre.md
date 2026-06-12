---
title: "can someone help with quick test of control centre?"
date: 2005-07-22
forum: Desktop Environments
---

### Post by arjay1 on 2005-07-22
[I]EDIT:  OK FOLKS HERE'S THE SCOOP:

The problem I am having is due to a bug.  If you want to see if you have the same problem, run the test sequence in my original post below.

Details:  There is a major, major, bug in KDE 3.4.0 AND 3.4.1.   I have found it is well documented at bug number 8681 at bugzilla.ubuntu.com and 61850 at bugs.kde.org. There are pages and pages of complaints - a quick google will get you there.

There are a few suggested workarounds but most only work for a few people.  The KDE developers suggest you switch to Gnome for the time being!!!!!!!!!!

I am going to try a couple of things (only a newbie I'm afraid) and I'll let people know if anything works.
[/I]


Original post:
I am having problems getting a router's ip address to stick in Kubuntu's network interface settings.  If I try to make changes manually in the network settings in KDE's Control Centre I get a strange situation - and need confirmation it is not just me.

I need someone to just tell me if the same thing happens when they follow this sequence:

1. Click on KDE main menu

2. Click on Control Centre

3. Click on Internet and Network

4. Click on Network Settinggs.  It should say "Please wait while detecting your network".  Then a greyed-out screen comes up with the interface details in the background.

5.  Click on Administrator Mode.  It should ask for your password.  Enter password.

6.  I then GET THROWN BACK TO PREVIOUS SCREEN instead of being allowed to edit network settings.

7.  If this happens to you - also try other services - e.g. Samba - the same thing happens to me - I get dumped back at the previuos screen.  I know the password is OK because it works for other things - e.g. sudo.

BTW - this happens on two different computers, both running Kubuntu and KDE 3.40 and 3.41

Could whoever tries this for me just report the results of this test.

Many thanks.

---

### Post by damonw5 on 2005-07-22
[QUOTE=arjay1]*The KDE developers suggest you switch to Gnome for the time being!!!!!!!!!!*[/QUOTE]

Somehow I doubt this...

---

### Post by JLTB on 2005-07-22
There are a few Kubuntu specific bugs with regards to the control center and networking.  My favourite (i've hit it several times) is that the control center, in 3.4.0 anyway, doesn't keep gateway settings and you have to reset them each time.

Best way around this craziness is to do it the old fasioned way and edit the /etc/network/interfaces file.  Anyway, mine basically looks like this

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet static
        address 192.168.1.101
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.1

```

voila, you can forget about the network part of the control center as long as you don't try to reinstall the system.

---

### Post by arjay1 on 2005-07-23
damonw5

Yes - sorry, it was an exaggeration/misunderstanding received from someone else I have been emailing re this problem.

What was actually said was on the bugzilla bug site where it was _suggested_ by several posters that it was simpler and more stable to switch to gnome for the time being.  Not sure if any of them were developers as I was told but it is a common theme there.

Sorry if I misled anyone.

---

### Post by skyboy on 2005-07-26
Anyway, I think it is much better and reliable to configure files by hand (not the easiest of course). That's the advantage of Linux in general so it's good not to loose the good reflex :)
editing /etc/network/interfaces by hand isn't that complicated and at least you are sure that no bugs is misleading you into some weird hougabouga network settings :)

---

### Post by arjay1 on 2005-07-26
skyboy

Sure you are right but it's not that easy for newbies who are probably used to auto config features of Windows.  Also, at least with the semi-auto GUI in kubuntu you can be reasonably sure that things will work even if they are not the most elegant or efficient settings.

For example, I faithfully made the changes to my interface file as per JTLB's post above - changing only the actual settings for my machine.  I got these from ifconfig and route - so they should have been right.  Anyway - with these settings, kubuntu absolutely refused to install my network.  It came up failed on boot every time.  For some reason it doesn't like the static setting.  When I changed it back to dhcp it was fine.  (dchp still gives the same ip addrerss every time anyway!)  

Now, I am beginning to understand how to config linux after a few months of learning but there is a point beyond which I cannot fathom out the why's and wherefore's.  Hopefully things will improve as long as I stick at it but you have to invest ENORMOUS of time and effort to get anywhere with linux.  Luckily I am retired now and can play about to my hearts content ......... not everyone has that luxury!

---

### Post by Takis on 2005-07-26
This is a bug that's been mentioned quite a few times.
[http://ubuntuforums.org/showthread.php?t=30893](http://ubuntuforums.org/showthread.php?t=30893)

---

### Post by arjay1 on 2005-07-27
Thanks for the tip - I can't be very good at searching in the forums as I turned up a load of stuff but not this.

I will hold the change in reserve in case I need it.  At the moment my system is stable and it took so long to get it there I dare not make any changes that might upset kcontrol (it kept deleting my interface gateway settings - losing me my netwqork and the internet).  Not going through that again.

Thanks anyway - much appreciated

Richard

---

