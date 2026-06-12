---
title: "Printing again!!!"
date: 2006-12-08
forum: Desktop Environments
---

### Post by madsurfer on 2006-12-08
Hi

Yet again I have lost the abillty to print workstation to workstation, both on the same network and both running Ubuntu. This did work but since I tried to get it working on windoze for some other PC'a it has stopped. To get it to at least show the printer I had to reinstall cups, but this is a long story and is covered by another thread. Now the remote machine is showing the network printer which is attached by a usb cable to a specific host. On this computer it is showing a normal printer and it is all ok for printing from the attached host. On the remote host I have installed a network printer using "Add Printer" with printer type being a Network Printer with URI being ipp://<hostname local printer>/printers/<name of printer on local machine>
This was accepted by the add printer. Now if I try to print from my remote machine it says its Printing 1 Job, but the local machine shows 0 jobs but says its ready and just sits there. What do I have to change to get it to work!!?

Please please help!

Adrian

---

### Post by jis on 2007-05-24
Bump. I have pretty much same situation.

I have configured cups using the web browser, see [https://help.ubuntu.com/6.06/xubuntu/desktopguide/C/printer-configuration.html](https://help.ubuntu.com/6.06/xubuntu/desktopguide/C/printer-configuration.html). A laser printer is connected to a parallel port of a Xubuntu 6.06.1 (Dapper) PC. There is another PC in the LAN, Xubuntu 7.04 (Feisty) in it. The remote PC sees the printer in its browser interface and jobs, too, but the job is not seen in the interface of the Dapper PC, I have even allowed remote administration of the printer, but it I try to set the printer options in the Feisty PC, Firefox complains "Unable to connect". Also, if I change some basic server settings, I am unable to use the browser interface, unless I restart cups from command line.

---

### Post by mitch.c on 2007-05-24
> **jis said:**
> A laser printer is connected to a parallel port of a Xubuntu 6.06.1 (Dapper) PC. There is another PC in the LAN, Xubuntu 7.04 (Feisty) in it.
Would you post the output from the following commands (on your Feisty machine):
```
$ aptitude search cupsys | grep ^i
$ lpstat -t
```

---

### Post by jis on 2007-05-24
$ aptitude search cupsys | grep ^i
i   cupsys                          - Common UNIX Printing System(tm) - server  
i   cupsys-bsd                      - Common UNIX Printing System(tm) - BSD comm
i   cupsys-client                   - Common UNIX Printing System(tm) - client p
i   cupsys-common                   - Common UNIX Printing System(tm) - common f
i   cupsys-driver-gutenprint        - printer drivers for CUPS                  
i   libcupsys2                      - Common UNIX Printing System(tm) - libs

$ lpstat -t
scheduler is running
no system default destination
device for LaserJet: ipp://192.168.0.102:631/printers/LaserJet
LaserJet accepting requests since Fri 25 May 2007 01:05:17 AM EEST
printer LaserJet is idle.  enabled since Fri 25 May 2007 01:05:17 AM EEST


After I launched a print job from Abiword:
$ lpstat -t
scheduler is running
no system default destination
device for LaserJet: ipp://192.168.0.102:631/printers/LaserJet
LaserJet accepting requests since Fri 25 May 2007 01:05:17 AM EEST
printer LaserJet is idle.  enabled since Fri 25 May 2007 01:05:17 AM EEST
        Network host '192.168.0.102' is busy; will retry in 30 seconds...
LaserJet-4              jarnos            8192   Fri 25 May 2007 01:07:28 AM EEST

No print so far.

---

### Post by mitch.c on 2007-05-24
Give me output on the Dapper machine (where the printer is attached) to this command:
```
$ cat /etc/cups/cupsd.conf | grep Listen
```
Or better yet, post /etc/cups/cupsd.conf

---

### Post by jis on 2007-05-24
There you have it:

/etc/cups/cupsd.conf
```
# Show troubleshooting information in error_log.
LogLevel debug
SystemGroup lpadmin
# Share local printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAddress @LOCAL
DefaultAuthType Basic
<Location />
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow @LOCAL
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType Basic
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  # Only the owner or an administrator can cancel a job...
  <Limit Cancel-Job>
    Order deny,allow
    Require user @OWNER @SYSTEM
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
Include /etc/cups/cups.d/ports.conf
Include /etc/cups/cups.d/browse.conf
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock

```

/etc/cups/cups.d/ports.conf
```
Listen localhost:631
Listen /var/run/cups/cups.sock

```

/etc/cups/cups.d/browse.conf
```
Browsing On
```

---

### Post by mitch.c on 2007-05-24
> **jis said:**
> /etc/cups/cups.d/ports.conf
```
Listen localhost:631
Listen /var/run/cups/cups.sock

```

I am glad you included /etc/cups/cups.d/ports.conf, it's what I was looking for but forgot it's a separate file on Dapper.

Change the first line to:
```
Listen *:631
```
Lose (or comment out) the last two lines in /etc/cups/cupsd.conf
```
 #Port 631
#Listen /var/run/cups/cups.sock
```
Restart cups
```
$ sudo /etc/init.d/cupsys force-reload
```

Try printing again.

---

### Post by jis on 2007-05-24
I think there is no need to comment out; it confuses [http://localhost:631/admin](http://localhost:631/admin) interface by unchecking "Share published printers connected to this system"  and "Allow remote administration". Anyway, remote printing works now. Modifying /etc/cups/cups.d/ports.conf helped. Thanks!

BTW. Should I make a bug report of this?

---

