---
title: "User logins, mounted folders, domain controller?"
date: 2006-10-05
forum: Desktop Environments
---

### Post by chocolatetoothpaste on 2006-10-05
Hey all,
  I hope my title matches my problem, so no one gets confused.  I have a big question that I can't seem to find an answer for.  So I will try to explain this as best as I can.
  I want to set up a small network in my home, and then a slightly larger one in my office.  I want this network to mimick the type of network you sometimes see in schools.  That is to say, I want to have centralized logins, and when a user logs in successfully, they have a folder mounted or mapped to their computer.  This behaviour should be to the effect that the user can just save all their files in that mapped or mounted folder, and no matter what computer they login in on it is available to them.  Bear in mind, this network will be mixed, meaning Linux and Windows machines.  It seems to me that this is almost a thin server type of setup, but that is not the direction I want to go, since there will be Windows machines.  So here are my following questions:

1.  Is this type of system called a domain/domain controller?  If not, what is it called?
2. Are the logins actually centralized, or are they local and synchronized?  What I mean is, are my usernames/passwords stored on the server, or are they stored on the local machines, and then matched up with the server to get mapped folders, etc.?
3. Where can I read up on this topic, and get some help setting it up?

  I found a website for a tool called [SADMS](http://sadms.sourceforge.net/), but I am not sure if this is the right tool for the task I want to accomplish.  This website talked about PAM authentication, WinBind and some other things.  I certainly want to avoid installing 3 services that do the exact same thing, that is why I am asking for a little direction in finding a solution to this issue.
  If you think you might be able to help but my babbling doesn't make sense, ask me question and I will do my best to clarify.
  Thanks Ubuntu Community!

---

### Post by crokett on 2006-10-05
> **chocolatetoothpaste said:**
> 
1.  Is this type of system called a domain/domain controller?  If not, what is it called?
2. Are the logins actually centralized, or are they local and synchronized?  What I mean is, are my usernames/passwords stored on the server, or are they stored on the local machines, and then matched up with the server to get mapped folders, etc.?
3. Where can I read up on this topic, and get some help setting it up?


1.  Depends on who you are talking to.  In the windows world it would be domains and a domain controller.  
2.  Both.  For the windows machines you are logging into both the  local machine and the domain controller.  However the login scripts, etc all sit on the domain controller and the user acount has to be authorized to access the domain
3.  If your server is a Linux machine then  you want Samba Server:

[http://www.howtoforge.com/samba_setup_ubuntu_5.10](http://www.howtoforge.com/samba_setup_ubuntu_5.10)
[www.samba.org](www.samba.org)

    If your server is a windows machine, then google smbclient for linux 

also google samba.  There are lots of how-tos.

---

### Post by chocolatetoothpaste on 2006-10-05
The server is a linux machine.  I am quite familiar with samba; I have used it a lot in the past.
  I want to use a linux machine as like a file server, but I don't want to have local logins, so I am not setting up 10 user accounts on ten machines each (100 setups! ouch).  Is this possible on linux and windows user machines?

---

### Post by randomnumber on 2006-12-18
> **chocolatetoothpaste said:**
> The server is a linux machine.  I am quite familiar with samba; I have used it a lot in the past.
  I want to use a linux machine as like a file server, but I don't want to have local logins, so I am not setting up 10 user accounts on ten machines each (100 setups! ouch).  Is this possible on linux and windows user machines?

I want to know how to do this too but I also want local and remote logins. This would be nice if you had a laptop that did not always have access to the local network. Updating the file afterwards may be a problem. I find this to be very interesting and I believe that the future sees this type of networking expanding greatly, even into the homes. One benefit of this in the home is backing up data so that upgrading software/OS does not delete your files or settings.

---

