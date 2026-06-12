---
title: "Printing to a Deskjet 3420 in a XP box."
date: 2006-06-09
forum: Desktop Environments
---

### Post by Hellaxe on 2006-06-09
Hello:
I'm having this problem that when i try to print to a HP Deskjet 3420 in an Xp box the paper don't came out.
The printer does all the steps until the pulling paper part, then it stops and nothing happens.

Is it a problem whith the ubuntu/dapper drivers of the DJ 3420?
I used to print there with Breezy.
This is my cupsd.conf:

```
# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin

# Only listen for connections from the local machine.
# These settings are configured in /etc/cups/cups.d/ports.conf so that
# changing them does not require to change this file.
# Listen localhost:631
# Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
# The 'Browsing' setting is configured in /etc/cups/cups.d/browse.conf
# so that changing it does not require to change this file.
# Browsing Off
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow @LOCAL
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Basic
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an adminstrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an adminstrator to authenticate...
  <Limit Pause-Printer Resume-Printer Set-Printer-Attributes Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Add-Printer CUPS-Delete-Printer CUPS-Add-Class CUPS-Delete-Class CUPS-Accept-Jobs CUPS-Reject-Jobs CUPS-Set-Default>
    AuthType Basic
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # Only the owner or an administrator can cancel or authenticate a job...
  <Limit Cancel-Job CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

# Include files in /etc/cups/conf.d
Include /etc/cups/cups.d/ports.conf
Include /etc/cups/cups.d/browse.conf

```

Thanks in advance.

---

