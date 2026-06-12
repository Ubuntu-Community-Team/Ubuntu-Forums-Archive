---
title: "Join a Windows Domain but Continue to Log On Locally?"
date: 2006-07-27
forum: Desktop Environments
---

### Post by Video Toaster on 2006-07-27
Hi everyone,

Earlier this week I returned to my school TV station's Kubuntu computer and tried to install the latest version of Amarok (I use it as a music computer for our morning broadcast).  However, I was unable to access the Internet.  I found the IT person for my school and asked what to do.

It turns out that the school district got new web filtering software that intercepts external web traffic, replacing their old ISA server.  However, not only does the filter require a username and password, but it also requires that the computer in question be part of the domain.

1.  How can I get past the domain requirement?  Can I join the domain using "net rpc join -D MYDOMAIN -U administrator" and not edit any config files so that I can preserve local logons instead of having to log onto the domain?  This is a general membership computer and I don't want to have to deal with individual domain logons.

2.  How would I go about setting up APT for the password requirement when there's no proxy server to associate the username and password with?

3.  Whatever the solution is (assuming there is in fact a solution), would it also work with Mac OSX Panther?  The TV station has three Macs that also need to go on the Internet.

Thanks in advance!

---

### Post by Video Toaster on 2006-08-14
*bump*

Any ideas?

---

### Post by cwaldbieser on 2006-08-14
> **Video Toaster said:**
> Hi everyone,

Earlier this week I returned to my school TV station's Kubuntu computer and tried to install the latest version of Amarok (I use it as a music computer for our morning broadcast).  However, I was unable to access the Internet.  I found the IT person for my school and asked what to do.

It turns out that the school district got new web filtering software that intercepts external web traffic, replacing their old ISA server.  However, not only does the filter require a username and password, but it also requires that the computer in question be part of the domain.

1.  How can I get past the domain requirement?  Can I join the domain using "net rpc join -D MYDOMAIN -U administrator" and not edit any config files so that I can preserve local logons instead of having to log onto the domain?  This is a general membership computer and I don't want to have to deal with individual domain logons.

2.  How would I go about setting up APT for the password requirement when there's no proxy server to associate the username and password with?

3.  Whatever the solution is (assuming there is in fact a solution), would it also work with Mac OSX Panther?  The TV station has three Macs that also need to go on the Internet.

Thanks in advance!

How exactly does the proxy determine whether your computer is part of the domain?

---

### Post by Video Toaster on 2006-08-16
> **cwaldbieser said:**
> How exactly does the proxy determine whether your computer is part of the domain?
Since I do not have anything to do with the setup of the new proxy, I can only guess, but it seems that the new proxy is connected to the school domain and checks the Active Directory list to see if that computer name is listed.  However, I have not been able to check this yet.  If it is just checking Active Directory, would "net rpc join -D MYDOMAIN -U administrator" add the current Linux computer to the list and fix the problem?

---

### Post by cwaldbieser on 2006-08-17
> **Video Toaster said:**
> Since I do not have anything to do with the setup of the new proxy, I can only guess, but it seems that the new proxy is connected to the school domain and checks the Active Directory list to see if that computer name is listed.  However, I have not been able to check this yet.  If it is just checking Active Directory, would "net rpc join -D MYDOMAIN -U administrator" add the current Linux computer to the list and fix the problem?
I am not sure about your net command-- I guess you could just try it and see if it works.  Couldn't one of the directory admins just add your computer name to the directory?  Or am I oversimplifying the situation?

---

### Post by Video Toaster on 2006-08-17
> **cwaldbieser said:**
> I am not sure about your net command-- I guess you could just try it and see if it works.  Couldn't one of the directory admins just add your computer name to the directory?  Or am I oversimplifying the situation?
That's what I would have tried to do, but the school system administrator I talked to claims you can only add computers to the domain by going to the local workstation and joining the computer to the domain - you apparently cannot just go into Active Directory and add a computer name (or if you can, the person I talked to doesn't know how).

I got that command I quoted from the end of a list of instructions for being able to log onto the domain from Ubuntu instead of logging on locally.  Since I don't want to log onto the domain, I was wondering if running only that command would work.  I'd love to try it, but I wasn't able to find the sysadmin for my school the last two days.

---

### Post by cwaldbieser on 2006-08-19
> **Video Toaster said:**
> That's what I would have tried to do, but the school system administrator I talked to claims you can only add computers to the domain by going to the local workstation and joining the computer to the domain - you apparently cannot just go into Active Directory and add a computer name (or if you can, the person I talked to doesn't know how).

I got that command I quoted from the end of a list of instructions for being able to log onto the domain from Ubuntu instead of logging on locally.  Since I don't want to log onto the domain, I was wondering if running only that command would work.  I'd love to try it, but I wasn't able to find the sysadmin for my school the last two days.

Give him this link:
[http://support.microsoft.com/default.aspx?scid=kb;en-us;320187]("http://support.microsoft.com/default.aspx?scid=kb;en-us;320187")
It seems to explain how to add a computer name to the directory without having to have an actual machine join the domain.

---

