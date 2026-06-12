---
title: "oppertunity - university deployment"
date: 2009-04-14
forum: Education &amp; Science
---

### Post by enduser000 on 2009-04-14
Hello,
     So I've been using ubuntu as my main for awhile now, and have successfully gotten at least one other person to use it as his main, and most of my other friends at least want to try it, so we're on our way.  I found out that I'll have the chance to draft up a proposal on bringing ubuntu to our college.  This sounds like a great idea but I find myself thinking about what I still don't know.  These are my questions:

How can you do a network-type login? Whenever we login in osx or windows (xp or vista) it loads our network drives and saves a few settings (not many) locally.  How ca I do this in ubuntu?

How easy is it to lock down ubuntu? No terminal, no extra applications, no ability to see or mount the drives, but still enough access to run basic applications and get work done.

Any other ideas?  Anyone that's already done this that has anything to say would be greatly appreciated, and anyone that has any ideas in the deployment or possible use of ubuntu in a university is encouraged to speak so I can make this presentation better.

My goal is to make this look like a very little amount of work for the administrators, and also not presenting a large learning curve for the users.  I think this is a great opportunity for my school because exposure to more than one OS will help all computer type students and maybe show everyone the value of free software. Post Post Post! let's get this thing rolling, I'd like to make a slideshow, maybe some screen recordings (tutorials), and a paper.  Any ideas are great!

enduser

---

### Post by Joeb454 on 2009-04-14
I'm not sure about network logins, though I can almost guarantee they'll be supported.

As for locking things down, that would probably be done in conjunction with the network login and groups. E.g. you can deny the students group access to terminal and sudo, so they couldn't do anything to damage the system then :)

I hope that gives you a basic start :)

---

### Post by nateperson on 2009-04-14
Couple of things that answerer's your first question.

Centralized account management can be set up with NIS
[http://www.linux-nis.org/](http://www.linux-nis.org/)
[https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo)

Interoperability with current systems will probably require Samba
[http://www.samba.org](http://www.samba.org)
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

and Open LDAP
[http://www.openldap.org/](http://www.openldap.org/)
[https://help.ubuntu.com/community/LDAP-Samba_PDC_(for_Linux_and_Windows](https://help.ubuntu.com/community/LDAP-Samba_PDC_(for_Linux_and_Windows))

---

### Post by enduser000 on 2009-04-14
They already use samba (to mount my school storage I install 'smbfs' and mount a cifs partition), so that's already ready.  I just need to find out how to automatically mount the students' drives' when they log in,

enduser

---

### Post by nateperson on 2009-04-15
I auto mounting of network drives can be accomplished with NIS.
[http://penguin.triumf.ca/recipes/nis-auto/index.html](http://penguin.triumf.ca/recipes/nis-auto/index.html)
[http://ubuntuforums.org/showthread.php?t=297233](http://ubuntuforums.org/showthread.php?t=297233)

---

### Post by hsweet on 2009-04-15
You might check out the KDE kiosk mode. 

+ LTSP which will turn the computers into essentially dumb terminals.  All config happens on the server etc..  The Edubuntu project uses this.  If you use LTSP and configure Kiosk mode you have an instant lab.

I can still boot my machines to windows.  It can be an easy way to transition.

---

### Post by Bucky Ball on 2009-04-15
What you might want to do is head to the IT department and see if you can find someone there that knows Unix. The college may be running a Unix server or two already. If there is someone there, take them out to dinner, buy them a beer, whatever it takes to get them onside. With any luck they will be able to help answer your current questions and the ones that will arise in the future. At least they can help you along the way and two heads are better than one and they know the current system and requirements in detail.

If you can get as many of the IT personnel onside as possible, it has to be a good thing, not just for you but for the Linux community in general. :)

Great opportunity, my university is in a Microsoft financial fantasy world so ya lucky. I find it extremely frustrating. A desktop excellence program that plans to replace all XP with Vista! Gawd help us ...

Good luck.

---

### Post by nateperson on 2009-04-15
I'm going to agree with Bucky Ball,  

Talking with your IT department and having them in your corner, and knowing what they currently have and don't have and currently can and cannnot do will go a long way.

---

