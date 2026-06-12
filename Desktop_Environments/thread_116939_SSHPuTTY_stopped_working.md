---
title: "SSH/PuTTY stopped working"
date: 2006-01-13
forum: Desktop Environments
---

### Post by %hMa@?b&lt;C on 2006-01-13
Just yesterday, I got PuTTY and Ssh working, i was ssh'ing to and from my computer.  I tryed to SSH my cousin, and then it didnt work.  I restarted at night, and now it wont work.
Here is cmd output. 
```


crowell@ubuntu:~$ ssh localhost
ssh: connect to host localhost port 22: Connection timed out



```
I dont get anything after that.

---

### Post by Mr_Grieves on 2006-01-13
Do this and paste output here:

```

ps -ef | grep ssh

sudo iptables -L | grep -i ssh
sudo iptables -L | grep -i 22

ping localhost

```

---

### Post by %hMa@?b&lt;C on 2006-01-13
```
crowell@ubuntu:~$ ps -ef | grep ssh
root      8318     1  0 09:42 ?        00:00:00 /usr/sbin/sshd
crowell   8507  8465  0 09:42 ?        00:00:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
crowell   9795  9785  0 16:56 pts/1    00:00:00 grep ssh
crowell@ubuntu:~$
crowell@ubuntu:~$ sudo iptables -L | grep -i ssh
crowell@ubuntu:~$ sudo iptables -L | grep -i 22
crowell@ubuntu:~$
crowell@ubuntu:~$ ping localhost
PING localhost.localdomain (127.0.0.1) 56(84) bytes of data.

--- localhost.localdomain ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 2998ms

crowell@ubuntu:~$

```
the localhost.localdomain timed out

---

### Post by Mr_Grieves on 2006-01-13
Very weird..

Very strange.

Try this and paste output. It displays any firewall rules in your system and some rules about who can access services on you're system.
```

sudo iptables -L
cat /etc/hosts.allow
cat /etc/hosts.deny

and
sudo killall ssh
then
ssh localhost

```

---

### Post by %hMa@?b&lt;C on 2006-01-13
```
crowell@ubuntu:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
TCPMSS     tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN tcpmss match 1400:1536 TCPMSS clamp to PMTU

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
crowell@ubuntu:~$ cat /etc/hosts.allow
# /etc/hosts.allow: list of hosts that are allowed to access the system.
#                   See the manual pages hosts_access(5), hosts_options(5)
#                   and /usr/doc/netbase/portmapper.txt.gz
#
# Example:    ALL: LOCAL @some_netgroup
#             ALL: .foobar.edu EXCEPT terminalserver.foobar.edu
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper, as well as for
# rpc.mountd (the NFS mount daemon). See portmap(8), rpc.mountd(8) and
# /usr/share/doc/portmap/portmapper.txt.gz for further information.
#
crowell@ubuntu:~$ cat /etc/hosts.deny
# /etc/hosts.deny: list of hosts that are _not_ allowed to access the system.
#                  See the manual pages hosts_access(5), hosts_options(5)
#                  and /usr/doc/netbase/portmapper.txt.gz
#
# Example:    ALL: some.host.name, .some.domain
#             ALL EXCEPT in.fingerd: other.host.name, .other.domain
#
# If you're going to protect the portmapper use the name "portmap" for the
# daemon name. Remember that you can only use the keyword "ALL" and IP
# addresses (NOT host or domain names) for the portmapper. See portmap(8)
# and /usr/doc/portmap/portmapper.txt.gz for further information.
#
# The PARANOID wildcard matches any host whose name does not match its
# address.

# You may wish to enable this to ensure any programs that don't
# validate looked up hostnames still leave understandable logs. In past
# versions of Debian this has been the default.
# ALL: PARANOID
crowell@ubuntu:~$

```

```
crowell@ubuntu:~$ sudo killall ssh
ssh: no process killed
crowell@ubuntu:~$ ssh localhost


```
it times out then

---

### Post by Mr_Grieves on 2006-01-13
If you don't mind I'd like you to flush you're iptables rules. To make sure they are not disturbing things. You seem to have some kind strange rule defined..

```

sudo iptables -F FORWARD
sudo iptables -F ALL

then
ping localhost
ssh localhost

```

A side note is that you oughto get some kinda firewall up and running. There is a package called firestarter that you may use.
But that is a later issue. You should also use the /etc/hosts.allow file to restrict usage to the ssh daemon.

---

### Post by %hMa@?b&lt;C on 2006-01-13
```

crowell@ubuntu:~$ sudo iptables -F FORWARD
crowell@ubuntu:~$ sudo iptables -F ALL
iptables: No chain/target/match by that name
crowell@ubuntu:~$


```
ok

---

### Post by Mr_Grieves on 2006-01-13
Things working now?

---

### Post by %hMa@?b&lt;C on 2006-01-13
still not working.  I believe that this might have something to do with localhost:631, because i cant contact cups server too.

---

### Post by Mr_Grieves on 2006-01-13
Check this out.. it will list the things that are listening on ports on your system

```

netstat -a | grep LISTEN

```

It checks so that the servers is really listening to the correct port..
I can't imagine what could be blocking all communication to you're box.. you should be able to atleast ping the localhost address..........

Have you done any special things before it stopped working?
What does this file say?

```

cat /etc/sysctl.conf

```

---

### Post by %hMa@?b&lt;C on 2006-01-13
```
crowell@ubuntu:~$ netstat -a | grep LISTEN
tcp        0      0 localhost.localdo:32770 *:*                     LISTEN
tcp        0      0 localhost.localdoma:ipp *:*                     LISTEN
tcp6       0      0 *:ssh                   *:*                     LISTEN
unix  2      [ ACC ]     STREAM     LISTENING     32807    /tmp/alsa-dmix-8518-1137191064-216408
unix  2      [ ACC ]     STREAM     LISTENING     11246    @/tmp/dbus-guq7zCMWjeunix  2      [ ACC ]     STREAM     LISTENING     10341    /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     11241    /tmp/ssh-OpkvVU8465/agent.8465
unix  2      [ ACC ]     STREAM     LISTENING     11265    /tmp/orbit-crowell/linc-2141-0-57cdaff9e3521
unix  2      [ ACC ]     STREAM     LISTENING     11275    /tmp/orbit-crowell/linc-2111-0-338ebaf2c6c2
unix  2      [ ACC ]     STREAM     LISTENING     11442    /tmp/.ICE-unix/8465
unix  2      [ ACC ]     STREAM     LISTENING     11451    /tmp/keyring-f1e920/socket
unix  2      [ ACC ]     STREAM     LISTENING     11467    /tmp/.esd-1000/socketunix  2      [ ACC ]     STREAM     LISTENING     11486    /tmp/orbit-crowell/linc-214a-0-726de82ee24b1
unix  2      [ ACC ]     STREAM     LISTENING     11508    /tmp/orbit-crowell/linc-214c-0-399df479517d9
unix  2      [ ACC ]     STREAM     LISTENING     11758    /tmp/orbit-crowell/linc-21d7-0-e6b00cef1be9
unix  2      [ ACC ]     STREAM     LISTENING     11785    /tmp/orbit-crowell/linc-21dc-0-29c0ab551c0fa
unix  2      [ ACC ]     STREAM     LISTENING     11805    /tmp/orbit-crowell/linc-21e0-0-29c0ab55672ef
unix  2      [ ACC ]     STREAM     LISTENING     11894    /tmp/orbit-crowell/linc-21de-0-14b77d00941f1
unix  2      [ ACC ]     STREAM     LISTENING     11940    /tmp/orbit-crowell/linc-21f3-0-14b77d01826d
unix  2      [ ACC ]     STREAM     LISTENING     11963    /tmp/orbit-crowell/linc-21ef-0-5e7ec6192fa8
unix  2      [ ACC ]     STREAM     LISTENING     12050    /tmp/orbit-crowell/linc-2203-0-7ae46727a201e
unix  2      [ ACC ]     STREAM     LISTENING     12075    /tmp/orbit-crowell/linc-2208-0-62a3ea50d321
unix  2      [ ACC ]     STREAM     LISTENING     12161    /tmp/orbit-crowell/linc-221b-0-5b6fc1f76ef50
unix  2      [ ACC ]     STREAM     LISTENING     12184    /tmp/orbit-crowell/linc-221d-0-452aac895d760
unix  2      [ ACC ]     STREAM     LISTENING     10946    /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     12228    /tmp/orbit-crowell/linc-2219-0-77d01777a3eb8
unix  2      [ ACC ]     STREAM     LISTENING     16724    /tmp/orbit-crowell/linc-25a9-0-7ae99ba7196f4
unix  2      [ ACC ]     STREAM     LISTENING     16787    /tmp/orbit-crowell/linc-25b3-0-62c9670d62887
unix  2      [ ACC ]     STREAM     LISTENING     11661    @/tmp/fam-crowell-
unix  2      [ ACC ]     STREAM     LISTENING     10121    /tmp/.gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     8609     @/tmp/hald-local/dbus-86w7O6H3pW
unix  2      [ ACC ]     STREAM     LISTENING     12130    /tmp/mapping-crowell
unix  2      [ ACC ]     STREAM     LISTENING     8593     /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     8519     /var/run/acpid.socketcrowell@ubuntu:~$

```

---

### Post by Mr_Grieves on 2006-01-13
It seems like you're ssh server is listening for IPv6..

Do this:

```

cat /etc/ssh/sshd_config

```
and paste output here..

---

### Post by %hMa@?b&lt;C on 2006-01-13
```
crowell@ubuntu:~$ cat /etc/ssh/sshd_config
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
PermitRootLogin yes
StrictModes yes

RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile     %h/.ssh/authorized_keys

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
#PasswordAuthentication yes


# To change Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#AFSTokenPassing no
#KerberosTicketCleanup no

# Kerberos TGT Passing does only work with the AFS kaserver
#KerberosTgtPassing yes

X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
KeepAlive yes
#UseLogin no

#MaxStartups 10:30:60
#Banner /etc/issue.net

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

Subsystem sftp /usr/lib/openssh/sftp-server

UsePAM yes
crowell@ubuntu:~$

```

---

### Post by Mr_Grieves on 2006-01-13
Hm. Try changing

```

---snip----
UsePAM yes
---snip----

to
---snip----
UsePAM no
---snip----

then

sudo killall ssh

then
ssh localhost

If no success try changing

---snip----
#ListenAddress 0.0.0.0
---snip----

to

---snip----
ListenAddress 127.0.0.1
---snip----

and then

sudo killall ssh

and

ssh localhost

```

---

### Post by Mr_Grieves on 2006-01-13
After this run

```

sudo lsof | grep ssh

```
to check that the ssh daemon is listening..

If the changes did not work, change back to the orgininal configuration to prevent us creating more problems than you allready have.
Don't forget to restart the daemon to make the changes take place, eg: sudo killall ssh

---

### Post by %hMa@?b&lt;C on 2006-01-14
still no success

---

