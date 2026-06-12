---
title: "Ubuntu and network printers with CUPS"
date: 2006-07-24
forum: Desktop Environments
---

### Post by kikinovak on 2006-07-24
Hi,

I'm a sysadmin living in Montpezat (South France), and a 100% GNU/Linux user since the days of Y2K or so. I've been a die-hard Slackware user for a few years, and I recently gave Ubuntu a try and I admit I sort of like it, except a few nasty details like GRUB installs without asking first, apt-proxy needing a kick in the config file to work properly, or the horrible things the Ubuntu people did to CUPS.

Speaking of CUPS. With the "classical distros" (Slack, Debian, RHEL, ...), setting up a network printer was a matter of 1) writing a fifteen-line cupsd.conf from scratch on the server side, and 2) writing a one-line client.conf (ServerName [server]) on the client side, lpstat -t and there you go. 

Now then. I've setup a printer the Ubuntu way (click, click, ...) on one machine on the LAN. Q: what's the Ubuntu way to make this printer visible and accessible on the network? I'm not against graphical tools (my favourite configuration tool is Vim:cool: ), only... I've never used them. I'm lost. (Should have entitled this message *** EXPERT NEEDS GUI HELP PLEASE HELP *** LOL)

Anyway. Any suggestions?

---

### Post by gborzi on 2006-07-24
Hello, to make your printers visible from outside give these two commands:
> sudo /usr/share/cups/enable_browsing 1
sudo /usr/share/cups/enable_sharing 1
These commands will change the content of /etc/cups/cups.d/browse.conf to *Browsing On* and the content of /etc/cups/cups.d/ports.conf to
> Listen 631
Listen /var/run/cups/cups.sock
Note: you can prepend the 631 above with a specific network interface, e.g. if your print server is also a router.
Obviously you need to restart cupsys.

---

### Post by kikinovak on 2006-07-25
Thanks for the suggestion. I applied both of the commands... by the way: each one takes care of restarting cupsys, so there's no need to do that manually. 

But how can I make the printer visible on the client side (since there's no client.conf file in Ubuntu's CUPS)? 

The machine acting as a print server is running plain Ubuntu 6.06 (with GNOME), the client machines are running Xubuntu. I waited for 30 seconds (which is the time it usually takes for CUPS to announce a printer on the network), but 'lpstat -t' shows there's no default destination.

Any suggestions for that?

---

### Post by gborzi on 2006-07-25
I connected the client using the gnome-cups-manager, selecting "New Printer" -> "Network Printer", then entering the URI manually as:
> http://192.168.0.1:631/printers/<PrinterName>
where 192.168.0.1 is the address of the server.

---

### Post by kikinovak on 2006-07-26
Thanks very much! I added the gnome-cups-manager to XFCE, started it via xfrun, and everything worked like a charm.

Cheers,

Niki

---

