---
title: "network connection &quot;suddenly&quot; won't connect at startup anymore"
date: 2006-05-28
forum: Desktop Environments
---

### Post by F for Fragging on 2006-05-28
I'm affected by a very annoying problem, I'd appreciate some help, but I hope some one could at least tell me under which package I should file a bug in Malone, because I have no idea what handles the network stuff, is it the kernel? Let's start with the beginning:

I was affected by [bug #37750]("https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/37750") so I edited /etc/default/rcS and changed "UTC=yes" to "UTC=no". During the session I edited that file, I'm sure I didn't do anything special as root or something, except for editing that file, so I can't think of anything else having caused the problem.

So I restarted my PC so the change could take effect. I had the correct time now. Unfortunately, now that my problem with the time was fixed, a new problem occured. After logging in to GNOME, I noticed I didn't have a working network connection anymore.

Before I create any misunderstanding, I should say this: my network connection was always working fine, both under Ubuntu and Windows XP (I'm dual booting). Because it's still working fine under Windows XP while I'm having problems with in Ubuntu, I'm 100% sure it's related to Ubuntu, and not the hardware. Concerning the network connection, I'm connected to my router via ethernet so that I can have internet access.

When I noticed that I had no network connection anymore after logging in to GNOME (before editing the file my network connection was behaving fine, and was working after logging in to GNOME) I went to System -> Administration -> Networking. I noticed eth0 was listed as "active". I figured out that when I deactivated, and activated eth0 again, I had my network connection back. However, this change is not permanent, I have to do it again every time I start up Ubuntu and log in to GNOME. Besides that, there is another curiosity with my network connection. I noticed that my internal IP address is changing every 10 minutes or so. For example, first it was 10.0.0.160, then it changed to 10.0.0.161, and now it is 10.0.0.171 after leaving my computer turned on for a while. I noticed this because Azureus started complaining that a port was already in use, and Gaim started having disconnects as well. The constantly changing internal IP address is not normal, and was introduced with this problem.

I hope someone can help me.

---

### Post by dmizer on 2006-05-29
this sounds like your typical ipv6 issue.

disable it by doing the following:
[https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28ipv6%29](https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28ipv6%29)

there are other ways to do this, but this one i can always find quickly. lol.

also, if you use firefox, browse to about:config and find the entry labled "network.dns.disableIPv6 -> true" ... double click on the line to set it as false.  restart firefox.

that should cure what ails ya.

---

### Post by jones_jj on 2006-05-29
Just curious how do you know it's an IPv6 issue and not some other issue?  To me it sounded like the fix to the bug is the issue to the problem, and reversing the fix would put the network back to what it was before the fix was implemented.  I am just trying to figure out how IPv6 is the cause of so many networking issues.  Thanks for the insight.

---

### Post by F for Fragging on 2006-05-29
Thanks for replies, but disabling IPv6 didn't fix it. I was told by someone else that the problem was probably related to dhclient, and after some searching I found [bug #21563]("https://launchpad.net/distros/ubuntu/+source/dhcp3/+bug/21563/") in Launchpad. I placed a comment there.

---

### Post by dmizer on 2006-05-29
[QUOTE=jones_jj]Just curious how do you know it's an IPv6 issue and not some other issue?  To me it sounded like the fix to the bug is the issue to the problem, and reversing the fix would put the network back to what it was before the fix was implemented.  I am just trying to figure out how IPv6 is the cause of so many networking issues.  Thanks for the insight.[/QUOTE]
well obviously i don't know for sure, because it wasn't the problem here.  but i experience similar problems to what is described here when i have ipv6 enabled so i offered a suggestion.

but i do wonder why ubuntu has ipv6 turned on by default.  or maybe it's simply my own limited understanding of the need for ipv6 in the desktop envornment.

---

### Post by F for Fragging on 2006-05-29
It seems that the real problem was [bug  #33968]("https://launchpad.net/distros/ubuntu/+source/dhcp3/+bug/33968/+index").

So I edited /etc/default/rcS and changed "UTC=no" back to "UTC=yes", which fixed the problem. My network connection is behaving normally again, but the time is now incorrect again. Thanks for your replies everybody.

---

