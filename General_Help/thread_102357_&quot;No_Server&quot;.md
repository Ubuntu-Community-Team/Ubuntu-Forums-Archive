---
title: "&quot;No Server&quot;"
date: 2005-12-11
forum: General Help
---

### Post by JoshHendo on 2005-12-11
> 
No servers were defines in the configuration file and XDMCP was disables. This can only be a configuration error. GDM has started a single server for you. YOu should log in and fix the configuration. Note that automatic and timed loggin are disabled.


That is a error I get now when I log out of my account (and I am assuming that it is also when I turn it on). When trying to set up some themes for the login page, I think i accidently deleted something related to this, and I know where I deleted it, I just don't know how to get it back :/

---

### Post by ppmt on 2006-01-12
Hi,

I have the same problem for a few days now. I don't remember doing anything special. The only things I can think of is that before I updated the laptop to the latest kernel I didn't have it.

I can't however say for sure it is related

/Philippe

---

### Post by ppmt on 2006-01-17
Well obviously me and Josh must be the only one to have that problem :???: 

Anyway a friend of mine help me troubleshooting it and it is fixed now

The fix was to edit the file gdm.conf in /etc/gdm

There is a section called [servers] in mine I had no server selected. They were commented out

So I removed the # in front of the line that was saying 
#1=Standard 

and after a gdm restart it was all working

After that I looked on another computer running Ubuntu and instead of 1=Standard it is 0=Standard

According to the comments in the file it should be 0 but as both seem to work I haven't question myself too much

I wonder what did that changes in the file because I certainly didn't do it

/Philippe

---

### Post by mishranurag on 2006-01-19
I am having the same errors now on my computer. Waiting for a response to this post. Anurag

---

### Post by ppmt on 2006-01-20
Hi,

[QUOTE=mishranurag]I am having the same errors now on my computer. Waiting for a response to this post. Anurag[/QUOTE]

Have you tried what I did?

/Philippe

---

### Post by mishranurag on 2006-01-22
Thank God, UBUNTU forum is back.
I had some other problems too (UBUNTU GDM didn't load after updating kernel and stuff), and I installed kubuntu-desktop. System seems to be working fine now and I don see that problem now. Lets wait for the issue to reappear.:)
Anurag

---

### Post by kalata on 2006-05-08
Thanks, fixed the problem.

---

