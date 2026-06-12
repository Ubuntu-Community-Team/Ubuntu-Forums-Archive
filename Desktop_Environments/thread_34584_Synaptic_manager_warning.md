---
title: "Synaptic manager warning"
date: 2005-05-15
forum: Desktop Environments
---

### Post by dqsis on 2005-05-15
Hello Ubuntu friends!

When I open the Synaptic Manager, I get the warning:

[http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/main/binary-i386/Packages.gz:](http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/main/binary-i386/Packages.gz:) 403 Forbidden
[http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/universe/binary-i386/Packages.gz:](http://ubuntu-bp.sourceforge.net/ubuntu/dists/warty-backports/universe/binary-i386/Packages.gz:) 403 Forbidden

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

Do you know how I can fix the problem???

Thanx in advance!!

---

### Post by bruizer on 2005-05-15
I would suspect that you tried to add some extra repositories without adding the gpg keyring... just go into the source.list file in /etc/apt and check which repositories you have configured. If you continue getting this errors, you may want to comment out those lines.

These are a few of the defaults:
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

Once you get the list updated, just "sudo apt-get update"

If you really want the other servers available, you will need to add the 'keyserver' to your gpg list.

---

### Post by dqsis on 2005-05-15
Hey Bruizer! 

THanks for the answer!!! 

What do you mean by:

"you will need to add the 'keyserver' to your gpg list"? 

I' ve never heard about it before! How can I do it?

Thanks!

dqsis

---

### Post by bruizer on 2005-05-15
When you add additional sources to your list, you need to state that you trust the sources GPG Key. Add a <keyserver> to look at and then find out the key that SourceForge uses. Add this in <key> after --rec-keys:

gpg --keyserver <keyserver> --recv-keys <key>
gpg --armor --export <key> | sudo apt-key add -
sudo apt-get update

Of course, you need to be extremely careful about which repositories you use. You may just want to stick with defaults, or known good sources.

---

