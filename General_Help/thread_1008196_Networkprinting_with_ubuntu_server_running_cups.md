---
title: "Networkprinting with ubuntu server running cups"
date: 2008-12-11
forum: General Help
---

### Post by damas on 2008-12-11
Hi all.

I have a problem configuring my printer.

Its a canon pixma (usb) and it works perfectly on my ubuntu server through cups. (meaning if i go to the servers ip:631 i can print a sample page with no problems.

I have managed to share the printer to my other computers (1 xp, 1 vista) i can browse the network and find them, and install.

BUT, when i print, the window bar in the printing que in window says "Access denied, unable to connect".

I want to have a very low security in the /etc/cups/cupsd.conf because i only have a local network.

here is my cupsd.conf file:

[HTML]LogLevel warning

SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL
DefaultAuthType None
<Location />
	allow all
  Allow localhost
  Allow from @LOCAL
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow from all
</Location>
<Location /admin>
  Allow all 
  Allow 192.168.1.*
  # Allow remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin/conf>
  AuthType None
  Allow localhost
  Allow all
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow all
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Allow all
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType none
    Allow all
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Order deny,allow
    allow all
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
DefaultEncryption Never[/HTML]

In some guides Im suppoest to create a user cupsys and group shadow cant see why, and from what i understand i dont need samba to share the printer.
 Any ideas???

Thanks in advance!

/Tomas

---

