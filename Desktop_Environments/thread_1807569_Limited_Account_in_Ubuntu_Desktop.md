---
title: "Limited Account in Ubuntu Desktop"
date: 2011-07-19
forum: Desktop Environments
---

### Post by yameen101 on 2011-07-19
Can we create a limited user account in ubuntu like XP where user can not be able to change its networking settings (like changing IPs / enable & disable netwrok interface).

Thanks
Yameen

---

### Post by haqking on 2011-07-19
easiest way is go to users and groups and add a user then choose advanced settings and remove priveleges from the user.

---

### Post by yameen101 on 2011-07-19
But this is not included in privilege list... :(

---

### Post by matt_symes on 2011-07-19
Hi

Yes it is possible as haqking suggests. 

Create a user and remove them from the admin account.

Kind regards

---

### Post by yameen101 on 2011-07-19
I have created a account... but user has authority to change network settings... am i wrong? :(

---

### Post by matt_symes on 2011-07-19
Hi

Open a terminal and type

```
groups <user_name>
```where <user_name> is the name of the new limited user account.

Copy and paste the results back here.

Kind regards

---

### Post by yameen101 on 2011-07-19
s2@hzco:~$ groups as4
as4 : as4 adm dialout fax cdrom floppy tape dip video plugdev fuse


as4 is limited user while as2 is admin account.

---

### Post by yameen101 on 2011-07-19
I have checked it again, now i have unchecked all privileges and the result is:

as2@hzco:~$ groups as4
as4 : as4


but still as4 has an option to edit network connections.

---

### Post by haqking on 2011-07-19
> **yameen101 said:**
> I have checked it again, now i have unchecked all privileges and the result is:

as2@hzco:~$ groups as4
as4 : as4


but still as4 has an option to edit network connections.

login as that user and change your network.

log back in as you and you will see no changes have been made.

your first listing showed then as being in adm groupd by the way

---

### Post by yameen101 on 2011-07-21
Dear haqking,

I have now format my pc and has created two account, one is admin and the other is as2. Through admin account i have disabled all privileges of as2. The result is as under using groups commad:

as2@admin:~$ groups as2
as2 : as2

Now, icon in top panel for networking disappeared but still as2 has an option through system > Preferences > Network Connections to change IP / enable & disable wireless access point.

I want user to have no choice to change IP and DNS settings. I am  not an expert in netwokring or in linux. Hope you will bear this #-o

Thanks

---

### Post by haqking on 2011-07-21
> **yameen101 said:**
> Dear haqking,

I have now format my pc and has created two account, one is admin and the other is as2. Through admin account i have disabled all privileges of as2. The result is as under using groups commad:

as2@admin:~$ groups as2
as2 : as2

Now, icon in top panel for networking disappeared but still as2 has an option through system > Preferences > Network Connections to change IP / enable & disable wireless access point.

I want user to have no choice to change IP and DNS settings. I am  not an expert in netwokring or in linux. Hope you will bear this #-o

Thanks


create the user, remove all priveleges.

If you want to prevent internet access etc then under your admin account remove the tick from available for all users for the network connectsion you have.

When that user logs in, yes they can go to network connections and start configuring a ip address etxc, however when they click apply is should say system prevents user from making changes and will ask for admin password.

try it ?

---

### Post by mikewhatever on 2011-07-21
In Ubuntu, things like network, sound and desktop settings are set on per-user level. In effect, each user can choose what settings to use, but these settings will only affect that user. To override that behavior for networking, you'll probably have disable the network manager and use /etc/network/interfaces instead.

---

### Post by matt_symes on 2011-07-21
Hi

Have you looked at app armor. I believe you can lock it down using that.

Kind regards

---

### Post by yameen101 on 2011-07-21
> **mikewhatever said:**
> In Ubuntu, things like network, sound and desktop settings are set on per-user level. In effect, each user can choose what settings to use, but these settings will only affect that user. To override that behavior for networking, you'll probably have disable the network manager and use /etc/network/interfaces instead.


How to disable network manager?

---

### Post by yameen101 on 2011-07-22
Can limited account is available in other distro?
Like Linux Mint or Fedora????

---

### Post by rushikesh988 on 2011-07-22
> **yameen101 said:**
> can limited account is available in other distro?
Like linux mint or fedora????
yes you can

---

### Post by yameen101 on 2011-07-22
Means this option is available in linuxmint???

---

### Post by mikewhatever on 2011-07-22
I think in Mint it's the same as in Ubuntu, as they use the same Gnome Network Manager. It's a trifle of terminology, but what you seem to want is to lock down an account so that it won't make any networking changes. A limited account is just that which can't make global system changes.

You can stop the Network Manager with **sudo service network-manager stop**.

---

