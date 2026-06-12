---
title: "User permissions problem/question"
date: 2006-09-28
forum: Desktop Environments
---

### Post by knichel on 2006-09-28
I am running ubuntu in a lab setting.  We are using nis to create roaming login ability.  The user accounts are created on a gentoo server (not my choice).  My question is... how do I make it so the students can access a program that is normally administrator only (network-admin) without making them adminstrator level users?

Also, there is a generic user created on each workstatin as a local user.  They can use most of the programs.  When I create a user on the server, I have to add them to the /etc/group file on each workstation.  The local user on the workstation is called "student".  If I add a group called student on the server and then add all users to that group, will the permissions of "student" be inherited by all newly created users thus preventing me from having to add them manually to the group file on each computer?

I appreciate the help. I am fairly new to linux, but eager to learn. I have tried to find answers to these questinos in the forums, but all I get is configuring answers.  I am wondering if I shouuld change the server from gentoo to ubuntu to make this work?

--
Mike

---

### Post by kidders on 2006-09-28
Hi there,

I'm mostly a Gentoo user (Ubuntu is just something I've been trying for a while). Gentoo is very ... well ... hardcore! Having said that, the flavour of Linux you use doesn't really have to make much difference to the way things like this work. Ubuntu and Gentoo are happy to chat completely seamlessly to eachother.

Can I ask what kind of program you want to allow low-level users to run? There are easy ways to do such things (like using "sudo"), but whether they would be safe is a whole other question.

> will the permissions of "student" be inherited by all newly created users thus preventing me from having to add them manually to the group file on each computer
The point of using a centralised authentication mechanism (my choice would have been LDAP btw) is to avoid having to do things like this. If you find yourself having to individually update details about individual users & groups on your machines, you should re-think your strategy. Ideally, you should be able to control everything about your users from one box.

I hope that helps.

---

### Post by knichel on 2006-09-28
I am interested in letting my students use the network-admin utility to configure network devices.  We switch routers (wireless) from time to time and it is a pain for me to have to do it.

Mike

---

### Post by kidders on 2006-09-28
Hmm...

You could try granting your users access to it via sudo, but I wouldn't consider it particularly safe. If the switch-over to alternative wireless access points happens in a uniform, predictable manner however, you could easily arrange to do it centrally, from your own account.

What I'm imagining is that, for some reason, you periodically swap all your computers onto a different AP. The most secure (and most convenient) solution would be to log into a computer yourself, execute a single command, and watch it all happen. Would something like that be plausible?

---

