---
title: "black screen of death"
date: 2007-11-06
forum: Desktop Environments
---

### Post by flander on 2007-11-06
Running version 7.10
This morning I applied updates to my system including one to System Monitor which failed as that was running at the time of the update. I now find that when I switch on the PC before it gets to the logon screen I just get a black screen. Having seen this before I thought I could fix it by running sudo dpkg-reconfigure xserver-xorg   That created a new xorg.conf but the system still stops at the black screen. Can somebody please suggest what I should look at next to solve the problem ! I am able to use my PC by booting from a 7.04 Live Disc.

Thanks in advance

Fixed It  :-)

For info I managed to get to a prompt and then keyed
sudo apt-get install   A message came back about running dpkg  manually with some parameters, so I keyed them as shown. A couple of messages displayed about libc6 being configured.
Did a reboot and up she comes  ------ one very happy bunny

---

