---
title: "Ubuntu Client with Windows Server login script"
date: 2008-10-13
forum: Desktop Environments
---

### Post by chiefchief on 2008-10-13
I've been searching the forums and the internet, and I can't seem to find anything on the subject.

I have a Kubuntu client that is authenticating to Active Directory using [likewise-open]("http://anothersysadmin.wordpress.com/2008/04/06/howto-active-directory-authentication-in-ubuntu-804/").  So far it's worked exceptionally well, I can log in on the box as any user setup on the Windows Server 2003.  The only problem is, depending on which user, they need access to different SAMBA shares.  

Is there an easy way to setup the client box so any network user can log into it, it'll authenticate to the Active Directory, then automatically map the network drives specified in the login.bat script on the Windows server?

Thanks for any help guys!

p.s.  I'm also going to bet setting up a Linux Antivirus relay server (it saves a lot of cash compared to Symantec's insane licensing schemes), so it can be used as a BDC, or an LDAP server, if that ends up being easier.

---

### Post by chiefchief on 2008-10-14
After doing some research, I believe the answer is to ditch the likewise-open and go for a fully configured SAMBA script.

Here's an excerpt from an O'reilly book on how to make samba mount network drive: [http://oreilly.com/catalog/samba/chapter/book/ch06_06.html](http://oreilly.com/catalog/samba/chapter/book/ch06_06.html)

edit:  That's for setting up a SAMBA server.  Still in the same place as before...

---

### Post by JonLarson3 on 2012-04-26
> **chiefchief said:**
> After doing some research, I believe the answer is to ditch the likewise-open and go for a fully configured SAMBA script.

Here's an excerpt from an O'reilly book on how to make samba mount network drive: [http://oreilly.com/catalog/samba/chapter/book/ch06_06.html](http://oreilly.com/catalog/samba/chapter/book/ch06_06.html)

edit:  That's for setting up a SAMBA server.  Still in the same place as before...

I am not sure if anyone still follows this thread, but if the OP still has the script that you had wrote that would be great! We are having the same exact issue as you were experiencing. We currently have a thread here:

[http://ubuntuforums.org/showthread.php?t=1961008&page=2](http://ubuntuforums.org/showthread.php?t=1961008&page=2)

Any help would be appreciated!!!

---

### Post by henthorn1 on 2012-05-07
OUR WORKING SOLUTION
 
While this may or may not be the easiest or most stable method to mount drives, it definitely was an easy solution. We found that by going to Places > Connect to a server ... > and entering our windows share information, it mounted the specified information we had wanted. This created a link in Nautilus which when you hovered over it, it gave you an smb link. We took that link and made it into a very simple script:
 
nautilus smb://172.20.0.15/students/$USER
 
The 172.20.0.15 is the server that our student information is stored on. 
The $USER variable tells the script to mount the folder for the specific user that logged on. 
 
Then we created a simple launcher on the desktop that points to the script as well as adding the script to the startup applications. (System > Preferences > Startup Applications) This makes it run the script every time the user logs in.
 
In order to run that script for every user, we had to place the script in the home folder. Since we wanted it to be in everyones home folder so they can run the script when they log in, we had to create a default profile that gets assigned to everyone on their first login. In order to do this, we simply created a user on the machine named edstudent. We configured everything we wanted for the users to have using this profile, then went onto the root account and opened Nautilus, the file manager. We then copied the whole user folder (/home/edstudent/) into the directory /etc/skel/  Now whenever a new user logs in, the folder from /etc/skel/ gets copied to the new users home folder.
 
We would appreciate any comments on our solution or if anyone knows of an easier way of doing this. At this date we are no longer having problems with rights and access to the home folders.

---

