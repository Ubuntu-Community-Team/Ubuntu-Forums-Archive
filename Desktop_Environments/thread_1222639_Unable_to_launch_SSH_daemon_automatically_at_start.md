---
title: "Unable to launch SSH daemon automatically at start-up"
date: 2009-07-25
forum: Desktop Environments
---

### Post by emma_peel on 2009-07-25
Hello Ubuntu forum.

It is my first post on this forum, so if they are some specific rules or requirement, do not hesitate to explain.

I have installed Kubuntu for desktop on my laptop a couple of days ago and feel quite satisfied. Moreover, I really impressed by the Ubuntu documentation, which is very extensive, detailed and easy-to-read.

I am now facing a small issue. I want to have the daemon SSH automatically started up on boot. So I have done a classical :

```
sudo update-rc.d ssh defaults
```

I tried with another priority :

```
sudo update-rc.d -f ssh remove
sudo update-rc.d ssh start 50 2 3 4 5 . stop 50 0 1 6 .
```

Everything looks OK :

```
arnaud@KubuntuBox:~$ ls /etc/rc*
/etc/rc.local

/etc/rc0.d:
K01kdm               K74bluetooth                        S31umountnfs.sh
K02usplash           K99laptop-mode                      S35networking
K20apport            README                              S40umountfs
K25hwclock.sh        S01linux-restricted-modules-common  S60umountroot
K50alsa-utils        S15wpa-ifupdown                     S90halt
K50ssh               S20sendsigs
K63mountoverflowtmp  S30urandom

/etc/rc1.d:
K01kdm      K20acpi-support  K21apmd          K88dbus         S30killprocs
K02usplash  K20apport        K39ufw           K89klogd        S70bootlogs.sh
K11anacron  K20hotkey-setup  K50ssh           K90sysklogd     S70dns-clean
K11atd      K20rsync         K74bluetooth     K99laptop-mode  S70pppd-dns
K11cron     K20saned         K80cups          K99policykit    S90single
K16hal      K21acpid         K86avahi-daemon  README

/etc/rc2.d:
README        S20hotkey-setup    S50saned        S98usplash
S01policykit  S24hal             S50ssh          S99acpi-support
S10acpid      S25bluetooth       S70bootlogs.sh  S99laptop-mode
S10apmd       S30kdm             S70dns-clean    S99ondemand
S10sysklogd   S50avahi-daemon    S70pppd-dns     S99rc.local
S11klogd      S50cups            S89anacron      S99rmnologin
S12dbus       S50NetworkManager  S89atd          S99stop-readahead
S20apport     S50rsync           S89cron

/etc/rc3.d:
README        S20hotkey-setup    S50saned        S98usplash
S01policykit  S24hal             S50ssh          S99acpi-support
S10acpid      S25bluetooth       S70bootlogs.sh  S99laptop-mode
S10apmd       S30kdm             S70dns-clean    S99ondemand
S10sysklogd   S50avahi-daemon    S70pppd-dns     S99rc.local
S11klogd      S50cups            S89anacron      S99rmnologin
S12dbus       S50NetworkManager  S89atd          S99stop-readahead
S20apport     S50rsync           S89cron

/etc/rc4.d:
README        S20hotkey-setup    S50saned        S98usplash
S01policykit  S24hal             S50ssh          S99acpi-support
S10acpid      S25bluetooth       S70bootlogs.sh  S99laptop-mode
S10apmd       S30kdm             S70dns-clean    S99ondemand
S10sysklogd   S50avahi-daemon    S70pppd-dns     S99rc.local
S11klogd      S50cups            S89anacron      S99rmnologin
S12dbus       S50NetworkManager  S89atd          S99stop-readahead
S20apport     S50rsync           S89cron

/etc/rc5.d:
README        S20hotkey-setup    S50saned        S98usplash
S01policykit  S24hal             S50ssh          S99acpi-support
S10acpid      S25bluetooth       S70bootlogs.sh  S99laptop-mode
S10apmd       S30kdm             S70dns-clean    S99ondemand
S10sysklogd   S50avahi-daemon    S70pppd-dns     S99rc.local
S11klogd      S50cups            S89anacron      S99rmnologin
S12dbus       S50NetworkManager  S89atd          S99stop-readahead
S20apport     S50rsync           S89cron

/etc/rc6.d:
K01kdm               K74bluetooth                        S31umountnfs.sh
K02usplash           K99laptop-mode                      S35networking
K20apport            README                              S40umountfs
K25hwclock.sh        S01linux-restricted-modules-common  S60umountroot
K50alsa-utils        S15wpa-ifupdown                     S90reboot
K50ssh               S20sendsigs
K63mountoverflowtmp  S30urandom

/etc/rcS.d:
README                              S35mountall.sh
S01mountkernfs.sh                   S36mountall-bootclean.sh
S01readahead                        S37apparmor
S02hostname.sh                      S37mountoverflowtmp
S06keyboard-setup                   S37udev-finish
S07linux-restricted-modules-common  S39readahead-desktop
S10udev                             S39ufw
S11mountdevsubfs.sh                 S40networking
S13pcmciautils                      S45mountnfs.sh
S15module-init-tools                S46mountnfs-bootclean.sh
S17procps                           S49console-setup
S20checkroot.sh                     S55bootmisc.sh
S22mtab.sh                          S55urandom
S25brltty                           S70screen-cleanup
S30checkfs.sh                       S70x11-common
```

Please note the the conf file is OK. When manually started up, I can connect to my laptop without any problem

I suspect some dependencies or something like that.

Any idea will help.

Thank you in advance for your support !

---

### Post by hrod beraht on 2009-07-25
> **emma_peel said:**
> I want to have the daemon SSH automatically started up on boot.

Assuming you have installed **openssh-server**, it will start from */etc/init.d/ssh*. If the server has been installed and the /etc/init.d/ssh file exists but doesn't seem to work, I'd execute a **dpkg-reconfigure openssh-server**.

Bob

---

### Post by emma_peel on 2009-07-25
Hello Hrod & thank you for the reply.

I fact the SSH daemon is working fine. I have configured I used to. When launch manually, I can connect to it without any problems. :D

I just want to have it automatically started on boot.

---

### Post by emma_peel on 2009-07-29
Hello.

A little UP for this thread.

I tried the reconfigure dpkg switch, without success.

Just in cas, I have installed the apache2 package. The daemon is properly launched, everything works fine for it.

I have tried a couple of priority level, including the one used by apache2 ... still no result.

This is probably something stupid that will look obvious afterwards, but I'm currently stuck ... any idea would be appreciated.

---

### Post by emma_peel on 2009-07-29
I found something that may be interesting :

```
arnaud@KubuntuBox:/$ grep sshd /var/log/auth.log
Jul 29 22:55:17 KubuntuBox sshd[3046]: error: Bind to port 22 on 192.168.1.101 failed: Cannot assign requested address.
Jul 29 22:55:17 KubuntuBox sshd[3046]: fatal: Cannot bind any address.
Jul 29 22:57:22 KubuntuBox sshd[3550]: Server listening on 192.168.1.101 port 22.
Jul 29 22:58:22 KubuntuBox sshd[3554]: Accepted publickey for arnaud from 192.168.1.204 port 50423 ssh2
Jul 29 22:58:23 KubuntuBox sshd[3554]: pam_unix(sshd:session): session opened for user arnaud by (uid=0)
```

It looks like there are errors during sshd start up. But how to correct them ?

---

### Post by emma_peel on 2009-07-30
I finally resolve the issue by commenting the listen adresse param :

```
arnaud@KubuntuBox:/etc/ssh$ cat sshd_config
# Quick config file
# Copied from virologie.free.fr
Port                     22
Protocol                 2
#ListenAddress            192.168.1.101
ServerKeyBits            1024
PermitRootLogin          no

PubkeyAuthentication     yes
IgnoreRhosts             yes
AuthorizedKeysFile       .ssh/authorized_keys
PasswordAuthentication   no

UsePAM                   yes
Compression              yes
```

And ... it works !

---

### Post by xfile087 on 2009-08-26
> **emma_peel said:**
> I finally resolve the issue by commenting the listen adresse param :

!

Ah brilliant. I'm just getting to grips with ssh now and like you it wouldn't launch on boot but now I've found your post and disabled the listen address param it works perfectly so thanks for posting the answer, it's greatly appreaciated. :D

---

### Post by VipX1 on 2009-12-15
[SIZE=2][COLOR=Blue]Finally, a solution to this! Thanks for posting.[/COLOR][/SIZE]
This does work. 
This error caused me great irritation. 

The commenting of the ListenAddress entry causes the OpenBSD sshd service to restart 3 times at boot. This can be seen on the local vga screen attached to the server.
When I try to log into sshd immediately after reboot from a client the service is unavailable and my connection attempt gets "No Route to Host" error. The after 1 minute I can connect.
If I look at the local server screen I can then see that sshd was restarting and did so 3 times.

If sshd is run in Debug mode with out the comment on the ListenAddress line the error is "cannot bind" in /var/log/messages
I think the network interface has not yet recieved it's i.p. address from the dhcp server and the sshd service cannot bind to the configured i.p. set in the ListenAddress directive in sshd_config. Without the directive it reboots until it has an address.
I tried a wild card 
[*] instead of commenting out but it was considered 'garbage'...

---

### Post by orls on 2010-02-14
Sorry to resurrect an old thread (esp. on my first post!) but I was struggling with this and wanted to add my solution for the benefit of future searchers.

To restate the problem:

SSH was not starting correctly on system startup after a pretty standard install. The ssh daemon was running (ps -ef|grep ssh), but I couldn't get in from a remote client. Once logging in on the server, issuing sudo /etc/init.d/shh restart on the box correctly restarted it, and I could access it remotely. Obviously this is no good for a headless machine, having to login at the physical box every restart.

Problem, as identified above, is that SSH wasn't binding to the ListenAddress in its config, because network has not been fully initialized/got its IP from DCHP when sshd starts up. The solution above (remove listenaddress from config) seems to work, but that might limit what you can do with SSH - as I understand it, you need ListenAddress to correctly set up remote access over public internet. (according to [this]("http://forums.linuxmint.com/viewtopic.php?f=42&t=13695") at least)

So if you want ListenAddress instructions in your config and also want it to start correctly  at startup, you need to do the following workaround, found [here]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/241796"). The way this works is that every time NetworkManager changes address it will try and restart SSH. Not the pretties workaround, but it does the job.

$ su
Password:
# cd /etc/NetworkManager/dispatcher.d/
# echo /etc/init.d/ssh restart > ./10ssh
# chmod 755 ./10ssh

Hope that helps someone!

---

### Post by emma_peel on 2010-02-15
That looks a very clean solution and even far better. That may allow to launch SSH when connected to the wired network, and stop when connected by wifi.

I guess that a fixed IP should also work, but do not wanna try on my headless server.

Thank you for sharing your experience.

---

### Post by Du, Wei on 2010-07-06
Hello everyone.
 
I installed Ubuntu 9.10 desktop i386 for testing a few days ago.
 
Unfortunately, I encountered the same problem with this thread:
 
Unable to launch sshd automatically at the system startup.
 
Here is My /etc/ssh/sshd_config:

[Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2

HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key

UsePrivilegeSeparation yes

KeyRegenerationInterval 3600
ServerKeyBits 768

SyslogFacility AUTH
LogLevel INFO

LoginGraceTime 120
PermitRootLogin yes
StrictModes yes
RSAAuthentication yes
PubkeyAuthentication yes

IgnoreRhosts yes

RhostsRSAAuthentication no

HostbasedAuthentication no

PermitEmptyPasswords no

ChallengeResponseAuthentication no]
 
Most of the commented line has been removed except "ListenAddress" which is involved this issue directly.
 
This file is definitely the raw file which was installed by:
 
#apt-get install openssh-server
 
This host has a static IP address 128.224.163.52, which means static IP address doesn't work for this problem.
 
and obviously commenting the "ListenAddress" item doesn't work either.
 
Due to NIS configuration, the NetworkManager has been remove from this system, so that doesn't help too.
 
Following is the log information after reboot:
 
# grep ssh /var/log/auth.log
 
Jul  6 14:41:17 pek-vxhig-lx1 sshd[3657]: error: Bind to port 22 on 0.0.0.0 failed: Permission denied.
Jul  6 14:41:17 pek-vxhig-lx1 sshd[3657]: error: Bind to port 22 on :: failed: Permission denied.
Jul  6 14:41:17 pek-vxhig-lx1 sshd[3657]: fatal: Cannot bind any address.

and after restart manually, I get this:
 
# /etc/init.d/ssh restart
 
# grep ssh /var/log/auth.log
 
Jul  6 14:41:59 pek-vxhig-lx1 sshd[3685]: Server listening on 0.0.0.0 port 22.
Jul  6 14:41:59 pek-vxhig-lx1 sshd[3685]: Server listening on :: port 22.
Jul  6 14:58:24 pek-vxhig-lx1 sudo:   target : TTY=pts/1 ; PWD=/tftpboot ; USER=root ; COMMAND=/etc/init.d/ssh restart
Jul  6 14:58:24 pek-vxhig-lx1 sshd[2857]: Server listening on 0.0.0.0 port 22.
Jul  6 14:58:24 pek-vxhig-lx1 sshd[2857]: Server listening on :: port 22.
Jul  6 15:09:38 pek-vxhig-lx1 sshd[2930]: Accepted password for root from 128.224.162.164 port 3831 ssh2

I tried almost all I can, please help.

---

### Post by Pstevens on 2010-11-26
Did you ever get a reply?  I have the same situation.

---

### Post by emma_peel on 2010-11-27
Did you try the configuration file from the message #6 ?

---

### Post by Walter Jnr on 2013-02-23
> **emma_peel said:**
> I finally resolve the issue by commenting the listen adresse param :

```
arnaud@KubuntuBox:/etc/ssh$ cat sshd_config
# Quick config file
# Copied from virologie.free.fr
Port                     22
Protocol                 2
#ListenAddress            192.168.1.101

```And ... it works !

I did the same the other night and it is now working perfectly. Thanks for the tip.):P

---

### Post by oldos2er on 2013-02-23
Old thread closed.

---

