---
title: "Pass through printing through Telnet / SSH"
date: 2009-02-17
forum: General Help
---

### Post by casperl on 2009-02-17
Hi, 

How can I implement pass-through printing through a Linux terminal connection using either Telnet or SSH?

Pass-through printing is where a series of printer commands are sent between escape codes to a terminal whereby the printer codes are directed to the attached terminal printer.

The requirement is to replace current Wyse and Sunnix terminals (and future connections) with existing PC's running Xubuntu 8.10.  The server application is a medical system that has been migrated from SCO to a Linux server.  Windows based workstations connect to the server through a terminal program called Netterm that implements pass-through printing.

Most specialised Windows programs have the facility to direct printer output directed to the terminal to a local printer.  The only terminal program that I could locate on Linux that supports that feature is Putty that has been ported to Linux from Windows.  Putty does work, but where dedicated terminals are being replaced by PC's I would prefer to bypass the Ubuntu GUI completely and connect through a shell script using either Telnet or SSH.

How can I implement this feature through either Telnet or SSH connections on a local Ubuntu 8.10 desktop?  I have googled and though the question has been asked on how to implement pass-through-printing in Linux, no clear answers have been given.

(BTW, I am well aware that SSH is secure and that allowing Telnet is a security risk, but this is an existing site with a local network protected by a firewall - unfortunately this legacy configuration is beyond my control.)

TIA

Casper

---

### Post by albandy on 2009-02-17
I've got the same problem with an iseries and linux client, and I've used the lp5250d daemon that register a printer in iseries, but you're in another environment.

lpr can print to remote printer, for example, if you've a printer in your desktop computer , you can print from ssh this way:

lpr -H ip_of_the_desktop:631

I remeber that it could be configured by environment variables like PRINTER or things like that. see the lpr documentation

It's possible to register the local printer to the server but I don't remember how 
to do that.

read all the lpr documentation and the lpr environment variables.

---

