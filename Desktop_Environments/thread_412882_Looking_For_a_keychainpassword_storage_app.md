---
title: "Looking For a keychain/password storage app"
date: 2007-04-18
forum: Desktop Environments
---

### Post by pormogo on 2007-04-18
While I love ubuntu and I really have grown to enjoy using my desktop more then my laptop (mac OS 10.4.9) I have to say that I miss the functionality the key chain offers me on my desktop.

It gives me a quick place to store passwords, or notes that I want to be encrypted and does an overall awesome job of centralizing passwords. Is there anything even remotely like this in the repositories somewhere. Hell even something more like 1passwd (mac) or Password Keeper or obliete for windows would be welcome. Thanks for the advice :)

---

### Post by gene6482 on 2007-04-18
if you're using gnome i'm pretty sure it's built in

---

### Post by b1k3r4ck on 2007-04-18
Not sure if this is what you're looking for but I "think" it might be in the repos [http://keepassx.sourceforge.net/]("http://keepassx.sourceforge.net/")

---

### Post by 50words on 2007-04-18
KeePassX is the Linux version of KeePass, and can be found in the Add/Remove software utility. It's a fantastic program. I use KeePass when in Windows, and KeePassX when in Linux on the same password file. Works great.

---

### Post by thk on 2007-04-18
Revelation is the 'official' app. YMMV.

---

### Post by Buffalo Soldier on 2007-04-18
> **pormogo said:**
> ... notes that I want to be encrypted

```
sudo apt-get install seahorse
```

Seahorse description in Synaptic:> Seahorse is a Gnome front end for GnuPG - the Gnu Privacy Guard program. It
is a tool for secure communications and data storage.  Data encryption and
digital signature creation can easily be performed through a GUI and Key
Management operations can easily be carried out through an intuitive
interface.

In addition it includes a Gedit plugin, can handle files using Nautilus,
an applet for manging stuff put in the clipboard and an agent for storing
private passphrases, as well as a GnuPG and OpenSSH key manager.

---

### Post by pormogo on 2007-04-20
[i]root@pleasantodor:/etc/apache2# apt-get install seahorse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  seahorse: Depends: libdbus-1-2 (>= 0.60) but it is not installable
            Depends: libgail17 (>= 1.6.6) but it is not installable[/i]

:( That looked really cool too

---

### Post by Buffalo Soldier on 2007-04-20
repo servers are probably being bogged down right now from the downloads and people updating to feisty.

---

