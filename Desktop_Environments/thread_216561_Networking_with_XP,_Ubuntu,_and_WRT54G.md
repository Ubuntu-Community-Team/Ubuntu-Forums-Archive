---
title: "Networking with XP, Ubuntu, and WRT54G"
date: 2006-07-15
forum: Desktop Environments
---

### Post by Cheesemold on 2006-07-15
Here's my situation.  I have two computers, both running WinXP Pro, connected via ethernet cables to a Linsys WRT54G router.  The router is then hooked up through another ethernet cable to the modem, which gives me my tangy, daily dose of internet.  Ubuntu is installed on a laptop, which interfaces with the router (and thus the rest of the network) via wifi.  I am, for some reason, unable to do various file/printer sharing between computers for who knows why.  I eventually got it boiled down to the hypothesis that the router blocks NetBIOS requests or something--using a computer's name for doing tasks will not work, but using the LAN ip number will(under many cases).

Linux is able to manipulate files between itself and other computers, but other computers require a username and password when trying to do the same to linux.  What is the deal?  I have tried using my ubuntu user/pass but this does not work.

WinXP machines actually require this password when trying to connect to various other machines, and I'm really not sure why.

This is probably more of a "how do I fix my XP machines to work with Linux(and themselves)?" instead of a "how do I fix Linux to work with XP" question.

Or maybe even a "How do I fix my stupid router?" question.

---

### Post by x64Jimbo on 2006-07-15
You'll have to edit your /etc/samba/smb.conf
Under the global parameters, change your security to "share" and under the specific share directory parameters, set guest ok to "yes"
then restart your samba by doing this:
sudo /etc/init.d/samba restart

---

