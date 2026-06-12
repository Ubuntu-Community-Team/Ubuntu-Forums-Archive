---
title: "A videolan (VLC)for breezy that works for streaming"
date: 2006-02-07
forum: Desktop Environments
---

### Post by Jazman on 2006-02-07
I'm looking for a version of videolan (VLC) for breezy that works for streaming over a network.  The version of VLC in the repositories crashes with a segmentation fault whenever you try to stream with it.  It will however accept streams directed at it.
Questions:
Is their a deb binary build out there for breezy that will do that?
Are the deb nightly builds at the videolan site compatable with breezy?
What would I need to compile VLC myself? (I've never done this but am willing to try)
Comments? Suggestions, etc.

---

### Post by tagg3rx on 2006-02-07
Hi Jazman

I was having simular probs till I ran Automatix

[http://www.ubuntuforums.org/showthread.php?t=66563](http://www.ubuntuforums.org/showthread.php?t=66563)

Not sure if it was the actual VLC or some of the MPEG decoders but after the install of all the stuff it does VLC streamed like a champ.

---

### Post by Jazman on 2006-02-07
I tried the automatrix installer - with choices for the multimedia codecs, media players, and AUD-DVD codecs options selected.
VLC version shows VLC media player 0.8.4-svn20040920 Janus
Alas, I still get segmentation fault when trying to stream.

Does the VLC version match up with what you use?
Any other options?
Thanks

---

### Post by Jazman on 2006-02-09
2/9/06
FIXED!!
Fiewall on host machine was blocking streaming (incoming net addresses)
That made vlc seg fault when used in the gui mode and stall when used in the command line mode.
Sidenote: vlc debs in Ubuntu depositories not up to date with other distro's - maybe drapper will fix this.

---

### Post by squashstring on 2006-02-09
Whenever I try getting VLC to stream Unicast or Multicast, I also get an instant shutdown of VLC in graphics mode, or a seg fault when in command line mode.

I don't think I'm running a firewall (how can I tell)?

Any other suggestions?  I obtained VLC by doing a sudo apt-get install wxvlc.  I think I may have enabled extra repositories.

I also tried automating the process by using automatix.  No change.

Paul

---

### Post by Jazman on 2006-02-09
I'm new at this so here is what I found.  Short answer:  Unless you can ping between the two machines no streaming will take place.  Let me explain.  I have two machines.  EPOX a Windows XP based machine with two ethernet cards.  eth0 is connect to the DSL modem and eth1 is connected to UBUBTU my Ubuntu brezzy based machine that has an ethernet card eth0 on it.  eth1 on EPOX has an address of 192.168.1.1, eth0 on UBUNTU has an address of 192.168.1.2
When I boot up UBUNTU for some reason networking is not active.  I'm not sure if this is a problem in the breezy distribution or if I have the setup jacked up.  In any case in order to get networking up on UBUNTU I have to do the following each time I boot up.
sudo ifconfig lo up
sudo ifconfig eth0 up
sudo smbd -D
sudo nmbd -D
Then go to System -> Administration -> Networking -> Ethernet connection and deactivate it and then activate it.
I can then ping EPOX (192.168.1.1) from UBUNTU and get a reply and
ping UBUNTU (192.168.1.2) from EPOX and get a reply.
Now I can use videolan for streaming between the two.
On my EPOX Windows XP machine I had to set my firewall (ZoneAlarm) so that eth1 on EPOX was "trusted" and eth0 on UBUNTU was "trusted".  That is both address were not blocked by the firewall.
I don't think that the stock install of breezy puts a firewall into play on the UBUNTU based machine.  I could be wrong.  The version of vlc I'm using on UBUNTU is vlc 0.8.4-test1 Janus.  I did the automatrix thing before I discovered the firewall seting thing on the Windows XP machine.
This is how I got vlc to stream - there may be more involved that I may yet discover.  One other thing, in order to share between UBUNTU and EPOX I had to install samba on the UBUNTU machine and configure samba.  That is another story.

---

