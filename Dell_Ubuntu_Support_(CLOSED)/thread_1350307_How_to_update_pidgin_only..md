---
title: "How to update pidgin only."
date: 2009-12-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by psy1013 on 2009-12-09
I have a Dell Mini 9.  Evidently Pidgin needs to be updated as the older version no longer works.  However, when I first got my netbook, I loaded updates and it crashed my system because updated filled the 4GB HD.  So I had to reload and have not updated anything since.  When I do an update check it tells me of 60MB that will need to be updated, but I don't see Pidgin on the list.  I don't really want to update anything else if I don't need to.  Can anyone way smarter then me with linux assist?

---

### Post by gbrainin on 2009-12-09
The Pidgin maintainers actually keep their own repository, which will keep Pidgin more updated than the regular repositories will.  The instructions for adding the repository are on their website at [http://www.pidgin.im/download/ubuntu/]("http://www.pidgin.im/download/ubuntu/").

Once you add the repository (and reboot and/or reload), the latest Pidgin updates should appear in your update manager.

---

### Post by psy1013 on 2009-12-09
I checked yesterday and got several updates which is going to take up 62MB.  Is there any way I can choose only the Pidgin to update?  I can't select or deselect updates that I want.  Thank you for all the help.  :)

---

### Post by psy1013 on 2009-12-09
OK, I tried what they said on the website:

teya@teya:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com \     67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
[sudo] password for teya: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com   67265eb522bdd6b1c69e66ed7fb8bee0a1f196a8
gpg: requesting key A1F196A8 from hkp server keyserver.ubuntu.com
gpg: key A1F196A8: "Launchpad PPA for Pidgin Developers" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

But when I look for new updates it shows me a bunch of dell.mini updates, but no updates for pidgin.

Thanks for helping a nubface.  :)

---

### Post by MelDJ on 2009-12-09
in terminal type sudo apt-get update pidgin

---

### Post by psy1013 on 2009-12-09
When I do that I get:

teya@teya:~$ sudo apt-get update pidgin
[sudo] password for teya: 
E: The update command takes no arguments
teya@teya:~$

---

### Post by rhonaldmoses on 2009-12-09
Hi,

Pidgin latest is available @ Ubuntu PPA repository. Try the below:

[https://launchpad.net/~pidgin-developers/+archive/ppa](https://launchpad.net/~pidgin-developers/+archive/ppa)

Regards,

---

### Post by psy1013 on 2009-12-09
I have gotten it, I think, to update, but how to I load it now?

teya@teya:~$ sudo apt-get update
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Sources
Reading package lists... Done

The 3 files I have in the Synaptic Package Manager are:
libpurple0
pidgin-data
pidgin

When I select pidgin to be uploaded it tells me that pidgin-otr and libpurple0 will be removed.  Is this ok?  Sorry for the stupid questions.  I'm not great at linux.

---

