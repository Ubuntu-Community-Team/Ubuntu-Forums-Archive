---
title: "Firestarter ... does not .... (ver. 7.04)"
date: 2007-04-23
forum: Desktop Environments
---

### Post by expatCM on 2007-04-23
From the number of people who post this is a very old chestnut.  The solution is not so obvious (to me).

I installed Firestarter and it would manually load.

I went to this link 
[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)
and followed the instructions for editing the sudoers file and adding the entry to the sessions options and according to the article Firestarter should then load on boot and the icon should appear in the system tray.

“Firestarter will in that case load directly into the system tray without user intervention, after which the main interface can be accessed by clicking the tray icon.”

Trouble is that it does not.

So then I researched a bit and people were suggesting to check the box to have Firestarter load on dial-up even though dial-up is not installed.  Did that.

What now happens is that Firestarter does not auto start and if I try to load from the System / Administration menu it does not even start.

From a command prompt when entering the Firestarter command the following is returned ...

Xlib: connection to ":0.0" refused by server

Xlib: No protocol specified




(firestarter:6754): Gtk-WARNING **: cannot open display:  

but google does not offer many results ....

Could anyone offer any suggestions of what I can do to get this firewall to load on start?

---

### Post by orb9220 on 2007-04-23
> Could anyone offer any suggestions of what I can do to get this firewall to load on start?

Firestarter is NOT a firewall. It is the gui frontednd to iptables which is the firewall and is installed and runs automatically.

Firestarter is for customizing settings like allow and blocking specific sites,IP's.etc

Sorry but I thought the same when I first started out and found out I did not need it to have a firewall running.

---

### Post by expatCM on 2007-04-23
Yes, I actually know that ....  but the reason for using Firestarter is the speed and ease you can change the settings...  to edit through a graphical front end is MUCH more friendly than hacking your way though the command line and not knowing whether you have just edited your way into a perfect disaster.

---

### Post by mcduck on 2007-04-24
> **expatCM said:**
> Yes, I actually know that ....  but the reason for using Firestarter is the speed and ease you can change the settings...  to edit through a graphical front end is MUCH more friendly than hacking your way though the command line and not knowing whether you have just edited your way into a perfect disaster.

You still don't need to run the firestarter GUI tool all the time, the firewall will work anyway. The GUI tool is just for settings, the firewall itself is started on boot, no matter if you ever run the GUI tool or not.

edit: to make it more clear, your firewall is divided in 3 parts. Iptables is the actual working firewall, then there is firestarter script that starts and configures iptables on boot and works as 'brains' for your firewall. And then there's the firestarter GUI tool that is used to change settings of the firestarter script.

So to get what you want just open the GUI when you need to change some setting, and leave it closed other times. It's easier, and also safer as that way you don't have root apps running on your desktop all the time. :)

---

### Post by expatCM on 2007-04-24
I do appreciate the reply but I already understand what you are saying .....

So let me try this on another track ............

Firestarter does not work. I want it to work.

How do I do that?


(the program will not launch from either the menu or the command line.  Details in the original post)

---

### Post by mcduck on 2007-04-24
> **expatCM said:**
> I do appreciate the reply but I already understand what you are saying .....

So let me try this on another track ............

Firestarter does not work. I want it to work.

How do I do that?


(the program will not launch from either the menu or the command line.  Details in the original post)
Were you able to start Firestarter GUI before you started tweaking sudoers etc.? Then the first thing I'd recommend is trying to undo the steps you have done to allow running the Firestarter GUI without sudo/root.

---

### Post by expatCM on 2007-04-24
What I have now done is to remove the entry in the sudoers file and removed the sessions start option.  I also uninstalled Firestarter and then installed it again.

The situation now is that Firestarter will start from the menu option.  I have not yet attempted the sudoers setting again ...  not sure what I should change though since what I did at the outset was "out of the book".

I would like Firestarter to open with the system since I am at present setting up four machines on a network and for me it is very useful to be able to see at a glance where problems are appearing (since the system tray icon will show red when there is blocked traffic).  I would also like my children to see the icon so that they start thinking about what is happening when it shows red and whether they need to think about a firewall when they install games.

Whilst I am using gnome, perhaps Guarddog would be an easier choice?

Incidentally, I know that Firestarter is a front end for IPtables.  However, Firestarter does describe itself as a firewall.   Presumably there is no firewall active on a new system until a program such as Firestarter has been run to make the initial settings .... I cannot see that IPtables will protect a system until there is some basic configuration to do so..

---

### Post by mlind on 2007-04-24
As a default, root user doesn't have access to your xserver DISPLAY. You can extract a MAGIC-COOKIE and import is as a root or use xhost +local:root to allow this.

```

#as normal user
xauth extract /tmp/display $DISPLAY

#as root
xauth merge /tmp/display

#as normal user who has NOPASSWD in /etc/sudoers for /usr/sbin/firestarter
sudo firestarter

```

You can also try, not sure if this works (needs NOPASSWD entry too)
```

#as normal user
xhost +local:root
DISPLAY=:0.0 sudo firestarter

```

I recall using env_keep+="DISPLAY" in /etc/sudoers used to work at some point, but it doesn't seem to do the job anymore.

---

### Post by orb9220 on 2007-04-24
> Presumably there is no firewall active on a new system until a program such as Firestarter has been run to make the initial settings .... I cannot see that IPtables will protect a system until there is some basic configuration to do so..


I am sorry I just went to shields Up web site and ran the test on my default no firestarter, no adjusting iptables on my side. This was the results.

GRC Port Authority Report created on UTC: 2007-04-24 at 16:58:33

Results from scan of ports: 0-1055

    2 Ports Open
    1 Ports Closed
 1053 Ports Stealth
---------------------
 1056 Ports Tested

Ports found to be OPEN were: 22, 80

The port found to be CLOSED was: 161

Other than what is listed above, all ports are STEALTH.

TruStealth: FAILED - NOT all tested ports were STEALTH,
                   - NO unsolicited packets were received,
                   - A PING REPLY (ICMP Echo) WAS RECEIVED.

22=ssh remote Logon
80= World Wide Web Http protocal
161=snmp

**File Sharing**

Your Internet port 139 does not appear to exist! 

One or more ports on this system are operating in FULL STEALTH MODE! Standard Internet behavior requires port connection attempts to be answered with a success or refusal response. Therefore, only an attempt to connect to a nonexistent computer results in no response of either kind. But YOUR computer has DELIBERATELY CHOSEN NOT TO RESPOND (that's very cool!) which represents advanced computer and port stealthing capabilities. A machine configured in this fashion is well hardened to Internet NetBIOS attack and intrusion.

Unable to connect with NetBIOS to your computer.

All attempts to get any information from your computer have FAILED. (This is very uncommon for a Windows networking-based PC.) Relative to vulnerabilities from Windows networking, this computer appears to be VERY SECURE since it is NOT exposing ANY of its internal NetBIOS networking protocol over the Internet.

I need 80 open because I am on a wifi hotspot and they have it open and it is for web browsing,

So to say that iptables is not working is incorrect.

---

### Post by expatCM on 2007-04-25
mlind...  thanks for your reply ... I am just about to try this but a thunderstorm has just blown in ...  I will post again a bit later ...

---

### Post by KrazyPenguin on 2007-04-25
Try this link:

[http://ubuntuforums.org/showthread.php?t=187899&highlight=krazypenguin+firestarter](http://ubuntuforums.org/showthread.php?t=187899&highlight=krazypenguin+firestarter)

---

