---
title: "Upgrade, Re-boot, and Log-in via SSH?"
date: 2009-06-13
forum: General Help
---

### Post by astroryan7 on 2009-06-13
Post from "Installation and Upgrades" section, but perhaps more applicable in "General" section...

I need to upgrade from Dapper to a newer version (perhaps 9.04), but I am half-a-world away from the actual machine. So, I've been SSHing in. My question is (and I've seen it partially answered in other posts, but not completely): Can I upgrade from 6.06 to 9.04, re-boot to allow changes to take effect, and also log-in (at the normal username/password screen), via SSH? And is this last step, the log-in part that I could not find answered in other posts, necessary via SSH, or will it log-in automatically after the re-boot?

I have root access.

Any pointers are appreciated, thanks!

---

### Post by nandemonai on 2009-06-13
In theory it's possible but I'd be doubtful it'll be easy without physical access (or ability to tell someone to access it for you).

First, dapper is old, real old. You'd need to first do a LTS to LTS upgrade, ie Dapper to Hardy. Then Hardy -> Interpid -> Jaunty.

The problem I've faced with a Dapper to Hardy upgrade is the change from hdX references to sdX. While the machine will still likely boot after the upgrade (hopefully) your drive refs will be seriously borked and the machine spits errors to tty like no tomorrow which makes it incredibly hard to edit /etc/fstab from tty.

Also you have to be real careful about doing the upgrades properly. A simply changing of the /etc/apt/sources.list file and apt-get update && apt-get dist-upgrade will not suffice. You'd need to follow the 'server' method of upgrading from tty.

> Network Upgrade for Ubuntu Servers (Recommended)

   1.

      Install update-manager-core if it is not already installed:

      sudo apt-get install update-manager-core

   2.

      Launch the upgrade tool:

      sudo do-release-upgrade

   3. Follow the on-screen instructions. 

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

Based on my experience you're asking for trouble without physical access.

As far as the log in stuff goes, rebooting will sever your ssh connection. You'd need to wait till the machine comes back up and login again.

Some extra info would be handy.. Is this a server install? Desktop Install? If desktop is there no way someone can run the upgrade via the GUI for you? If a server install then why not stick to upgrading just to Hardy?

---

