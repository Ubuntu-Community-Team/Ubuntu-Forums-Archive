---
title: "Firefox cannot display html file form a networkshare"
date: 2009-08-11
forum: Desktop Environments
---

### Post by Shadowlord1 on 2009-08-11
Hoi,

I got here a problem. I am able to open a local html file form the desktop but when I open the same file form a windows netwerkshare it displays a white page. 

When firefox opens it create a tab that is called Untitled and the navigation adress tool bar isnt filled.

I am using Ubuntu 8.04 with firefox 3.0.13.

I also got a Unbuntu 6.10 with firefox 2.0.0.1 witch does not give any problems on the same html file and netwerkshare.

Does anyone got a idea to sove this problem?

Greetings,

Bryan 
Title Ubuntu noob

---

### Post by DaithiF on 2009-08-11
Hi, so are you opening it via a file:// type link?

if so, it could be a firefox security setting which prevents the opening of links to these so-called local files.  see [http://kb.mozillazine.org/Links_to_local_pages_don%27t_work](http://kb.mozillazine.org/Links_to_local_pages_don%27t_work) for more info.

---

### Post by Shadowlord1 on 2009-08-11
The link that you send describe the error i am getting.

I am trying to disable it with no result. I have installed the no-script plug in and try to follow the instruction with no result. Plus i am unable to follow all the instruction of 
**Disabling the Security Check.**

The NoScript Options ("Advanced ->  Trusted -> "Allow local links) had no effect.

This is the way i am opening the file.

Places > Network > Windows Network > then my company name > then the sever where the file is at > c$ > Temp > and then dubble klik on schermen.html.

---

### Post by DaithiF on 2009-08-11
hmm, from what you have described I'm not sure this is the issue actually.  The link I provided referes to the situation where a webpage contains links to file:// type urls on different machines or drives.  In these cases, access to these is blocked by firefox unless you override the behaviour as described.

However, if you are navigating directly to a file in nautilus via the places -> etc. menus, and then click to open a file from there with Firefox, then that should just work, as long as Firefox is able to navigate that path.  Sorry, I'm out of ideas :(

---

