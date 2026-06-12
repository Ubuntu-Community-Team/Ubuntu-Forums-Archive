---
title: "logged in as root/do not have permission to..."
date: 2009-05-31
forum: General Help
---

### Post by NickySix on 2009-05-31
Hi - I am brand new to Ubuntu and Linux in general so all the help documentation I am trying to read is just confusing me even more.

I have my Ubuntu machine in a Windows network.  It works perfectly from inside Ubuntu and I can always access my Window shares.  However, I cannot access anything on the Ubuntu machine from within Windows.

I opted to share a folder in Ubuntu today and it downloaded and installed Samba for me.  I opted to allow everyone to read or change files within that share.  It said "Nautilus" would set permissions for me, so I hit accept.

I can SEE the share in Windows now, which I couldn't before, but it does not give me permission to open it.  I also cannot mount the shared drive from within Ubuntu anymore unless I login as the root.  

I logged in as a root and checked the permission on the folder and it is set to allow root access only.  I click on the drop-down box to add another group and it says "You do not have permission to change the settings on this folder".  Which confuses me, becasue I thought the root account do anything.

I'm lost.  Can anyone explain what I need to do in simple terms to get this opened up on the network? Thanks.

---

### Post by Sycron on 2009-05-31
You can try this [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605) .

---

### Post by mal on 2009-05-31
NickySix,

You mentioned that you logged in as root.  However, Ubuntu normally installs with no root account activated, so you would have to create a root password to be able to log in as root.

It is generally considered bad practice to log in to a graphical desktop as root.  I suggest you have a look at this tutorial [http://www.psychocats.net/ubuntu/security]("http://www.psychocats.net/ubuntu/security") for a good introduction to this issue.

There are some other good tuturials on this site that would also make good reading for a newbie.

Regards,

Mal

---

