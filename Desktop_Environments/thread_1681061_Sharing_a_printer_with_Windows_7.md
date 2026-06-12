---
title: "Sharing a printer with Windows 7"
date: 2011-02-03
forum: Desktop Environments
---

### Post by Heathicus on 2011-02-03
I'm a relative Ubuntu/Linux newbie, and I've been hammering at this problem for a while.  I've read all the forum posts I can find, I've googled to death, but nothing seems to fix my problem.

 I have Ubuntu 10.04 running on my desktop PC.  My wife's laptop is running Windows 7.  I have our Canon MP490 printer attached to my PC and I'm trying to share it so she can print from her laptop.

 The printer works fine and I can print from Ubuntu.  I have a VirtualBox VM running Windows XP and it can access the shared printer and print with no problems.

 I have these printing related lines in smb.conf:

 ```

[Global]
    load printers = yes
    printing = CUPS
    printcap name = CUPS

[printers]
    guest ok = yes
    browseable = yes
    use client driver = yes

```The content of my cupsd.conf file is as follows (honestly, I don't understand most of it):
 ```
 
LogLevel warn
MaxLogSize 1m
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Share local printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseRemoteProtocols
BrowseAddress @LOCAL
BrowseLocalProtocols cups ldap slp
DefaultAuthType Basic
<Location />
  # Allow shared printing...
  Order allow,deny
  Allow all
</Location>
<Location /admin>
  # Restrict access to the admin pages...
  Order allow,deny
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Restrict access to the configuration files...
  Order allow,deny
</Location>
<Policy default>
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
  <Limit Create-Job Print-Job Print-URI>
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

``` On my XP virtual machine, I was able to add the printer as a network printer using the port [http://192.168.103:631/printers/mp490-series](http://192.168.103:631/printers/mp490-series).

 This is the process I have used to try to add the printer.


[LIST=1]
[*]Installed printer drivers.
[*]Start the Add Printer wizard (Start -> Devices & Printers -> Add a printer)
[*]Choose "Add a network, wireless, or Bluetooth printer."
[*]Stop the automatic search and click "The printer that I want isn't listed."  (I've alway waited for the search to complete - the printer was not found.)
[*]Choose "Add a printer using a TCP/IP address or hostname."
[*]Complete the Leave the Device Type as "Autodetect."  Enter "http://192.168.1.103:631/printers/mp490-series" as the Hostname or IP address.  (I also tried it without the "http://" and replacing the IP address with the host name of the server, and also added the server host name/IP address to the Windows hosts file.)
[*]The next page in the dialog box always says "The device is not found on the network."
[/LIST]
 
 On the Windows 7 machine, I can access the CUPS web interface (at [http://192.168.1.103:631](http://192.168.1.103:631)), and can see the printer properties (at [http://192.168.103:631/printers/mp490-series](http://192.168.103:631/printers/mp490-series)).  I disabled the firewall. Still, nothing.  So where am I going wrong?

---

### Post by Heathicus on 2011-02-06
Bump 

Anybody?

---

### Post by loza1984 on 2011-02-12
I was having the same problem while trying to share my printer, but managed to get it working thanks to a post on a blog:

**Sharing with Windows**
It is  usually best to use a native printing protocol. For Ubuntu, LPD and CUPS  are native. Most versions of Windows support network printing to LPD  servers, so sharing with LPD should be enough, but it requires user to  configure their printers.

Native Windows environments can share printers using the Server Message Block  (SMB) protocol. This allows Windows users to browse the Network  Neighborhood and add any shared printers-very little manual  configuration is required. For Ubuntu to share a printer with Windows  users requires installing SAMBA, an open source SMB server.

On the print server:
1. Install SAMBA on the print server. This provides Windows SMB support.
sudo apt-get install samba

2. Create a directory for the print spool.
sudo mkdir /var/spool/smbprint

3. Edit the SAMBA configuration file: /etc/samba/smb.conf

4. Change workgroup = to match your Windows Workgroup.

5.  Under the [global] section is an area for printer configuration.  Uncomment (remove the leading ;) the load printers = yes and CUPS  printing lines.

6. Set the [printers] section (further down) to look like this:
[printers]
   comment = All Printers
   browseable = no
   security = share
   use client driver = yes
   guest ok = yes
   path = /var/spool/smbprint
   printable = yes
   public = yes
   writable = yes
   create mode = 0700

This setting allows any Windows client to access the printers without a password.

7.  (Optional) Under the [printers] section, set browseable = yes. This  allows Windows systems to see the printers through the Network  Neighborhood.

8. Restart the SAMBA server.
sudo /etc/init.d/smbd restart

On  the Windows client, you can add the printer as if it were a Windows  printer. For example, if the server's name is printer.example.com and  the printer is Okidata127, then the shared printer resource would be  \\printer.example.com\Okidata127. Windows clients will need to install  their own print drivers.



  Hope this works for ya, Phill.

---

### Post by Heathicus on 2011-02-13
Thank you for replying!!  This actually helped, I think.  And I'm making progress, but I'm not quite there yet.

I made the changes to my smb.conf file as per above.  Now, from the Windows 7 machine, I can see the printer (I changed "browseable" to yes) when I browse the server.  I can "connect" to the printer and install the drivers.  But, I still can't print.  Print jobs never go into the queue.  And when I go to the Printer Properties dialogue and click on the Ports tab, no port is checked, but everything is grayed out (all of the existing ports, and the add/delete/configure buttons).

---

