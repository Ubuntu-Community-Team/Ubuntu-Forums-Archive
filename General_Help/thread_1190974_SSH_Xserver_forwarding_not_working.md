---
title: "SSH Xserver forwarding not working"
date: 2009-06-18
forum: General Help
---

### Post by abyrne on 2009-06-18
Hey,

   I'm having a couple problems with SSH. When I use
```
ssh -X [ipaddress]
```
or
```
ssh -Y [ipaddress]
```
I can still get to the remote shell, but when I try to start an X app (say, thunar) I get
```
X11 connection rejected because of wrong authentication.
Thunar: Cannot open display: 
```
I do a lot of work over SSH, so I find Xserver forwarding very useful. So, any help would be great!
:KS

---

### Post by t4thfavor on 2009-06-18
I have to open /etc/ssh/ssh_config and change the lines

Host *
#   ForwardAgent no
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no

To

Host *
#   ForwardAgent no
   ForwardX11 yes
   ForwardX11Trusted yes
#   RhostsRSAAuthentication no

I have it working on a bunch of my machines. 


I believe you only need to do it on the client as the server already has this setting (not sure)

---

### Post by abyrne on 2009-06-19
Thanks. But it still didn't  work. I even enabled the setting on the server.

---

### Post by tgalati4 on 2009-06-19
ssh -2 -Y user@host

---

### Post by abyrne on 2009-06-19
Again, thanks. But it still didn't work.
Out of curiosity, what does the -2 switch mean.

Oh, and by the way, when I log in remotely I get this
```
Linux byrne-server 2.6.27-14-generic #1 SMP Wed Apr 15 18:59:16 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
Last login: Fri Jun 19 11:02:58 2009 from 192.168.1.2
**[COLOR="Red"]/usr/bin/X11/xauth:  error in locking authority file /home/anthony/.Xauthority[/COLOR]**
```
(The /usr/bin.... part isn't really in bold and red, I just highlighted it)

You think there's a problem there?

---

### Post by tgalati4 on 2009-06-19
Check permissions of your .Xauthority file.  It should look something like:

-rw-------  1 tgalati4 tgalati4      171 2009-06-19 08:14 .Xauthority

If not then fix it with:

sudo chmod 600 .Xauthority

According to:

man ssh

-2 forces type 2 authentication protocol.  It may or may not be needed in your case.

It works out-of-the-box between a gutsy machine logging into an intrepid machine with no configuration changes needed.  (Both are running Linux Mint, so there may be some configuration changes from stock Ubuntu.)

If none of that works, try deleting .Xauthority.  It gets created with each new session.

My ssh_config file from Intrepid without any changes:

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
#   ForwardX11 no
#   ForwardX11Trusted yes
#   RhostsRSAAuthentication no
#   RSAAuthentication yes
#   PasswordAuthentication yes
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
#   Ciphers aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour,aes192-cbc,aes256-cbc
#   MACs hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160
#   EscapeChar ~
#   Tunnel no
#   TunnelDevice any:any
#   PermitLocalCommand no
    SendEnv LANG LC_*
    HashKnownHosts yes
    GSSAPIAuthentication yes
    GSSAPIDelegateCredentials no

```

I would change the config files back to default (on both machines) and see if it works.  You need the same user account on both machines as well.

---

