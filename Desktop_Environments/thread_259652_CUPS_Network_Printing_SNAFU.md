---
title: "CUPS Network Printing SNAFU"
date: 2006-09-17
forum: Desktop Environments
---

### Post by greenstar on 2006-09-17
I've followed the guide at easylinux.info, as well as a thousand other random places with CUPS network printing info. Now I have the printer installed as a network printer and when I attempt to print to it, paper does actually come out. However, it doesn't print what it should. Instead, it prints something like:

ApK XXc014e     AY

in the top left corner of the page, and then nothing else. Local printing does not display this behavior.

The print server box is running Xubuntu Dapper & the other boxes are running Ubuntu Dapper.

IP of printserver box: 192.168.1.100
running ```
lpq
``` on the printserver gives:
```
BJC-8200 is ready
no entries
``` 
running ```
lpq -h 192.168.1.100
``` on the remote box gives:
```
BJC-8200 is ready
no entries
``` 

The printer is a CanonS300 named BJC-8200, which works fine on both machines when directly plugged into usb. The print server machine is visible to the other boxes on the network in Places->Network Servers.

[https://192.168.1.100:631/printers](https://192.168.1.100:631/printers) in my browser gets me the CUPS web config page. I re-enabled administration as per the instructions in /usr/share/doc/cupsys/README.Debian.gz, and then configured administration via the web interface. I tested this by adding a local printer (the same one with a different name) and did a test print which came out fine. The web admin was done from the box I want to print from.

Any help would be appreciated.

Thanks in advance,
Greenstar

---

### Post by nix4me on 2006-09-17
Is the source of the print request from a windows machine?
If so, checkout the octet stream setting in the cups/cups.d config files.

nix4me

---

### Post by greenstar on 2006-09-17
The sending machine is running Ubuntu Dapper, the receiving machine is Xubuntu Dapper.

Greenstar

---

### Post by greenstar on 2006-09-19
Anyone have any ideas?

Greenstar

---

### Post by xzithlan on 2006-09-21
I have a similar problem with my CUPS configuration.

The server, shmi, is running Kubuntu 6.06 Dapper, and HP Deskjet 648C is connected via parallel port.

The client, Leia, is running Kubuntu 6.06 Dapper

I can ssh to and from both Leia and Shmi and have x forwarding set up, so I know the network works fine.  My firewall is configured to allow port 631 to be forwarded to shmi.

Printing works great locally from Shmi. I've set up the printer on Leia from the printers icon in the systemsettings. When I send a job it appears to work just fine. In actually, it prints multiple pages with meaningless text and garbage characters on the first few lines.

lpq on Leia gives
[FONT="Courier New"]HP_Deskjet is ready
no entries[/FONT]

Using Adept, I've checked the version of CUPS installed on both systems and they are both identical, 1.2.2-0ubuntu0.6.06.

Any ideas?

---

### Post by greenstar on 2006-09-24
xzithlan: Looks like we've been hung out to dry again. This isn't the only time I've been left flapping in the breeze by the community. I have a thread on the forums about my Kino being broken, and I can't get help with that either. 

Greenstar

---

