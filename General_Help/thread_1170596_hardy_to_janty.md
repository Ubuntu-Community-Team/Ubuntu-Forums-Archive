---
title: "hardy to janty"
date: 2009-05-26
forum: General Help
---

### Post by hp owner on 2009-05-26
is their a code i can enter in the terminal to upgrade??? btw i use the 64 bit version.

---

### Post by Girl™ on 2009-05-26
Update */etc/apt/sources.list* to say *jaunty* instead of *hardy* and then do an *aptitude update && aptitude safe-upgrade && aptitude dist-upgrade*.

---

### Post by .nedberg on 2009-05-26
I would recommend a step-by-step upgrade from Hardy to Intrepid to Jaunty.

Use the recommended update from Hardy to Intrepid: [https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades)

Then from Intrepid to Jaunty: [https://help.ubuntu.com/community/JauntyUpgrades](https://help.ubuntu.com/community/JauntyUpgrades)

From Hardy:
```

-Network Upgrade for Ubuntu Servers (Recommended)

-Install update-manager-core if it is not already installed: 
sudo apt-get install update-manager-core

-Edit /etc/update-manager/release-upgrades and set: 
Prompt=normal

-Launch the upgrade tool: 
sudo do-release-upgrade
-Follow the on-screen instructions.

```
then when on Intrepid:
```

sudo do-release-upgrade

```

---

### Post by Kozar on 2009-05-28
Do you have a howto on going directly from hardy to jaunty? I've got a cd with jaunty on it and since my internet connection is abusivley slow (sometimes just 3kbps) it's very impractical to download intrepid first.

---

### Post by raymondh on 2009-05-28
That would be considered a fresh, clean install which is OK (i.e, no need to jump to intrepid if you plan to install using the jaunty liveCD).

try out the liveCD first to see how it interacts with your specs.

back up your files (if possible, also on to an external HD) that way, if anything bonkers your set-up, your files are safe.

See the release notes for Jaunty to prepare yourself.

[http://www.ubuntu.com/getubuntu/releasenotes](http://www.ubuntu.com/getubuntu/releasenotes)

Good luck and regards,

---

### Post by raymondh on 2009-05-28
[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

---

