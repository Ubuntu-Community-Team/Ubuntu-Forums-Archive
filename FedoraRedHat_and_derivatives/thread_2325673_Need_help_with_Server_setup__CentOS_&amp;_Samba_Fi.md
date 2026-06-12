---
title: "Need help with Server setup : CentOS &amp; Samba File system + Windows server 2012"
date: 2016-05-24
forum: Fedora/RedHat and derivatives
---

### Post by Clinton_Baptista on 2016-05-24
Hello everyone,

This is my first post in the forum.

I've been handed a task of managing a school lab setup as the Admin no longer assists the management.
The computer lab setup initially had 20 thin clients linked to an IBM server.

The base OS installed is CentOS 6.4 over which they have Windows Server 2012 running and they also have Samba File server.
So users were created via Active Directory and added to a group.
The same users were then created in Webmin, Unix users I mean and added to a group and then they were converted to Samba Users.
This is how the mapping was done as I understand.

So there students logged in through their accounts (Windows interface) and used the programs installed on the server and the data was correctly saved for next login via any client as such.

Since the new syllabus demands them to use desktop based programs, this year the setup has changed to 20 desktop systems running windows 7 all connected via a domain to the server.

I have followed the same very steps but I am not able to get the data saved on the server or synced as the desktops basically have local storage and I cant somehow understand the folder permissions I need to set for a shared drive if thats the soluton.

What am I missing here?

I would be grateful If you people can be patient enough to atleast guide me with material if not assist me.

Do let me now if you need any additional info so that I can fetch the details.

Any help is appreciated.

Regards,
Clinton

---

### Post by howefield on 2016-05-24
Thread moved to the "*Fedora/RedHat and derivatives*" forum.

---

### Post by QIII on 2016-05-24
The Cafe is not for support requests.  We are happy to entertain support requests regarding other operating systems, but the Ubuntu Forums primary purpose is to provide support for Ubuntu and official flavors.

Hopefully you'll get a good answer here.

Cheers!

Ninja'd, I see.

---

### Post by Clinton_Baptista on 2016-05-24
Thanks guys!
Appreciate the support already.

Fingers crossed!

---

### Post by oldos2er on 2016-05-24
[https://www.centos.org/forums/viewforum.php?f=3&sid=6ad7ed38a9b47087240cd3fb432efc34](https://www.centos.org/forums/viewforum.php?f=3&sid=6ad7ed38a9b47087240cd3fb432efc34)

---

### Post by Clinton_Baptista on 2016-05-25
A true roaming profile is what I wish to achieve and I already had a folder redirection in mind but I'm clueless how to go about setting it up.

Also, in thin clients when a user logged into his windows account, no one could login to the same account.

With the current setup, a user can login to his account at multiple places. 
I want to get it switched back to the old mechanism.

When I did create Unix users, I entered a path for the home directory, how do I get that folder show up in Windows account or did I miss a link somewhere? 
Also, is that the unique folder for the Unix user account which can be shared across 20desktops?

Can you please guide me in getting this done?

Regards,
Clinton.

---

### Post by Clinton_Baptista on 2016-05-26
Any suggestions people?

---

