---
title: "Sharring files between XP Home and Ubuntu 5.10"
date: 2005-12-25
forum: General Help
---

### Post by barqster on 2005-12-25
First of all is it even possible? Also, to give a little background on the internet connection between the two. My laptop is running Windows XP Home, and my desktop is running Ubuntu 5.10. My Laptop is recieving data via wireless network and my desktop is connected to my laptop by a crossover. The internet works fine on both computers, I just want to know how to share files between the two.

---

### Post by zoiks on 2005-12-25
As long as your two computers can see each other's ip addresses then sharing is no problem.  If you want to see your WinXP shares on your ubuntu machine, an easy way is to open the file manager, hit <ctrl>-L, and enter the address "smb://hostip/sharename".  You should see your files in the window.

For the other way around, install samba on the ubuntu machine, make sure the smb.conf file is set up correctly, add the user to the samba system with "smbpasswd -a <username>" on the ubuntu machine, and in the Windows machine use "Map a Network Drive", using \\hostip\sharename.

(Interesting thing is that XP Home doesn't allow you to put a password on a shared folder.  Isn't that great?)

---

### Post by barqster on 2005-12-25
I tried to open the location in Ubuntu, but it said,"**The folder contents could not be displayed** Sorry, couldn't display all the contents of "Windows Network: 192.168.0.1"

Oh and the share folder I'm trying to access is my music folder; I right clicked on it and told it to be a share folder, and to allow people on the network to edit my files in the folder.

---

### Post by barqster on 2005-12-25
anyone else around? I'm trying to do the samba thing zoiks also said I should try

---

### Post by zoiks on 2005-12-25
Some things to check:

1) That your software firewalls are turned off or are at least allowing access.
2) Make sure you have the ip addresses correct.  You can do "ping <ip address>" from both windows and linux to make sure networking is allowing you to connect to the other one.
3) Sounds like you've already enabled file sharing in Windows.  Make a note of the name you're giving the share.  Note it can be different from the folder's name.
4) Try just "smb://<host ip address>" in ubuntu's file manager.  You may not be able to browse, but you should get some response from the XP host machine.  If this gives some response, then "smb://<host ip address>/<share name>" should work.
5) Try looking in "Places|Network Servers" in the gnome menu, and see if you can browse to the XP host.

---

### Post by barqster on 2005-12-27
OK I got my Ubuntu computer to be able to grab files from my computer, but I can't grab files from Ubuntu on my Winodws laptop. Any suggestions?  I've installed samba ocording to Ubuntu Wiki, but I don't have a smb.conf (should I make one?) and if so, is there a special way to make it or just: sudo gedit /etc/smb.conf? And after I do make it, what should I put in it?

---

### Post by Ozitraveller on 2005-12-27
There is a whole bunch of useful stuff here:

Samba Server
[http://ubuntuguide.org/#sambaserver]("http://ubuntuguide.org/#sambaserver")

EDIT:

If you have installed samba /etc/samba/smb.conf will definitely exist. But the instructions for doing the changes are in the samba server section of the user guide above. I think it's in the help menus as well!

---

