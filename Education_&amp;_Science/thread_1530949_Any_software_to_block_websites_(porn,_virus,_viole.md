---
title: "Any software to block websites (porn, virus, violence) in Ubuntu"
date: 2010-07-14
forum: Education &amp; Science
---

### Post by tranduyhung on 2010-07-14
I'm sorry if this post is not eligible here. My friend asked me this question. She works in a primary school and this school is going to say goodbye to Microsoft Windows and use Ubuntu instead. And she wants to prevent her pupils from visiting bad websites like porn or violence unintentional, you know, they are just kids and those things are not good for them. In Windows there are many applications like that and my friend have been using some of them, but she tried and none of them working well with Wine. I don't know any application like that in Linux so I post here, hope someone could help me and my friend. Thank you very much!

---

### Post by earlycj5 on 2010-07-14
One could edit the hosts file to deny access to certain domains.

I'd not be surprised if a list were available, much like ad blocking host files.

---

### Post by cdnaerogeek on 2010-07-14
I just did some quick internet searching and found a program called DansGuardian.

[http://dansguardian.org]("http://dansguardian.org")

Your friend has probably never heard of it since it is not a Windows program, but it does work on Linux and Mac platforms. Might be worth a look ...

---

### Post by bubblehead74 on 2010-07-14
[http://projects.gnome.org/nanny/](http://projects.gnome.org/nanny/)

---

### Post by memilanuk on 2010-07-14
Have them use OpenDNS, and sign up for a free account to try it out.  Later it would probably be well worth the time and money for the school to get a pay account with them.  It allows fairly painless filtering and reporting that about anyone (even primary school teachers) should be able to set up.  Since it doesn't reside on the school's computers, it's completely platform agnostic.  All they have to do is set their local dhcp servers to feed the right dns server ip numbers to the clients, or use a local/internal dns forwarder and not allow any other internal machine to make dns requests outside the network.

---

### Post by tranduyhung on 2010-07-18
DansGaurdian and Nanny are awesome!
Thank you very much!

---

### Post by screwballl on 2010-07-20
I work for a company that handles internet filtering from a Christian perspective and we use a modified Dans Guardian via proxy for our customers. 

(and to prevent any obscene comments, everyone that uses our service does so voluntarily, so nothing is forced on them)

---

### Post by KIAaze on 2010-07-23
Pretty extensive list of solutions (scroll down a bit on the first post ;) ): [http://ubuntuforums.org/showthread.php?t=843510](http://ubuntuforums.org/showthread.php?t=843510)

Gnome Nanny didn't work for me last time I tried. Maybe it works better now.

---

### Post by blue2010 on 2010-07-31
Please click one of the Quick Reply icons in the  posts above to activate Quick Reply.                                        

True, but whats about this case. How would you install Dans guardian and still allow the user semi root like access. For example, you want the user to have the ability to install programs but you prevent them from deleting Dans guardian at a whim. Is this possible?;)

---

### Post by TNT1 on 2010-07-31
> **blue2010 said:**
> Please click one of the Quick Reply icons in the  posts above to activate Quick Reply.                                        

True, but whats about this case. How would you install Dans guardian and still allow the user semi root like access. For example, you want the user to have the ability to install programs but you prevent them from deleting Dans guardian at a whim. Is this possible?;)

For a school environment, I'd run a EBOX as a gateway, and do the content filtering from there. Then the individual users can still have full control over their own machines, but with a single access to the web, controlled and filtered. Plus with EBOX, you can get a full report of who went to what website, what they downloaded and so on...

---

### Post by KIAaze on 2010-07-31
> **blue2010 said:**
> 
True, but whats about this case. How would you install Dans guardian and still allow the user semi root like access. For example, you want the user to have the ability to install programs but you prevent them from deleting Dans guardian at a whim. Is this possible?;)

Like the previous poster said, you can just do the filtering on another box through which the user's PC gets access to the internet.

However it is also possible on a single PC by using /etc/sudoers.
You can create a script calling apt-get install/remove, but which purges out any reference to programs listed in a blacklist (ex: dansguardian, tinyproxy, firehol).
Then you just give the user sudo access to this script.

Help on using /etc/sudoers: [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

P.S.: Eric Duveau worked on something like that here: [http://forums.opendns.com/comments.php?DiscussionID=2942&page=1#Comment_18690](http://forums.opendns.com/comments.php?DiscussionID=2942&page=1#Comment_18690)

---

### Post by silverwink on 2010-09-30
Ive been using [http://www.timedoctor.com/2](http://www.timedoctor.com/2) . 
It uses a better procedure  than blocking social media sites because it only monitors websites during production hours. People/Employees still have the option to use it for a breather or during breaks  really . Sometimes they use it for work too . 

For me its really unnecessary to block websites.

---

### Post by KIAaze on 2010-09-30
> **silverwink said:**
> Ive been using [http://www.timedoctor.com/2](http://www.timedoctor.com/2) . 
It uses a better procedure  than blocking social media sites because it only monitors websites during production hours. People/Employees still have the option to use it for a breather or during breaks  really . Sometimes they use it for work too . 

For me its really unnecessary to block websites.

Thanks for the info (even if it looks like self-advertising...:rolleyes:). I added a link to the software here: [http://ubuntuforums.org/showthread.php?t=843510](http://ubuntuforums.org/showthread.php?t=843510)
I haven't tried it yet and don't really feel comfortable using a closed-source application tracking what I do, but since it supports GNU/Linux and is related to the filtering, time-management issues, it makes sense to add it to the list.

Note: What is the license of timedoctor? I haven't found any mention of it on the site or in the Windows installer (on Windows at the moment).

---

### Post by hsweet on 2010-09-30
And you don't have to worry a lot about virus problems if your clients are not running Windows.

---

### Post by DreamReality on 2010-10-03
Hey guys, did you decide on an appropriate type of software to block websites from? I have also heard of dansguardian, is it a proper firewall and virus protection site?

---

