---
title: "Jaunty 9.04 64 bit - What's the newest version of KDE I can install?"
date: 2009-11-24
forum: Desktop Environments
---

### Post by Roasted on 2009-11-24
I'd like to get the most updated version of KDE possible on my Jaunty 9.04 64 bit system. No - Karmic isn't an option. (already tried it, didn't work out, failed to detect all of my HDDs properly).

Soooo what can I do to get the latest KDE? Everywhere I read I read some inconsistencies on what the latest version is supported by Jaunty and whatnot. Does anybody know a concrete answer with a solution?

---

### Post by Untitled_No4 on 2009-11-24
The version in the Jaunty backports is KDE 4.3.2 and according to this ([http://kubuntuforums.net/forums/index.php?topic=3107745.0](http://kubuntuforums.net/forums/index.php?topic=3107745.0)) 4.3.3 will not be backported to Jaunty.

---

### Post by Roasted on 2009-11-25
Okay, sounds good. But where exactly do I go to get the backports for 4.3.2?

EDIT - I followed this guide:

[http://www.ubuntugeek.com/howto-install-kde-4-3-2-on-ubuntu-jaunty.html](http://www.ubuntugeek.com/howto-install-kde-4-3-2-on-ubuntu-jaunty.html)

And installed accordingly. At the end of installing it with the last command "install kde" I got:

Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/kdebase-workspace-bin_4%3a4.3.2-0ubuntu1~ppa1~jaunty1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jason@Skynet:~$


However - in Dolphin - Help - About KDE:

K Desktop Environment
Version 4.3.2 (KDE 4.3.2)

Uhhhh??

EDIT AGAIN - typing from a 2nd computer here. Now when I boot up to my main rig in KDE, it shows me a different looking login screen which I assume is due to going from 4.2 to 4.3.2. Okay, fine. So I log in, I hear the log in sound, I have a mouse... and both monitors just go black... I can't do anything... I tried to log into failsafe, but failsafe failed. LOL? It errored out.

How can I fix this? djklfajs;dkfjasl

EDIT YET AGAIN - I realized that logging in to terminal was in a different option at the KDE screen, so I logged in there and ran sudo nano /etc/apt/sources.list. Then I removed the repository for the PPA and ran apt-get update. It requires me to run apt-get -f install first, and I did, then apt-get update. Then I did apt-get remove kde. Rebooted, bam - back to the original login screen so I thought I was back to 4.2. But when I check Dolphin help - About KDE - it still says 4.3.2. Whaaaat? What am I running? What did I do?

---

### Post by Untitled_No4 on 2009-11-25
Right. Sorry to hear you're having problems, but I think that HOWTO was for people using Gnome and wanting to try KDE rather than KDE people wanting to upgrade to the latest version.

Since you were already running Kubuntu (or so I understand) all you needed to do was:
```

sudo aptitude update
sudo aptitude full-upgrade

```

and that would upgrade KDE to 4.3.2. I think your best option now is to add the ppa repository back to your sources.list and run the above and that should sort out your problems and put you on 4.3.2.

I have done this upgrade myself in Jaunty and it was seamless without any errors. Hopefully that will get you where you want to be.

---

