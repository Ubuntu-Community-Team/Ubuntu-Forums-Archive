---
title: "Unable to get exclusive lock?"
date: 2009-04-28
forum: General Help
---

### Post by Falx_ on 2009-04-28
When either using terminal or add/remove programs im getting,
"Unable to get exclusive lock"

or

"E: Could not get lck /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)

Thanks

---

### Post by Anthon on 2009-04-28
Do you get this when you open the terminal, or when you try to run dpkg/aptitude or something like that *in the terminal*. If you have Synaptic open at the same time, you will get messages like this.

---

### Post by dcstar on 2009-04-28
> **Anthon said:**
> Do you get this when you open the terminal, or when you try to run dpkg/aptitude or something like that *in the terminal*. If you have Synaptic open at the same time, you will get messages like this.

Or if the scheduled CRON updating is occuring.

---

### Post by Falx_ on 2009-04-28
I get it when i try to install an app,
for example im trying to get wine, and typing "sudo apt-get install wine"
I dont know if this is correct, but the message i was saying is coming up when i type that.
Also how to i tell if the CRON of whatever is updating?
Cheers.

---

### Post by Falx_ on 2009-04-28
bump :)

---

### Post by bapoumba on 2009-04-28
Please try:
```
sudo apt-get clean
sudo apt-get -f update
```
and post the complete error message here, thanks.

---

### Post by Falx_ on 2009-04-28
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAA
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 28A8205077558DD0
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2ED6BB6042C24D89
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
W: GPG error: [http://deb.mulx.net](http://deb.mulx.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B1F5957DE4946268
W: GPG error: [http://deb.opera.com](http://deb.opera.com) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?



Appologies for the late reply.

---

### Post by Falx_ on 2009-04-28
Bump!

---

### Post by Falx_ on 2009-04-28
bump

---

### Post by kpkeerthi on 2009-04-28
> **Falx_ said:**
>  
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

At any point in time, only one package manager (apt, apt-get, aptitude, update-manager, synaptic) should be running. If you are not sure, **reboot your PC**.

> 
The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791

Have you installed the public keys of the PPA repositories you have in /etc/apt/sources.list?

---

### Post by Falx_ on 2009-04-28
Apologies but im not sure about installing the PPA or whatever you were talking about.
Also i fear to reboot my pc, last reboot the login screen showed nothing but the desktop and disabled all of my options, i had to reinstall ubuntu.....

Thanks.

---

### Post by kpkeerthi on 2009-04-28
Can you run this command and copy/paste the contents here?
```
gedit /etc/apt/sources.list
```

---

### Post by Falx_ on 2009-04-28
# Salimane Adjao Moustapha's Ubuntu Jaunty Jackalope 9.04 Sources list
#
# Repository List based on standard Jaunty with many extra packages
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number):
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you have a gpg key URL use (replace URL with the key address):
#
# wget -q [http://lut1n.ifrance.com/repo_key.asc](http://lut1n.ifrance.com/repo_key.asc) -O- | sudo apt-key add -
#
# If you have a gpg key file use (replace FILE with the key file):
#
# sudo apt-key add FILE
# Ubuntu supported packages
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jaunty main restricted multiverse universe
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted multiverse universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-proposed main restricted universe multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jaunty main restricted multiverse universe
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-proposed main restricted universe multiverse
#Canonical Commercial Repository
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-backports partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-updates partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-security partner
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-proposed partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-backports partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-updates partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-security partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty-proposed partner
#gnome-globalmenu
deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) jaunty main
#opera
deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) lenny non-free
#skype
deb [http://download.skype.com/linux/repos/debian](http://download.skype.com/linux/repos/debian) stable non-free
#firefox
deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) jaunty main
#gnome-do
deb [http://ppa.launchpad.net/do-core/ubuntu](http://ppa.launchpad.net/do-core/ubuntu) jaunty main
#compiz-fusion
deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) jaunty main
#google
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free
#medibuntu
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free
# MySQL Workbench
deb [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/) binary/
deb-src [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/) source/
# Depot PlayOnLinux
# KEY GPG: wget -q [http://deb.mulx.net/pol.gpg](http://deb.mulx.net/pol.gpg) -O- | sudo apt-key add -
deb [http://deb.mulx.net/](http://deb.mulx.net/) jaunty main
# Ubuntu tweak
deb [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/tualatrix/ubuntu](http://ppa.launchpad.net/tualatrix/ubuntu) jaunty main
##Themes du ZgegBlog: Project Bisigi
deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) jaunty main

---

### Post by kpkeerthi on 2009-04-28
```


#gnome-globalmenu
deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu jaunty main
#opera
deb http://deb.opera.com/opera/ lenny non-free
#skype
deb http://download.skype.com/linux/repos/debian stable non-free
#firefox
deb http://ppa.launchpad.net/fta/ubuntu jaunty main
#gnome-do
deb http://ppa.launchpad.net/do-core/ubuntu jaunty main
#compiz-fusion
deb http://ppa.launchpad.net/compiz/ubuntu jaunty main
#google
deb http://dl.google.com/linux/deb/ stable non-free
#medibuntu
deb http://packages.medibuntu.org/ jaunty free non-free
# MySQL Workbench
deb ftp://ftp.mysql.com/pub/mysql/downlo...-tools/ubuntu/ binary/
deb-src ftp://ftp.mysql.com/pub/mysql/downlo...-tools/ubuntu/ source/
# Depot PlayOnLinux
# KEY GPG: wget -q http://deb.mulx.net/pol.gpg -O- | sudo apt-key add -
deb http://deb.mulx.net/ jaunty main
# Ubuntu tweak
deb http://ppa.launchpad.net/tualatrix/ubuntu jaunty main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu jaunty main
##Themes du ZgegBlog: Project Bisigi
deb http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bisigi/ppa/ubuntu jaunty main

```
These are the unsuported PPA repositories you have. I'm surprised these got in without your knowledge.

---

### Post by kpkeerthi on 2009-04-28
For now, I suggest you do this
1. ```
gksudo gedit /etc/apt/sources.list
```

2. Delete the line starting from **#gnome-globalmenu** through end of file. Save and Exit.

3. ```
sudo rm /var/lib/dpkg/lock 
```

4. ```
sudo apt-get update
```

---

### Post by huntzire on 2009-04-28
Indeed a few of them myself I have never seen... lol

---

### Post by Falx_ on 2009-04-28
[FONT=monospace]rm: cannot remove `/var/lib/dpkg/lock': No such file or directory



[/FONT]

---

### Post by 3rdalbum on 2009-04-28
> **Falx_ said:**
> [FONT=monospace]rm: cannot remove `/var/lib/dpkg/lock': No such file or directory



[/FONT]

Are you running this as root?

---

### Post by kpkeerthi on 2009-04-28
> **Falx_ said:**
> [FONT=monospace]rm: cannot remove `/var/lib/dpkg/lock': No such file or directory

[/FONT]
Just skip that go to Step# 4.

---

### Post by Falx_ on 2009-04-28
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by 3rdalbum on 2009-04-28
> **Falx_ said:**
> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

Run it in the terminal.

---

### Post by Falx_ on 2009-04-28
Thanks i tried initially and nothing happened, now it works.
Cheers.


Ugh yet i still cant install, the same lock error is occuring

---

### Post by kpkeerthi on 2009-04-28
Like I said. I would reboot. If it is still locked, use the rm command to remove the file it says is locked.

---

### Post by opap on 2012-12-09
> **bapoumba said:**
> Please try:
```
sudo apt-get clean
sudo apt-get -f update
```and post the complete error message here, thanks.

```
@Mint13 ~ $ sudo apt-get -f update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by Wim Sturkenboom on 2012-12-09
If you're sure nothing is using it (update manasger, synaptic, software center), you can (re)move the lock file

In a terminal

to delete (remove)
```

sudo rm /var/lib/dpkg/lock

```

to rename (move)
```

sudo mv /var/lib/dpkg/lock /var/lib/dpkg/lock.old

```

By the way. moderators here don't like reviving of old threads; it might even be in the forum policy. This one will more than likely be closed ;)

---

### Post by oldos2er on 2012-12-09
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

