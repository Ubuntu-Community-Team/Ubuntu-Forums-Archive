---
title: "Financial software recommendations"
date: 2009-02-06
forum: General Help
---

### Post by sr_guy on 2009-02-06
I'm running Ubuntu 8.10. I'm looking for personal checking software for ubuntu. I am looking for open source financial/accounting software that I would be able to access remotely through web interface or on that would invoke a java app when accessed remotely. Is there an accounting software out there for linux that can be accessed remotely? If not, what other financial software would you all recommend?

---

### Post by kramulous on 2009-02-06
Hi,

  No doubt you've probably heard of GNUCash.  It, as far as I'm aware, doesn't do remote access.  But just install sshserver as well with X tunneling.

  I use GNUCash to watch my accounts.  It's pretty good once you get used to it.

GNUCash
sudo aptitude install gnucash

---

### Post by 73ckn797 on 2009-02-06
> **kramulous said:**
> I use GNUCash to watch my accounts.  It's pretty good once you get used to it.

That has been the issue with me getting used to it. I have not messed with it in a while. Seems too much to set up and it would crash when trying to import Quicken data.

---

### Post by sr_guy on 2009-02-07
I have gnucash installed, and already have my bank data loaded. I will be accessing it at work. I prefer not to have to use vnc as it is awkward and clumsy at times. How do I go about using gnucash via ssh remotely? I thought gnucash was only gui-based software, and cannot be accessed through commandline.

---

### Post by dcstar on 2009-02-07
> **sr_guy said:**
> I'm running Ubuntu 8.10. I'm looking for personal checking software for ubuntu. I am looking for open source financial/accounting software that I would be able to access remotely through web interface or on that would invoke a java app when accessed remotely. Is there an accounting software out there for linux that can be accessed remotely? If not, what other financial software would you all recommend?

Moneydance is a Java app, but it is not free (a lot recommend it, including me).

---

### Post by Tanker Bob on 2009-02-07
Another vote for Moneydance. I tried GNUCash and KMoney, but Moneydance was the only program with a complete set of features built-in. Moneydance also imported my Quicken data with minimal issues. The others couldn't get here from there. Moneydance isn't free, but it's been worth every penny to me.

---

### Post by kramulous on 2009-02-08
To access GNUCash remotely (well, just about any program for that matter), you want to install ssh server on the remote machine.  

```
sudo apt-get install openssh-server
```

This will complete the installation.the package will take care of creating the initial RSA and DSA keys you need, as well as providing you with a default SSH config.
[B]
Connecting to the server[/B]

Now you can connect to the server from other machines using the following command

ssh serveripaddress

Example

ssh 195.14.2.1

**Configure SSH**

The main configuration file located at /etc/ssh/sshd_config and the default configuration will enable remote root logins and X11 forwarding which is not good for your server security.  Disable these two options.

**Disable remote root logins**

For this you need to search for the following line in 
/etc/ssh/sshd_config file

PermitRootLogin yes

and change this to the following one

PermitRootLogin no

**Disable X11 forwarding**

For this you need to search for the following line in 
/etc/ssh/sshd_config file

X11Forwarding yes

and change this to the following one

X11Forwarding no

After finishing your configuration you need to restart SSH server using the following command

```
sudo /etc/init.d/ssh restart
```

**X11 Forwarding**

To use GNUCash remotely, you want to type
```

ssh -X serveripaddress
```

---

### Post by kramulous on 2009-02-08
Sorry, then, when logged into the remote machine, type at the command line

```
gnucash
```

It should work.

Are the remote machine and the client machine linux installs?  If the client machine is a windos box there are a few extra minor steps.

---

