---
title: "An idea to reduce the load on ubuntuforums server"
date: 2009-04-21
forum: Forum Feedback &amp; Help
---

### Post by coffeecat on 2009-04-21
The forums have been running much better for the last few weeks, but I have an idea to help them run even better. Simply request the devs to modify the dpkg package for all supported versions, so that instead of this error message:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.... it puts out this one:

> E: dpkg was interrupted, you must open a terminal and run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.That should reduce the load quite significantly.

:wink:

---

### Post by Joeb454 on 2009-04-21
I totally agree, or adding that the command needs to be run as root :)

The only way to get this added though would be to file a bug report of some sort I believe. I'm not 100% sure of the best way to get it done, as it isn't technically a bug...

---

### Post by Elfy on 2009-04-21
I believe that jaunty has produced this magic - I have vague memories of it telling me to sudo dpkg --configure -a

---

### Post by sisco311 on 2009-04-21
> **forestpixie said:**
> I believe that jaunty has produced this magic - I have vague memories of it telling me to sudo dpkg --configure -a

Yes, you are right.
This is the error message in Jaunty:
> E: Sub-process returned an error code
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

:evil: 

You update/upgrade/install the packages as root. The error message is for the admin/root user. It's evident that you have to run the command as root. 

:evil:

---

### Post by Joeb454 on 2009-04-21
> **sisco311 said:**
> The error message is for the admin/root user. It's evident that you have to run the command as root.

But while that's the case, how many people will have single user Ubuntu systems, therefore BE the admin user themselves?

I think mentioning sudo is just one of those things that might make peoples lives easier :)

---

### Post by coffeecat on 2009-04-21
> **sisco311 said:**
> You update/upgrade/install the packages as root. The error message is for the admin/root user. It's evident that you have to run the command as root. Mentioning sudo in the error message is redundant. 

You miss the point of the suggestion, which I only meant half-seriously anyway, but I'm glad that greater minds than I had already thought of it. :wink:

 We get far too many support requests from newcomers who know nothing about root or sudo and who cannot understand why 'dpkg --configure -a' won't work. Adding sudo to the message is merely being helpful. If experienced users are offended by it, that's their problem.  

> **forestpixie said:**
> I believe that jaunty has produced this magic - I have vague memories of it telling me to sudo dpkg --configure -a

In which case I need to suggest another idea. :p How about when you try to enable the proposed repository, you get this message?

> Do you really want to break your system, or are you an experienced user helping with quality assurance?:wink:

---

### Post by Elfy on 2009-04-21
I believe that when you do that your screen implodes.

---

### Post by bapoumba on 2009-04-21
For dpkg, please look here :)
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/52697](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/52697)
(not commenting the -proposed repos, [https://help.ubuntu.com/community/UbuntuUpdates](https://help.ubuntu.com/community/UbuntuUpdates)).

---

### Post by sisco311 on 2009-04-21
> **coffeecat said:**
> 
In which case I need to suggest another idea. :p How about when you try to enable the proposed repository, you get this message?

:wink:

Pop up messages/warnings are "dangerous". 

It's easy to fall into the bad habit of clicking Next... Next... I Agree ... Allow ... OK ... without thinking.

It's hard to find a good balance between security and usability.

---

