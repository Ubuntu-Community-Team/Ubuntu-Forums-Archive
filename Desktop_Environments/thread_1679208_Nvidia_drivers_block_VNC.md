---
title: "Nvidia drivers block VNC"
date: 2011-01-31
forum: Desktop Environments
---

### Post by Halkus on 2011-01-31
If I install Nvidia drivers on the server in my loft, I cannot VNC to Gnome properly.

If I VNC in I get a snapshot of the desktop, and mouse/keyboard movements are sent correctly, but the display does not refresh. I can close the VNC viewer and restart it, and I'll get a single refresh of the screen.

This occurs when I enable Nvidia drivers, and stops when I disable them.

Is there a more robust alternative to VNC'ing in, or is there some way I can install the Nvidia drivers and still have VNC?

I believe it might be something to do with desktop effects, which seem to be enabled if I enable the Nvidia driver.... but I'm a complete idiot on Ubuntu, I've only had it installed for a day.

---

### Post by mharrison on 2011-01-31
Right click on the Desktop and select Change Background.

When that window pops up, click on the last tab and select the 1st radio button.

Sorry I can't be more specific on names and such, I'm not at my Ubuntu box.

Doing this will disable the compiz effects and then you can try to VNC in.

---

### Post by Halkus on 2011-01-31
Well. I'm pleased to confirm that did work. I wasn't sure how to get access to that menu... I have no mouse on the PC in the loft, and as soon as I enable the Nvidia driver Ubuntu enables desktop effects...

I managed it using the keyboard... 

Thanks very much mharrison!

---

### Post by ubername on 2011-01-31
1) Open a terminal or press ALT+F2, then run/type: gconf-editor
2) Go to /desktop/gnome/remote_access and enable "disable_xdamage"

Allows VNC without disabling desktop effects.

[http://ubuntuforums.org/showpost.php?p=9659038&postcount=14](http://ubuntuforums.org/showpost.php?p=9659038&postcount=14)

---

### Post by Halkus on 2011-01-31
Thanks for that - I seem to now have effects enabled and VNC is working. :)

---

### Post by JRV on 2011-01-31
I would try XDMCP or SSH.

With VNC you must be logged in, it's possible but very difficult to log in to VNC through SSH.

For XDMCP:

```

To enable XDMCP server in Ubuntu 9.04 (Jaunty) and before:

   sudo gedit /etc/gdm/gdm.conf.custom

For Ubuntu 9.10 (Karmic) and after: 

   sudo gedit /etc/gdm/custom.conf

Add the following lines:

[xdmcp]
Enable=true
MaxPending=4
MaxSessions=16
MaxWait=15

Then, restart gdm with the command:

   sudo /etc/init.d/gdm restart

or reboot the PC.

Install the XDMCP client called Xephyr with the command:

   sudo apt-get install xserver-xephyr

XDMCP will then be available after login from the command line, use:

 Xephyr :1 -query HOSTNAME -fullscreen -once

Note the capital X.

```

For SSH:

On the server
```


  sudo apt-get install ethtool openssh-server

```
 
Then you need to modifiy the /etc/ssh/ssh_config file on the clients.

Here is mine:

```


# This is the ssh client system-wide configuration file.  See
# ssh_config(5) for more information.  This file provides defaults for
# users, and the values can be changed in per-user configuration files
# or on the command line.

# Configuration data is parsed as follows:
#  1. command line options
#  2. user-specific file
#  3. system-wide file
# Any configuration value is only changed the first time it is set.
# Thus, host-specific definitions should be at the beginning of the
# configuration file, and defaults at the end.

# Site-wide defaults for some commonly used options.  For a comprehensive
# list of available options, their meanings and defaults, please see the
# ssh_config(5) man page.

Host *
#   ForwardAgent no
   ForwardX11 yes
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
  PasswordAuthentication yes
#   HostbasedAuthentication no
#   GSSAPIAuthentication no
#   GSSAPIDelegateCredentials no
#   GSSAPIKeyExchange no
#   GSSAPITrustDNS no
#   BatchMode no
#   CheckHostIP yes
#   AddressFamily any
#   ConnectTimeout 0
#   StrictHostKeyChecking ask
#   IdentityFile ~/.ssh/identity
#   IdentityFile ~/.ssh/id_rsa
#   IdentityFile ~/.ssh/id_dsa
#   Port 22
#   Protocol 2,1
#   Cipher 3des
#   Ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
#   VisualHostKey no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no


```

And modify the /etc/ssh/sshd_config file on the server.

Here is mine:

```


# Package generated configuration file
# See the sshd_config(5) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes

# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768

# Logging
SyslogFacility AUTH
LogLevel INFO

# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes

RSAAuthentication no
PubkeyAuthentication no
#AuthorizedKeysFile	%h/.ssh/authorized_keys

# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes

# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Change to no to disable tunnelled clear text passwords
PasswordAuthentication yes

# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes


```

To connect:

```


ssh -X USER@HOSTNAME


```

From here you can run a program on the server and it will be displayed on the client.

To use files on the server click on Places=>Connect to server=>Service Type is SSH.
This will create an SFTP connection, now bookmark it.

I hope this helps.

---

### Post by Halkus on 2011-01-31
To be entirely honest JRV, I've had Ubuntu installed for about 1 day so far, and my knowledge of Linux configuration is minimal at best... the most I've done is manage a slice through a shell bash account.

However, I'll come back to your suggestions when I get other things sorted and work through them. I think your advice is step by step instructions on a way to replace the default remote access to Ubuntu with something that at least provides an alternative, but also may be more robust.

Thanks very much!

---

### Post by ankspo71 on 2011-01-31
Hi,
I see you can use VNC now, but I'll mention this so you have a backup plan. I like using TeamViewer as an alternative to VNC. I have not tried it on the Gnome desktop though so I can't confirm if it has problems with compiz or not. I have easily used it to and from Windows XP and Linux (Kubuntu and PClinuxOS, both with KDE4 desktops) across my local network though. [http://www.teamviewer.com/](http://www.teamviewer.com/)

---

### Post by Halkus on 2011-02-01
Thanks ankspo71, your alternative seems to be a fair bit easier to comprehend.

However now that I've installed it on both the Windows PC and the Ubuntu server and am able to connect. However, assuming that I have neither access to the Ubuntu desktop to start the program, nor to see what the client ID and password are... - which are the only circumstances I'd use it... How would I get it working so that it'd be there always for me to fall back on, without having to go up into the loft to find information out?

---

### Post by ankspo71 on 2011-02-01
Hi,
Sorry it took a while, I had to go figure it out for myself. Go into the menu of teamviewer: 
Extras > Options > Security
Now set a "permanent password for the unattended access".

Now you will have to get teamviewer to start automatically with the computer that needs to be accessed unattendedly.

Also, if you go back to the Teamviewer download page for Windows, scroll down and you will see a download that says: "For unattended servers: TeamViewer Host" and read the description. I haven't tried that download, so I don't know if it costs money for non commercial use OR if it will work with (or on) a linux server. It might be worth checking out though.

Hope this helps.

PS. The host and client IDs don't ever change as far as I can see. You just need to enter the client ID once and TeamViewer will remember it (unless you clear the history yourself). So if you have a permanent password set on the client, you will only have to physically look at the client GUI once.

---

### Post by Halkus on 2011-02-04
Well, that works! I didn't look at the unattended servers thing. The method you suggested sounded simple. I puzzled over how to get it to start automatically, as the googling I did pointed at preferences>sessions, however I guess that's now changed and I've added it to startup successfully!

Thank you very much indeed.

---

