---
title: "Join desktop to AD domain - username includes domain name"
date: 2019-04-16
forum: Desktop Environments
---

### Post by dbcrvl on 2019-04-16
Hi,

I need to join some Ubuntu 18.04 desktop machines to the company's AD domain.

I use these commands to do so:

```
sudo apt update && apt upgrade -y
sudo apt install -y ssh vim realmd sssd sssd-tools libnss-sss libpam-sss adcli samba-common-bin openssh-server chromium-browser browser-plugin-freshplayer-pepperflash

sudo DEBIAN_FRONTEND=noninteractive apt install krb5-user -y
sudo sed -i '2s/ATHENA.MIT.EDU/LOCAL.DOMAIN.COM/' /etc/krb5.conf
sudo sed -i '3i\dns_lookup_realm = true' /etc/krb5.conf
sudo sed -i '4i\dns_lookup_kdc = true' /etc/krb5.conf

sudo sed -i '15s/#NTP=/NTP=ntp2.local.domain.com/' /etc/systemd/timesyncd.conf
sudo timedatectl set-ntp true
sudo systemctl restart systemd-timesyncd.service
sudo timedatectl --adjust-system-clock

sudo touch /etc/realmd.conf
cat <<EOT >> /etc/realmd.conf
[users]
 default-home = /home/%D/%U
 default-shell = /bin/bash

[active-directory]
 default-client = sssd
 os-name = Ubuntu Workstation
 os-version = 18.04

[service]
 automatic-install = no

[local.domain.com]
 fully-qualified-names = yes
 automatic-id-mapping = no
 user-principal = yes
 manage-system = yes
EOT

sudo realm join --verbose --user=domain_admin_user --computer-ou=CN=Computers,DC=local,DC=domain,DC=com local.domain.com
sudo sed -i '32i\session optional pam_mkhomedir.so' /etc/pam.d/common-session
sudo sed -i '6i\use_fully_qualified_names = False' /etc/sssd/sssd.conf
sudo service sssd restart

sudo reboot
```

this works, I can see the new machine on AD and domain users can log in to the machine, the problem is that the username gets created as [FONT=courier new]username@local.domain.com[/FONT] instead of just [FONT=courier new]username[/FONT], and this causes issues with some commands and programs, as for example it can't create the "[FONT=courier new]username@local.domain.com[/FONT]" group.

I have tried adding the "[FONT=courier new]default_domain_suffix = local.domain.com[/FONT]" line to [FONT=courier new]/etc/sssd/sssd.conf[/FONT] but users are still created as "[FONT=courier new]username@local.domain.com[/FONT]".

What am I doing wrong and what should I do so the domain users get created as [FONT=courier new]username[/FONT] only?

Thanks!

---

