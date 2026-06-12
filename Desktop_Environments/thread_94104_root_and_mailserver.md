---
title: "root and mailserver"
date: 2005-11-23
forum: Desktop Environments
---

### Post by petrus bitbyter on 2005-11-23
So I installed Ubuntu and want to use it as a mailserver. But, I can't even log in as root. I was asked to make a user account during installation and so I did but that will not give superuser rights I guess I need to install something. Other Linux installations I ever used gave an opertunity to specify a root password during installation. So is there a default root password in Ubuntu?

As for the mailserver, I checked wiki to find out howto install a mailserver but no result. Anyone has a pointer to a Howto or other doc? Basically I want to have a pop3 server to make it possible to distribute the incoming mail from one mailbox to a number of accounts. 

petrus bitbyter

---

### Post by odin on 2005-11-24
well there's no root account enable by default.Instead you should use the sudo command.this link may help you: [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

But if you really want to use root instead then just login with your user open a terminal and type: sudo passwd root    

Then set your password and after that go to System->Administration->login screen configuration(this is translated from spanish so it might be a bit different but guess you understand) hten in the security tab select the "allow administrator to login in gdm"  if that's what you wnat.Then logout and you are ready to login as root.

Everyone here will not suggest you to use the root account but it is up to you.I'm not using a lot but...

---

