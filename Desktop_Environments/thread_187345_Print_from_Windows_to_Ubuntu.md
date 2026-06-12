---
title: "Print from Windows to Ubuntu"
date: 2006-06-02
forum: Desktop Environments
---

### Post by rbp1976 on 2006-06-02
Ok, I have read alot of the forums here as well as googled for answers but to no avail. I need helpwith my network printing. I've configured my cupsd.conf file using advice from other forums. It is filled with a bunch of gibberish which I have no idea what it means: 

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
<Location />
Order Deny,Allow
Deny From All
Allow From 192.168.2.*
</Location>

<Location /printers>
 AuthType None
 Order Deny,Allow
 Deny From None
 Allow From 192.168.2.*
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

#
#


Someone please help me. The printer shows up when I add printer (probably through Samba) but then says unable to connect. I apologize if this has already been discussed somewhere else, but I feel I need some personal help based on my specific configuration. Thanks in advance for any help. 

P.s. The rest of this OS kicks butt. Everything else worked upon installation.:D

---

### Post by Shadowline on 2006-06-02
I followed this [https://wiki.ubuntu.com/NetworkPrintingWithUbuntu](https://wiki.ubuntu.com/NetworkPrintingWithUbuntu) wiki page and was able to get my XP and Win2k boxs to print thru my Ubuntu box. I know it's for breezy but it worked for dapper for me. Best of luck....

---

### Post by rbp1976 on 2006-06-03
Ok, I tried using that example, but I think I need help with the IP address. When I restarted CUPS It said this: 

* Restarting Common Unix Printing System: cupsd cupsd: Child exited with status 1!

Here is what I have for my <Location/>

    <Location />
    AuthType None
    Order Deny,Allow
    Deny From All
    Allow From @LOCAL
    Allow From 192.168.2.2/16
    Allow From 192.168.2.4/24
    </Location>


The allow from IP addresses are for each of my two computers. I also used them for the rest of the <Location/Printer> etc...
I'm not sure what the /16 and /24 mean.

Still stuck!](*,)

---

### Post by blair on 2006-06-03
The /16 and /24 are subnet masks. An IP address has 32 bits and is represented as 4 ASCII integers in the 0-255 range. e.g. 192.168.10.5.

/16 means the first 16 bits (first 2 characters) are the network number and the last 16 bits (last 2 characters) are the host number. /24 means  first 24 bits/3 characters are the network number and last 8 bits/1 character are the host number. 

My interpretation is:

Allow From 192.168.2.2/16 = Allow print requests from hosts with IP address 192.168.*.*

Allow From 192.168.2.4/24 = Allow print requests from hosts with IP address 192.168.2.*

Obviously the first Allow statement makes the second Allow statement superfluous.

---

### Post by rbp1976 on 2006-06-05
[QUOTE=blair]The /16 and /24 are subnet masks. An IP address has 32 bits and is represented as 4 ASCII integers in the 0-255 range. e.g. 192.168.10.5.

/16 means the first 16 bits (first 2 characters) are the network number and the last 16 bits (last 2 characters) are the host number. /24 means  first 24 bits/3 characters are the network number and last 8 bits/1 character are the host number. 

My interpretation is:

Allow From 192.168.2.2/16 = Allow print requests from hosts with IP address 192.168.*.*

Allow From 192.168.2.4/24 = Allow print requests from hosts with IP address 192.168.2.*

Obviously the first Allow statement makes the second Allow statement superfluous.[/QUOTE]

Forgive me if this is obvious, but I can get rid of all the "Allow From..." except for one? I.E "Allow From 192.168.2.*/24. Just so it's clear to me, if I have  two computers and both IP addresses are similiar except for the last part, then this will work?

---

