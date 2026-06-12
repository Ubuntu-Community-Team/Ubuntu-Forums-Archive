---
title: "File Sharing Problem (Saying I need a password)"
date: 2006-05-19
forum: Desktop Environments
---

### Post by srg0425 on 2006-05-19
I recently installed Ubuntu on one of my older computers and I put a folder on the computer with Unbuntu.  I shared the folder and then tried to open the folder from my Windows computer on the same network.  My Windows computer sees the shared folder but will not access it.  When I try to open the folder I shard on Unbuntu on my Windows system I get the screen shown below: (not from my computer but the screen I am getting)

[IMG]http://www.wellesley.edu/Computing/FileSharing/Windows/acc2kxp_imgs/xpconnect.jpg[/IMG

I tried entering the user name and password that I have on Ubuntu but it would not let me in.  I really would like to make it so that I can connect the the shared folder without entering a password.  If you have any ideas on how to solve this please post.

One more question does anyone know where there are step by step instructions on how to set a computer with Ubuntu up as a domain server that windows computers will connect to, to aurthenticate users.  Thanks is advance.

---

### Post by jones_jj on 2006-05-20
srg0425, let's first figure out what's going on.  I am going to assume you have Samba installed correct?  Next did you add yourself as a samba user?  To do this you run the command:
** sudo smbpasswd -a <username> **
This will allow you to create a username and password for samba.  Now you will be able to access the folder you want with the newly created username and password.

Something I do from my XP machine is I map my shared network drive from my samba server.  I use the command:
** net use <drive letter>: \\<server>\<directory> /user:<server>\<username> * **
I put this command into a batch file and called it netuse.bat.  This command pretty much does the same thing as opening up windows explorer and going to tools->map network drive.

Now for running linux as a domain controller yes, you can do this, but right now it is still in beta form I believe.  The next version of Samba is suppose to allow you run your linux box like it is a windows server and create windows domains with it.  Again I believe this is still in beta form.

I hope this helps you out.

---

