---
title: "Windows Shared Printer Not Viewable in CUPS"
date: 2011-05-04
forum: Desktop Environments
---

### Post by stevedude on 2011-05-04
Background: I have a Desktop running Windows 7 Professional that has a Brother HL-2140 laserjet printer attached to it. I can successfully view the Windows 7 shares using SAMBA, but when I choose NETWORK PRINTER > WINDOWS PRINTER via SAMBA >  BROWSE, I receive an error "NO PRINT SHARES - There were no print shares  found.  Please check that the Samba service is marked as trusted in  your firewall configuration."

I have no firewall installed, the Windows printer is shared, and before I upgraded to Natty, all worked fine under Ubuntu Maverick.

When I run the "testparm" command, I noticed that the line under [printers] states "browseable = No" even though in my smb.conf file it is set to "browseable = yes" (and I have changed/saved this file several times, using "sudo" with the same result).

I would like someone to look over my enclosed settings and see if there is a tweak I need to make in order to browse my Windows 7 shared printer.  Thanks in advance for your time.

testparm results of SMB.CONF:

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
    workgroup = FAMILY
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    name resolve order = lmhosts host wins bcast
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
    printcap name = cups
    dns proxy = No
    wins support = Yes
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d
    valid users = steve, @steve

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    **[COLOR=Red]browseable = No[/COLOR]**  [COLOR=Blue] (How do I change this?)
[/COLOR]
[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers


This is the CUPS configuration file:

LogLevel warn
MaxLogSize 0
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Enable printer sharing and shared printers.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
BrowseRemoteProtocols CUPS dnssd
BrowseAddress @LOCAL
BrowseLocalProtocols CUPS dnssd
DefaultAuthType Basic
<Location />
  # Allow shared printing...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin>
  Order allow,deny
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
</Location>
<Policy default>
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    Order deny,allow
  </Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default CUPS-Get-Devices>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>
<Policy authenticated>
  <Limit Create-Job Print-Job Print-URI Validate-Job>
    AuthType Default
    Order deny,allow
  </Limit>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job CUPS-Get-Document>
    AuthType Default
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
    AuthType Default
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

---

### Post by stevedude on 2011-05-08
Figured this out myself. For some reason Natty won't let me access my Windows shares either browsing in the Printer utility program or via Nautilus file manager.

What I had to do was use the "Other" setting for setting up a printer because browsing for a printer via SAMBA showed my workgroup and the name of the Windows 7 desktop, but not the shared printer on the Windows 7 desktop.

By entering the IP address of the Windows 7 desktop and the printer name, I am able to print now, even though this does not address the original dilemma.

So if your reading this and using Unity, try: Go to DASH > Type "Printing" (without quotations) > Launch the printers program > Add a new printer > Other, and type in the URI of the printer, then select the proper driver for your printer model and do a test print.
[Standard Gnome Desktop is System > Administration >Printing]

 For me, I could not use this format: smb://MyworkgroupName/Windows7DesktopName/PrinterName. I had to do smb://123.456.789.10/PrinterName

Everything works as it should.

---

### Post by spohn on 2011-05-09
Hi,

The same "feature" is present in "Ubuntu Classic": I had to enter the IP address of the windows box to get to the printer via Samba.

It's quite amazing such a basic functionality be broken in Natty.

Marcelo

---

