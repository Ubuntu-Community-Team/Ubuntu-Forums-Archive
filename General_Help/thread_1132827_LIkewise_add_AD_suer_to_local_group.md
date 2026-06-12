---
title: "LIkewise add AD suer to local group"
date: 2009-04-22
forum: General Help
---

### Post by bpickel on 2009-04-22
Alright so i hope someone has seen this before. I have searched and tried what I found but no luck. I have joined my Ubuntu machine to my Windows domain at work and have successfully logged in with my domain account. 

 I can sudo but if I try and system configuration I get "you are not allowed to access the system configuration" . i am fairly certain that this is a problem with local group membership. I have tried editing /etc/group to add my domain account to local groups but I cannot get it to work.

I have tried addin the domain user to the same groups as my standard ubuntu user but no luck. I have tried adding in the following formats 

DOMAIN\User

DOMAIN+User

[EMAIL="user@domain.net"]user@domain.net[/EMAIL]

None of these will work.  Can anyone help  ?

---

### Post by StuartN on 2009-04-22
Have you set all the user privileges for the Windows domain user in System->Administration->Users and Groups? And checked that this user is a member of the admin group?

---

### Post by bpickel on 2009-04-22
My windows domain user does not show there. i have add it via /etc/group but If I try and launch say Users and Groups, I get "you are not allowed to access the system configuration"

---

### Post by StuartN on 2009-04-22
> **bpickel said:**
> I get "you are not allowed to access the system configuration"

I would log in with the user name that you set up Ubuntu with and add the new Windows domain user from the administration tools rather than hand-editing files. That primary user should have access permissions to administer users. If you do hand-edit then there should be a line somewhere with admin:x:<group id> to which I guess you add :<new user> if there are none or ,<new user> to append to an existing list of users.

---

### Post by bpickel on 2009-04-23
Problem solved. It took a couple of things. 

Add the line

lwopen:name_map = /etc/samba/map.txt

to /etc/samba/lwiauthd.conf.

Where map.txt is a file I created in /etc/samba with the following content.

user1 = DOMAIN\domainuser

This will cause likewise to use user1 to log in instead of DOMAIN\domainuser

 This will also allow the user1 user account to be added to the admin, etc group. The is most easily done by editing the /etc/group file and simply adding user1 to every group that the user Ubuntu created is in using a comma to separate ( admin:000: ubuntuuser,user1).

 You then need to add      %DOMAIN\\domain^admins ALL=(ALL) ALL

to your /etc/sudoers file.  If you are not a member of domain admins in AD substitute domain^users for domain^admins


Lastly, you will need to open Synaptic and reinstall all packages that begin with dbus and are ALREADY INSTALLED.  


The problem is that the dbus code sees the \ in the DOMAIN\domainuser combo as a kill flag. The reinstall takes care of that.  I now am able to login with my AD creds and access resources, as well as, perform all actions in Linux.

---

### Post by Chad_Hurley on 2009-05-21
I am looking for this same solution but for likewise-open5.  I've been banging my head on it for 2 weeks now.  Does anyone know what the configuration options are for lsassd.conf?

---

### Post by Chad_Hurley on 2009-05-27
OK. I have solved my own question.  For anyone interested:

edit /etc/likewise-open5/lsassd.conf

Uncomment the following line:
    assume-default-domain = yes

Now add your domain <UserName> to sudoers and whatever groups you need in: /etc/group

Reboot. (This is the only way I could get the new privs working.  Simply restarting lsassd or logging out/in didn't work for me.)


VOILA!

Now instead of logging in as <DOMAIN>\<UserName> simply login with <UserName>.

---

