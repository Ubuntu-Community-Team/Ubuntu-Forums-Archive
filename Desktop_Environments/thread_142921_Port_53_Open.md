---
title: "Port 53 Open?"
date: 2006-03-11
forum: Desktop Environments
---

### Post by OffHand on 2006-03-11
*Sorry for the double post but nobody seems to look at the one I posted it in*

Hi

I just ran a Shields Up scan and it tell me port 53 (DNS) is open.
Now I cannot remember I installed or activated a DNS so can
anyone explain to me how to stop/close this?

Thanx in advance,
Subsonic

---

### Post by shof2k on 2006-03-13
I don't know how to stop your DNS.  However you can get your firewall to block port 53 for you.

Have a look through the netstat man pages, there is an option to see what process is using that port.

---

### Post by Limulus on 2006-04-06
[QUOTE=subsonic_shadow]I just ran a Shields Up scan and it tell me port 53 (DNS) is open. Now I cannot remember I installed or activated a DNS so can
anyone explain to me how to stop/close this?[/QUOTE]
I just noticed I had the same problem and here's what I did to fix it :)

0a. Use the Network Monitor applet (click the Support tab) to determine your IP address (if you are using a router, it will be different from what the outside world sees; e.g. 192.168.1.100)

0b. go System Tools -> Network Tools and click the Port Scan tab.  Enter your IP address (e.g. 192.168.1.100) and press Scan.  That's how I found out my port 53 was open (I'm behind a router firewall, so it wasn't exposed to the web; GRC's [Shields UP!](https://www.grc.com/x/ne.dll?bh0bkyd2) utility is great for finding open ports exposed to the internet BTW... my router was exposing (well, not *stealthing*) [port 113](http://grc.com/port_113.htm), unbeknownst to me)

1. as per [this page](http://www.servepath.com/support/debian_faq.htm), open terminal and run:

```
$ sudo fuser 53/tcp
```
(or use "udp" instead of "tcp") you'll get a result like:
```
53/tcp:               7718
```
The "7718" for me was the process identification (PID) for the "processes spawned by the port in question, or [...] the process actually responsible for listening"

2. go System Tools -> System Monitor, go Edit -> Preferences and under the Processes tab in Process Fields, put a check next to "ID" and press Close.  Now in the Processes tab of the main window, you'll see "ID" listed.  Click it to arrange by ID and find the number that showed up when you used fuser.  For me it was *usr/sbin/named* with some arguments.

3. go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and scroll down to the "Search the contents of packages" form; enter the keyword (in my case, it was the word "named" without quotes).  The results indicated that it occurs in two packages: bind and bind9.

4. go to Synaptic and find the packages in question.  I had "bind9" installed.  Dunno why (probably a dependency for something I installed and uninstalled a while back).  You can confirm that the file was installed by the package if you right-click the package, select Properties and click the Installed Files tab.  Now try uninstalling it.  If all goes well, it will be the only package Synaptic wants to uninstall.  If not, you have to figure out what you want to uninstall ;)

5. go back to System Monitor and confirm the process is closed (if not, you can kill it).  Go back to Network Tools (or whatever you were testing with) and rescan to confirm that the port is now closed.

Hope that works as well for you as it did for me! :)

---

### Post by dcstar on 2006-04-06
[QUOTE=subsonic_shadow]*Sorry for the double post but nobody seems to look at the one I posted it in*

Hi

I just ran a Shields Up scan and it tell me port 53 (DNS) is open.
Now I cannot remember I installed or activated a DNS so can
anyone explain to me how to stop/close this?

Thanx in advance,
Subsonic[/QUOTE]
Unless your Ubuntu box is running a public IP address (which few are), that is your router with the open DNS port, and there is nothing in Ubuntu's control that will do anything about it.

You will probably need to change a setting in your router.

---

