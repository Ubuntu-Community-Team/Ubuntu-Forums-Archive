---
title: "No CUPS for vista client."
date: 2009-03-28
forum: General Help
---

### Post by infallible on 2009-03-28
I want my vista laptop to print to my HP Printer. The printer works fine from the ubuntu box it is wired to, and after setting up CUPS, I can print the test page from the CUPS web interface. 

The laptop refuses to acknowledge CUPS. I can't access the web interface, I cant autodetect the printer or manually set up (directingto [http://myip:631/printers/printername](http://myip:631/printers/printername)) . Here's my cupsd.conf:

```

LogLevel warning
SystemGroup lpadmin
# Allow remote access
Port 631
Listen *:631
Listen 192.168.1.104
Listen /var/run/cups/cups.sock
# Share local printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAddress @LOCAL
DefaultAuthType Basic
DefaultEncryption IfRequested
<Location />
  Allow localhost
  Allow 192.168.1.*
  Allow all
  # Allow shared printing and remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
  Encryption Required
  # Allow remote administration...
  Order allow,deny
  Allow all
</Location>
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Allow localhost
  Allow 192.168.1.104
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow all
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order allow, deny
    Allow all
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

```

Has anyone else been able to make this work? Do I also need to set up samba beyond the default? I haven't worked with CUPS before, but it wouldn't surprise me to learn vista barred it...

---

### Post by redmk2 on 2009-03-29
I believe what you are looking for is IPP (Internet Printing Protocol) via CUPS.  Try [**here**]("http://www.google.com/search?hl=en&q=IPP++print&btnG=Search") for a start.

This is the [**description**]("http://en.wikipedia.org/wiki/Internet_Printing_Protocol") of IPP from Wikipedia.

---

### Post by infallible on 2009-03-29
To fix this, I changed back to the default cups.conf, adding a line to listen over the local ip. I used the Modify Printer option of the CUPS web interface to change the "device" from the already installed printer driver to an IPP Printer. The next page had me reselect the drivers. The vista laptop was then able to see the printer, and I loaded the Microsoft Imagesetter generic driver, as there is no vista support forthis printer. After, the printer didn't work, so I had to modify again and change the device back to the lpt printer, and reloaded the printer in the laptop. Not sure what went wrong, but it seems to be working now!

---

