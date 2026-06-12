---
title: "apt-get errors after upgrade"
date: 2005-04-12
forum: Desktop Environments
---

### Post by mattack on 2005-04-12
I'm having trouble after upgrading from warty to hoary.
when ever I try to install something (either with apt-get or synaptic) I get the following errors:

```
matt@mattack:~ $ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  x-window-system-core
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
8 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up postfix (2.1.5-9ubuntu3) ...

Postfix configuration was untouched.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Starting Postfix Mail Transport Agent...
 *stfix/postfix-script: fatal: the Postfix mail system is already running[fail]
invoke-rc.d: initscript postfix, action "start" failed.
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of at:
 at depends on mail-transport-agent; however:
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing at (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mailx:
 mailx depends on exim4 | mail-transport-agent; however:
  Package exim4 is not installed.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mutt:
 mutt depends on exim4 | mail-transport-agent; however:
  Package exim4 is not installed.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mutt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of anacron:
 anacron depends on exim4 | mail-transport-agent; however:
  Package exim4 is not installed.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing anacron (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of postfix-tls:
 postfix-tls depends on postfix; however:
  Package postfix is not configured yet.
 postfix-tls depends on postfix (= 2.1.5-9ubuntu3); however:
  Package postfix is not configured yet.
dpkg: error processing postfix-tls (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-base:
 ubuntu-base depends on at; however:
  Package at is not configured yet.
 ubuntu-base depends on mailx; however:
  Package mailx is not configured yet.
 ubuntu-base depends on mutt; however:
  Package mutt is not configured yet.
 ubuntu-base depends on postfix; however:
  Package postfix is not configured yet.
 ubuntu-base depends on postfix-tls; however:
  Package postfix-tls is not configured yet.
dpkg: error processing ubuntu-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb:
 lsb depends on exim4 | mail-transport-agent; however:
  Package exim4 is not installed.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
 lsb depends on at; however:
  Package at is not configured yet.
dpkg: error processing lsb (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postfix
 at
 mailx
 mutt
 anacron
 postfix-tls
 ubuntu-base
 lsb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Here is my /etc/postfix/main.cf file, if that helps:
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version

# For better performance, chattr -S -R /var/spool/postfix, and use a
# journaled filesystem to achieve the same results as chattr +S gives.

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# Uncomment the next line to use procmail for delivery
#mailbox_command = procmail -a "$EXTENSION"


myhostname = mattack
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = mattack, localhost.localdomain, localhost
relayhost = 
mynetworks = 127.0.0.0/8
mailbox_command = 
mailbox_size_limit = 0
recipient_delimiter = +

```

I checked the Update Manager just to see if everything is current, it says my system is up to date except that x-window-system-core is not upgraded, and to run sudo apt-get dist-upgrade to fix it.
Well, I get the errors as posted above...
I tried re-installing the packages but that didn't work. I'm not sure what to do...
Any one have any ideas?

---

### Post by lao_V on 2005-04-13
I had similar problem few weeks back. dpkg-reconfigure postfix solved the issue for me i think

---

### Post by mattack on 2005-04-13
I fixed this by installing the missing package called exim4. Everything else fell back into place. I had to reconfigure xorg and now my resolution is all messed up, but I'm working on that.

---

