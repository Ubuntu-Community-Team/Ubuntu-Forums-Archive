---
title: "Network Ubuntu with windows xp"
date: 2007-07-15
forum: Dell  Ubuntu Support
---

### Post by patspick on 2007-07-15
When I click on "Patsubuntu" from Windows XP, I get a window titled Connect to PatsUbuntu with a space for a username and password and when I fil in my username and password and press "Enter" , the window box changes to another similar box with the username line changed to "PatsUbuntu\patrick" and the password line filled in.  And when I press "Enter" the box disappears for a second and repears with the same box.  Unfortunately it won't let me go into Ubuntu and share files

---

### Post by fjgaude on 2007-07-15
In Windows have you permitted your various folders to be shared?

In Ubuntu have you clicked on System/Administration/Shared Folders and set up the share name and whether read only?

Let us know how you are doing.

frank

---

### Post by patspick on 2007-07-15
Hi Frank;

Thanks for the reply.  I went into Ubuntu - System - Administration - Shared Folders.  And in that window was a folder named \home\myusername.  When I clicked "Properities" the next window that came up had a box titled "Read Only" and it was unchecked.  That settings window also had my username alongside the title "Name" and below that another line titled "Comment" with my password on that line.  Above those lines is a line tilted "Share through" and on that line is the words "Windows networks (SNB).  There is also a drop down arrow that reveals "Linux networks (NFS).  I didn't know what to do with that line so I didn't select it

---

### Post by strabes on 2007-07-17
You'll need to install the driver from fs-driver.org on all the windows machines from which you plan on reading/writing the ubuntu machine.

---

### Post by rlyounker on 2007-10-26
> strabes  	
Re: Network Ubuntu with windows xp
You'll need to install the driver from fs-driver.org on all the windows machines from which you plan on reading/writing the ubuntu machine.

I am having the same problem, but your answer about fs-driver.org seems to be only for users dual-booting Windows and Linux....  right?

Patspick and I are both having trouble accessing our ubuntu shares from our Windows machines. we get a dialog box asking for a user name and password when we try to access the ubuntu share. 

If anyone has anymore ideas please post them, I will keep playing with it, and if I get it figured out I will post it here.

Thanks for your help

-Ryan

---

### Post by rlyounker on 2007-10-26
OK I know this is an old thread but here is how I fixed the problem.

First you must install SWAT (a web interface the allows you to change your Samba config)

to do this open a terminal and type
sudo apt-get install swat

now to open SWAT open you web browser and go to 
[http://localhost:901](http://localhost:901)

SWAT will ask for the root user's user name and password

once I was in SWAT I clicked on the globals icon and the only thing I changed was



[BASE OPTIONS]
workgroup - put the name of your windows workgroup here

netbios name - this is similar to the description of your computer in windows

server string - this is the name of you computer

[SECURITY OPTIONS]
security - I changed this to "share" and this eliminated the need for my windows machines to use a username and password when accessing my ubuntu shares.



I hope this helps!
It is 2am I have pulled out all of my hair and now I am going to bed... But it was a blast and learned a lot!!!  

Good luck to all!
- Ryan

p.s. Please correct me if I am wrong on anything... it's only my 2nd day using linux.

---

### Post by dfreer on 2007-10-26
This can also help, for those of you who aren't afraid of the terminal:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_share_public_folders_with_read.2Fwrite_permissions_.28Authentication.3DNo.29)

There are several guides in that section on configuring samba, choose the one most appropriate for what you want to accomplish.

---

