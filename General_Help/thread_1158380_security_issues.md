---
title: "security issues"
date: 2009-05-13
forum: General Help
---

### Post by grubster on 2009-05-13
can someone give me some advice on security programs for Ubuntu 8.10 just some general info about securing my system any advice would be appreciated because i have been using xp for too long and i am stuck in the windows security frame of mind.

---

### Post by Electron on 2009-05-13
You have come to the right place! To start follow the link

[https://help.ubuntu.com/9.04/keeping-safe/C/index.html](https://help.ubuntu.com/9.04/keeping-safe/C/index.html)

Also from bodhi this is a pretty good post

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Only one thing, keep in mind that your computer is secure as long as you are secure, good security practices apply to any OS. However, Ubuntu (Linux) is way more secure than Xp or any other windows crap.

---

### Post by albert ozzy on 2009-05-13
Most of the popular spywares/worms wont work on a linux distribution. So you are 1-0 already. There're experimental software that'll  do you harm. you can get these stuff from:

1-) Online - Browsing Internet, Installing software from internet
2-) Offline - From external drives (HDD, CD etc.) or direct access of 3rd party

For #1 : You won't use internet explorer so you're gonna be almost safe surfing the internet :P But i'd suggest using Firefox with extensions like:
a) NoScript : [https://addons.mozilla.org/en-US/firefox/addon/722](https://addons.mozilla.org/en-US/firefox/addon/722)
b) Adblock : [https://addons.mozilla.org/en-US/firefox/addon/1865](https://addons.mozilla.org/en-US/firefox/addon/1865)
c) BetterPrivacy: [https://addons.mozilla.org/en-US/firefox/addon/6623](https://addons.mozilla.org/en-US/firefox/addon/6623)
d) WOT: [https://addons.mozilla.org/en-US/firefox/addon/3456](https://addons.mozilla.org/en-US/firefox/addon/3456)

If you're gonna use Firefox Password Manager to store your passwords i strongly recommend you to use a master password.

For #2 : If you're using it on a public computer or someone else can have access to your computer you should password protect your user account on Ubuntu.
Not installing untrusted software is a platform-independent security solution so bear with it.
Additionally you can install a firewall if you want control softwares transferring data off the internet.


These are rather simple security solutions. But will help for starters.

---

### Post by grubster on 2009-05-14
Thanks for all the advice on security, I will now start to relax a bit more and I definitely wont be going back to xp, so thanks.

---

### Post by flax1905 on 2009-05-14
If you are going to open up your server to ftp, ssh, web, or other services, you might want to check into the program, fail2ban. I am running ftp and ssh services at the moment, and this program is set to ban unauthorized access by banning IP addresses either temporary or permanently from users trying to hack into your system. 

My server was getting hit by ssh and ftp requests from China, Japan, Taiwan, India, some US and Europe at the rate of 3 to 5 per sec. before I installed it.  I can only assume some sort of port scanning programs lead them to my server. 

Study the Ubuntu manual regarding setting up accounts and groups, and security before opening up any services. Make sure you are using hard to guess passwords! I have a paperback book that was very helpful: Ubuntu Linux Toolbox, Christopher Negus & Francois Caen.

---

### Post by XCan on 2009-05-14
> **flax1905 said:**
> If you are going to open up your server to ftp, ssh, web, or other services, you might want to check into the program, fail2ban. I am running ftp and ssh services at the moment, and this program is set to ban unauthorized access by banning IP addresses either temporary or permanently from users trying to hack into your system. 

My server was getting hit by ssh and ftp requests from China, Japan, Taiwan, India, some US and Europe at the rate of 3 to 5 per sec. before I installed it.  I can only assume some sort of port scanning programs lead them to my server. 

Study the Ubuntu manual regarding setting up accounts and groups, and security before opening up any services. Make sure you are using hard to guess passwords! I have a paperback book that was very helpful: Ubuntu Linux Toolbox, Christopher Negus & Francois Caen.

A good tip for espeically ssh and ftp that are intedende only to be used by authorized users is to change the default port. This helps A LOT.

---

