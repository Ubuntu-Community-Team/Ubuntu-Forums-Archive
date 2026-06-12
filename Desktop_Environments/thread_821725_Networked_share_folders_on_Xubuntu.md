---
title: "Networked share folders on Xubuntu"
date: 2008-06-07
forum: Desktop Environments
---

### Post by ed_d on 2008-06-07
OK, going to st up xubuntu on a friends laptop. Was wondering while running the live CD as to how I am going to get the data from my Ubuntu PC that I have moved from his laptop. I cannot seem to locate on the desktop where the network files is located. Is this an "add-on" or am I missing something?
Also, this is an Acer Aspire 3680-2022 with an Atheros chip set for wi-fi, so I will need a bit of assistance getting this working. Its funny, under xubuntu, it sees the card, but wont connect, but under Ubuntu, it doesn't even see the wi-fi at all....
TIA
Ed

---

### Post by psyntience on 2008-06-07
You need to set up OpenSSH server on your Ubuntu PC to share the files over a network.

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by ed_d on 2008-06-07
NO, I can already do that.
What I mean is, under ubuntu, I can, from places>network, I can see all the pcs on my network. Where is that on xubuntu?

---

### Post by wthex on 2008-06-07
You will need to set the permissions of the folder that you wish to share. 

One Method:

Right-click the folder and choose "Sharing Options".
Then check "allow other people to write in this folder".


To access another folder, create a link in side your newly "shared" folder and you will not have to set permissions on every folder you want to access.

---

### Post by ed_d on 2008-06-08
OK, Im not sure im putting this down right....

Heres what I mean.
Under ubuntu, to see other computers on the network, you go to start>places>network.
Under xubuntu, I have not found this part. I am wondering if there is a plug in or another program I need to down load that gives me this ability.

---

### Post by jlrubin on 2008-06-08
An alternative to getting shared folders working is use Xubuntu's builtin SSH server. Get SSH working on ubuntu, and then install WinSCP on the windows machine. This gives you a graphical user interface you can use to copy files back and forth between windows and ubuntu.

As you have discovered, Xubuntu doesn't come with a user interface for browsing your Windows network, or for mounting shared folders. I use pyNeighborhood for this.

Here are some links. If anybody knows of better references, please post!

Instructions for Xubuntu (may be too old..)
[http://programminglinuxblog.blogspot.com/2007/06/windows-file-sharing-samba-xubuntu.html]("http://programminglinuxblog.blogspot.com/2007/06/windows-file-sharing-samba-xubuntu.html")

pyNeighborhood home page (not specific to xubuntu)
[http://pyneighborhood.sourceforge.net/]("http://pyneighborhood.sourceforge.net/")

I think adding a windows network browser to Xubuntu should be a high priority.

---

### Post by wthex on 2008-06-08
Ok, now I understand the problem.

I have never used xffm but according to the user manual; to invoke xffm with smb support you use the xfsamaba4 at the terminal.

I would try xfsamba4 --help first then see what happens from there.

With Nautilus at the terminal it is: nautilus smb://

This takes me directly to the network without know what the name of the workgroup.

or if you know the shared folder: nautilus smb://ub-desktop/public

I suppose it would be close.

The documentation is at:

[http://www.xfce.org/documentation/4.2/manuals/xffm]("http://www.xfce.org/documentation/4.2/manuals/xffm")

---

### Post by ed_d on 2008-06-08
Perfect, thats the "plugin" I was looking for......
Oh, and the system is ubuntu Im connecting to. Im good to go now.

---

