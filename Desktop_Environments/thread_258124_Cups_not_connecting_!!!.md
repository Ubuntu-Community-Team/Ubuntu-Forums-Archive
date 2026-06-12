---
title: "Cups not connecting !!!"
date: 2006-09-15
forum: Desktop Environments
---

### Post by pod25 on 2006-09-15
Sorry guys, I've started a new thread so it's easier to find.

I'm getting this error when i try to add my new printer :
```
The cups server could not be contacted
```

Below are the contents of my cupsd.conf

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
# These settings are configured in /etc/cups/cups.d/ports.conf so that
# changing them does not require to change this file.
 Listen localhost:631
 Listen 192.168.1.201:631

# Show shared printers on the local network.
# The 'Browsing' setting is configured in /etc/cups/cups.d/browse.conf
# so that changing it does not require to change this file.
# Browsing Off
BrowseOrder allow,deny
BrowseAllow @LOCAL
BrowseAddress @LOCAL

# Default authentication type, when authentication is required...
DefaultAuthType Basic
AuthGroupName shadow

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



 Set the default printer/job policies...
<Policy default>
   Job-related operations must be done by the owner or an adminstrator...
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

```

---

### Post by moore.bryan on 2006-09-15
*did you chmod the cups file?*

---

### Post by pod25 on 2006-09-15
> **moore.bryan said:**
> *did you chmod the cups file?*

No !!

But so far what i've done is :

sudo apt-get remove cupsys cupsys-client

Then rebooted...  Then :

sudo apt-get install cupsys cupsys-client

But the problem is still there ?

What should I chmod to ?

---

### Post by moore.bryan on 2006-09-15
[I]```
sudo chmod +x cupsd.conf
```
no guarantee, but it may work.
[/I]

---

### Post by pod25 on 2006-09-16
> **moore.bryan said:**
> [I]```
sudo chmod +x cupsd.conf
```
no guarantee, but it may work.
[/I]

Sadly it did not work.
More suggestions please.

---

### Post by moore.bryan on 2006-09-16
[I]what does 
```
killall -HUP cupsd
/etc/init.d/cups restart
/etc/software/init.d/cups restart
```
do for you?[/I]

---

### Post by llamakc on 2006-09-16
There is no reason to make a configuration file for CUPS executable. CUPS runs great for me and my conf file looks like:

```

ken@nola:~$ ls -l /etc/cups/cupsd.conf
-rw-r--r-- 1 root root 2640 2006-08-03 03:53 /etc/cups/cupsd.conf

```

What you should do is check your logs @ /var/log/cups after changing the LogLevel in /etc/cups/cupsd.conf to "debug" as documented in the cupsd.conf file.

My cupsd.conf has

```


# Only listen for connections from the local machine.
# These settings are configured in /etc/cups/cups.d/ports.conf so that
# changing them does not require to change this file.
# Listen localhost:631
# Listen /var/run/cups/cups.sock


```

Are you trying to use the web interface for cups or the gnome frontend? I always add user cupsys to the shadow group (as documented at the end of /usr/share/doc/cupsys/README.Debian.gz)

```

zcat /usr/share/doc/cupsys/README.Debian.gz

<snipped>
- Administration over the web interface is disabled by default since it
   requires the CUPS daemon to be able to read /etc/shadow.  If you want to
   enable web administration with shadow passwords (authentication type
   'basic'), put the user cupsys into group shadow by

       adduser cupsys shadow

   as root.

   Only users who are in group 'lpadmin' can administrate printers (using
   gnome-cups-manager, lpadmin or any other frontend but the web
   interface).  To allow printer administration to user joe, put him into
   this group by executing

       adduser joe lpadmin

   (again as root).

```

Good luck.

---

### Post by moore.bryan on 2006-09-16
> **llamakc said:**
> There is no reason to make a configuration file for CUPS executable.
*just suggested it because the "trick" made my cups work... :-)*

---

### Post by pod25 on 2006-09-16
I forgot to mention.
I also get this when i try to restart cups

```
cupsd: Child exited with status 1!
```

Does this help to solve the problem ?

---

### Post by moore.bryan on 2006-09-16
> **pod25 said:**
> I forgot to mention.
I also get this when i try to restart cups
```
cupsd: Child exited with status 1!
``` 
Does this help to solve the problem ?
*i don't think it solves it, but i don't remember ever reading someone having that problem... have you tried reinstalling the cupsd?*

---

### Post by pod25 on 2006-09-16
> **moore.bryan said:**
> *i don't think it solves it, but i don't remember ever reading someone having that problem... have you tried reinstalling the cupsd?*

Sorry, I asked if it would *help* to solve the problem.

And yes, as previously stated above, I have removed and re-installed cups server and client.

I'm at a loss now.

---

### Post by moore.bryan on 2006-09-16
*you and me both... sorry i can't be of more help.  if i think of something, i'll post it.*

---

### Post by llamakc on 2006-09-16
Are you using apt-get to remove the packages and reinstall them? You should purge the configuration files before reinstalling.

---

### Post by pod25 on 2006-09-16
How do I purge ?

---

### Post by llamakc on 2006-09-16
apt-get remove --purge nameofpackage

---

### Post by pod25 on 2006-09-16
> **llamakc said:**
> apt-get remove --purge nameofpackage

You are a STAR . . . . At last, I'm in :D

---

### Post by Thav on 2006-09-19
> **llamakc said:**
> apt-get remove --purge nameofpackage

Purging and reinstall cupsys and cupsys-client seems to have done the trick for me. I ran into this issue after upgrading from Breezy to Dapper.

---

