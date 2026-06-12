---
title: "cups authorizations problem"
date: 2009-02-20
forum: General Help
---

### Post by T-MAN3000 on 2009-02-20
I've been trying to get CUPS to work and have gotten to the point where I can acces the web interface, see my printer (a HP P1005 Laserjet) get a test page to be accepted and processed, but not actually printed!

The error message I'm seeing in the error log is this:

```
E [20/Feb/2009:21:46:06 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [20/Feb/2009:21:53:20 +0100] Resume-Printer: Unauthorized
E [20/Feb/2009:22:18:26 +0100] Unable to bind socket for address 192.168.1.100:631 - Cannot assign requested address.
E [20/Feb/2009:22:19:30 +0100] Unable to bind socket for address 192.168.1.100:631 - Cannot assign requested address.
E [20/Feb/2009:22:22:32 +0100] Unable to bind socket for address 192.168.1.100:631 - Cannot assign requested address.
E [20/Feb/2009:22:22:39 +0100] encrypt_client: Unable to encrypt connection from 192.168.1.100!
E [20/Feb/2009:22:22:39 +0100] encrypt_client: A TLS fatal alert has been received.
E [20/Feb/2009:22:22:41 +0100] encrypt_client: Unable to encrypt connection from 192.168.1.100!
E [20/Feb/2009:22:22:41 +0100] encrypt_client: A TLS fatal alert has been received.
E [20/Feb/2009:22:22:42 +0100] encrypt_client: Unable to encrypt connection from 192.168.1.100!
E [20/Feb/2009:22:22:42 +0100] encrypt_client: A TLS fatal alert has been received.
E [20/Feb/2009:22:24:04 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [20/Feb/2009:22:24:12 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [20/Feb/2009:22:26:45 +0100] Pause-Printer: Unauthorized
E [20/Feb/2009:22:26:53 +0100] Resume-Printer: Unauthorized
E [20/Feb/2009:22:28:03 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [20/Feb/2009:22:29:19 +0100] Pause-Printer: Unauthorized
E [20/Feb/2009:22:29:25 +0100] Resume-Printer: Unauthorized
E [20/Feb/2009:22:29:36 +0100] PID 16026 (/usr/lib/cups/backend/cups-pdf) stopped with status 5!

```

My cupsd.conf file looks like this:

```
#
#
#   Sample configuration file for the Common UNIX Printing System (CUPS)
#   scheduler.  See "man cupsd.conf" for a complete description of this
#   file.
#

# Log general information in error_log - change "info" to "debug" for
# troubleshooting...
LogLevel warning

# Administrator user group...
SystemGroup lpadmin


# Only listen for connections from the local machine.
Listen 631
Listen 192.168.1.100
Listen /var/run/cups/cups.sock

# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic
DefaultEncryption IfRequested

# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow 192.168.1.100
  Allow 192.168.1.*
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Encryption Required
  Order allow,deny
  Allow 192.168.1.100
</Location>

# Restrict access to configuration files...
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
  Allow localhost
  Allow 192.168.1.100
</Location>

# Set the default printer/job policies...
<Policy default>
  # Job-related operations must be done by the owner or an administrator...
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>

  # All administration operations require an administrator to authenticate...
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>

  # All printer operations require a printer operator to authenticate...
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
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

#
#

```

What am I doing wrong? Probably a few things, but please bear with me, I'm new to CUPS ;)

---

### Post by Yellow Pasque on 2009-02-20
Is your user in the lpadmin group?
```
groups
```

---

### Post by T-MAN3000 on 2009-02-20
it is: 

```
tiemen3r@sukke:~$ sudo adduser tiemen3r lpadmin
The user `tiemen3r' is already a member of `lpadmin'.
```

---

