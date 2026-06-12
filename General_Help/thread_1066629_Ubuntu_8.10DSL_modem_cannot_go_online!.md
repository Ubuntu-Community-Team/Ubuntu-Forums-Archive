---
title: "Ubuntu 8.10/DSL modem: cannot go online!"
date: 2009-02-11
forum: General Help
---

### Post by amko on 2009-02-11
Hey, thanks for reading -  Ubuntu rocks! 

Just upgraded to Ubuntu 8.10 after a good Ubuntu 7.10 experience, but still a n00b :)

Anyway, here I go with my problem: cannot connect to the Net, using DSL modem.

--Hardware:

- 2.66GHz Dual-Core Intel Pentium 4 CPU, Intel GGc Motherboard, 1 GB RAM, 40 GB Disk size (single-disk)

- OS : Linux Ubuntu 8.10 (currently installed within Windows XP SP2 - really looking to 'make the switch', soon as I resolve this!)

Issue:

I connect to my ADSL modem via Ethernet. While I can go online in WinXP, I am unable to go online in Ubuntu 8.10.  

I 'became root', ran 'pppoeconf' in a terminal window and followed the sequence. Apart from entering my current provider-assigned user name/password when prompted, made no other changes in any settings.

What I've tried so far on my own:

1. Switched back to WinXP, and visited Ubuntuforums.org. 

Google search returned a post from Ubuntu 8.10 user, advising that this issue had been resolved as follows:  log in as 'root', then  in 'Places>Computer>Filesystem>etc>network>interface',  change a word in the last line in the 'interface' file - from ' manual' to 'dhcp'. Switched back to Ubuntu, logging in as 'root', replicated this process and saved the file, then opened Firefox - no dice. 


2. Tried running 'pon dsl-provider' - here is the output from the terminal:

amko@ubuntu:~$ sudo pppoeconf
Plugin rp-pppoe.so loaded.
amko@ubuntu:~$ pon dsl-provider
Error: only members of the 'dip' group can use this command.
amko@ubuntu:~$ 

- I do not understand why I should be receiving this error. Anyway. Logged in as 'root', created a Group called 'dip' (System>Administration>Users and Groups) and assigned my user account ('amko') to the 'dip' group, logged back in as 'amko' user, and...no dice.

- Then tried running 'plog', here is the output from the terminal:

amko@ubuntu:~$ plog
Feb 10 06:25:00 ubuntu pppd[7357]: Connection terminated.
Feb 10 06:25:30 ubuntu pppd[7357]: PPP session is 55720
Feb 10 06:25:30 ubuntu pppd[7357]: Using interface ppp0
Feb 10 06:25:30 ubuntu pppd[7357]: Connect: ppp0 <--> eth0
Feb 10 06:25:32 ubuntu pppd[7357]: Remote message: Authentication failure
Feb 10 06:25:32 ubuntu pppd[7357]: PAP authentication failed
Feb 10 06:25:32 ubuntu pppd[7357]: Connection terminated.
amko@ubuntu:~$

- Needless to add, unable to get online... 


- Then went to 'System>Preferences>Network Configuration', in the 'Network Connections' dialog, saw 'DSL', 'Wired' and 'Point-to-Point Protocol' tabs, in 'DSL', saw current DSL service provider name displayed, selected it, then clicked on 'Edit', the 'DSL' tab dialog was displayed, re-typed my user ID/PPP/password. Then clicked on the 'Wired' tab, on clicking this, saw that the 'MAC' field was blank. Is this a problem - do I need to add the address?  

Now requesting your advice, thanks. Will write up the process in detail once resolved and re-post for mutual benefit.

(What's that? Why am I not approaching my DSL provider for help? Um, I did try calling Support. When I said Linux there was an eerie silence followed by 'our technical dept. will call you'. I'm still waiting...)


Thank you kindly for your time and support.

Aaaand...hey, Ubuntu rocks!
amko

---

