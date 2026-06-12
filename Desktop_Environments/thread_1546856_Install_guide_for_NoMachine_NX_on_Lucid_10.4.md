---
title: "Install guide for NoMachine NX on Lucid 10.4"
date: 2010-08-06
forum: Desktop Environments
---

### Post by raysolomon on 2010-08-06
Hi folks, I am posting a quick guide for installing NoMachine NX client/node/server because I found a lot of past threads where many people were confused how to do this. Hopefully this thread will help.

I needed to setup a remote desktop software for my office computer and after searching around I found NoMachine NX to have the most features, very secure and good documentation.
My system is a new install of Ubuntu 10.4 Lucid 64-bit.

I am using the latest versions of the NX client, node and server as of August 5, 2010

***[COLOR="Red"]Note: Before you begin, you must install ssh and openssh-server[/COLOR]***
sudo apt-get install ssh openssh-server

**1) Edit the sshd_config file and replace it with the one below**
sudo nano /etc/ssh/sshd_config

*(Note: Make sure to add your username in the **AllowUsers** variable, but make sure nx is still there)*

```
# Package generated configuration file
# See the sshd(8) manpage for details

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
PermitRootLogin no
AllowUsers nx myusername
StrictModes no

RSAAuthentication yes
PubkeyAuthentication yes
AuthorizedKeysFile /usr/NX/home/nx/.ssh/authorized_keys2
#AuthorizedKeysFile %h/.ssh/authorized_keys

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
ChallengeResponseAuthentication yes

# Change to no to disable tunnelled clear text passwords
#PasswordAuthentication yes
PasswordAuthentication no

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

UsePAM yes
```

**2) Install the client, node and server packages (in that particular order)**
[http://www.nomachine.com/download-client-linux.php](http://www.nomachine.com/download-client-linux.php)
[http://www.nomachine.com/select-package.php?os=linux&id=1](http://www.nomachine.com/select-package.php?os=linux&id=1)

**3) Edit the server config file and enable the following**
sudo nano /usr/NX/etc/server.cfg

```
EnableNodeMonitoring = "1"
SSHDPort = "22"
EnableUnencryptedSession = "0"
SSHDAuthPort = "22"
EnableStatistics = "1"
```


**4) Edit the node config file and enable the following**
sudo nano /usr/NX/etc/node.cfg

```
EnableUnencryptedSession = "0"
SSHAuthorizedKeys = "authorized_keys2"
SSHDPort = "22"
NodeLoginGreeting = "Welcome to your NX session"
```


**5) Execute the installer script**
sudo /usr/NX/scripts/setup/nxserver --install debian

**6) Generate DSA key**
sudo /usr/NX/scripts/setup/nxserver --keygen

**7) Change ownership and permissions to this file**
sudo chown nx:root /usr/NX/home/nx/.ssh/authorized_keys2
sudo chmod 0644 /usr/NX/home/nx/.ssh/authorized_keys2

**8) Change ownership and permissions to this file**
sudo chown nx:root /usr/NX/home/nx/.ssh/default.id_dsa.pub
sudo chmod 0644 /usr/NX/home/nx/.ssh/default.id_dsa.pub

**9) Restart SSHD**
sudo /etc/init.d/ssh restart

**10) Restart nxserver**
sudo /etc/init.d/nxserver restart


Run the following command and copy this DSA key so you can configure your NX Client to use it.
sudo nano /usr/NX/share/keys/default.id_dsa.key

1) Go to Applications->Internet->NX Client for Linux->NX Client for Linux
2) Click the configure button
3) Host: localhost
4) Port: 22
5) Click the Key button and replace the existing DSA key with the key you copied earlier from /usr/NX/share/keys/default.id_dsa.key and press the Save button.
6) Select gnome from the Desktop options if that is correct
7) Finally click Save and OK

Now you can try to connect from your computer to see if it is working.
If so, try to connect from a different computer on your LAN to see if that is working.

If its working locally on your computer, but not remotely from another machine on your LAN, then its probably a firewall issue. I'm not going to explain firewall or router issues because that can be easily figured out from other threads in this forum.


**Basic commands for the NX server**
List users:
sudo /usr/NX/bin/nxserver --list

Start, restart or stop the NX server:
sudo /etc/init.d/nxserver start
sudo /etc/init.d/nxserver restart
sudo /etc/init.d/nxserver stop

**Administration guide:**
[http://www.nomachine.com/documents/html/admin-guide.html](http://www.nomachine.com/documents/html/admin-guide.html)

That's it.

---

### Post by erich2k8 on 2010-10-03
Hi,

Great guide!

Just wanted to add one tip. If you already have open ssh set up for normal ssh authentication, you might not want to hardcode the NX authorized keys file in sshd_config. You can add a sym link to map the keys file that NX expects to a pattern that matches your existing config. The nx user's home dir is typically "/usr/NX/home/nx"

So, for instance, if you are using the default:
```
AuthorizedKeysFile %h/.ssh/authorized_keys
```You can set a link like the following for the nx user
```
sudo ln -s /usr/NX/home/nx/.ssh/authorized_keys2 /usr/NX/home/nx/.ssh/authorized_keys
```
This points to the correct file for nx logins, and still allows you to use ~/.ssh/authorized_keys for normal ssh auth.

---

### Post by J&#7885;hn on 2010-11-29
Apologies for resurrecting an old thread, but I was wondering if anyone had experience of moving a custom nx key from server a to server b?

This would allow all our machines to be accessed via one client key, and would be very useful.

---

### Post by Loan_Refi on 2010-12-02
Do any of you have File Share enabled and working? 

I can't get it to work. I want to mount NXShare folder to my NXServer.

This is the error I get;

Cannot mount share 'NXShare'
Error: cannot mount share//SL410(mycomputername)/user/, missing command /bin/mount.cifs in /usr/bin:/bin:/usr/local/bin. Cannot use NX smb privilegd script to mount shares.

Does anyone know what could be wrong her?

I'm able to share my printer and can connect just fine but Folder Sharing is just not working for me.

Thanks in advance!

---

### Post by pricetech on 2010-12-02
Been using NX for some time.  Piece of cake to set up and use.

I will add this though;  back up any files prior to editing them just for safety's sake.

---

### Post by horstkotte on 2011-08-17
Awesome thread. For whatever reason I hosed my nomachine or ssh setup and was not able to connect anymore. This procedure worked great after removing openssh-server, openssh-client, ssh and all nomachine artifacts (/usr/NX/*). Thanks!

---

### Post by MrDetermination on 2011-08-21
Thanks for the thread.  Using this method I am still able to log in via SSH with no key (password only) even when 

"PasswordAuthentication no" in /etc/ssh/sshd_config

Is there a way to set up NoMachine NX and still have keys be required for SSH auth?

---

### Post by ccfisch on 2013-05-04
I came to this thread via google searching ... so apologies if I'm posting in a stale location. 

In any case, in addition to the suggestion of symbolic linking authorized_keys2 to authorized_keys, to get NX 3.5 working you need to add the nx user to the groups allowed to log in via ssh. In my case sshd_config contained the line

```
AllowGroups sshlogin
```

so I added nx to this group

```
sudo usermod -a -G sshlogin nx
```

---

### Post by oldos2er on 2013-05-04
Old thread closed.

---

