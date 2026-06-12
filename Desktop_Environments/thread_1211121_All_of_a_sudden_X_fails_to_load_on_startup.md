---
title: "All of a sudden X fails to load on startup?"
date: 2009-07-12
forum: Desktop Environments
---

### Post by laeg_ on 2009-07-12
So I booted my ubuntu box this morning, got the ubuntu logo with the progressing status bar and I was waiting for my regular login them to load asking for my username and password, instead the computer stayed in what I would call a terminal (black on white text) and asked for my username and password.

The information on my actions on ubuntu over the last 24 hours which I'm about to provide is extensive but I didn't want to leave anything out.

I'm able to login and although irssi loads it says it can't find the freenode server which it usually does no problem. This puts me at a disadvantage because I can load #ubuntu in screen and troubleshoot according to recommendations in real time, instead I've to access #ubuntu from mIRC on Windows XP (on the same computer so GFX card should be okay).

Things I changed yesterday:

Edited the sshd_config and *possibly* ssh_config in error.

Most of the things on [https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#disable-password-authentication]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring#disable-password-authentication") including **AllowUsers laeg** which I understood would make it so I'm the only user able to log in via ssh, it wouldn't have made it so the only was to login is on the command line, right?

Attempted to install an Intruder Detection System following a guide with sudo teskel install lamp-server, after someone telling me that ACID and Snort etc would have too much overhead for my desktop PC which is for personal use I mistakenly killed the process when it was looking for me to setup a MySQL password.

Later when trying to install nmap there were errors which apt-get resolved itself. I then did a sudo teskel remove lamp-server and at some point following a prompt sudo apt-get autoremove.

This morning after X failed to load I tried sudo service gdm start, I'm asked for my password but then just given a bash prompt with no errors. Sudo X loads a full black screen that stays like that until I press the power button.

tail /var/log/syslog shows the eth0 failing to load and then being deactivated

tail /var/log/Xorg.0.log mentions only my mouse

sudo dpkg-reconfigure -phigh xserver-xorg just gives me a bash prompt.

I tried dpkg-reconfigure xserver-xorg twice, restarting each time, because the first option presented said if one doesn't work to try the other.

After this I tried to launch X again and I'm told screens are available but none with a suitable configuration?

How can I fix this? I have my root and home dirs on different partitions so would reinstalling the OS/kernel on root fix the problem and if so would I lose other settings?

Thank you for taking the time to read all of this.

---

