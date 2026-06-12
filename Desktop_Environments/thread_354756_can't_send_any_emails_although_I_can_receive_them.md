---
title: "can't send any emails although I can receive them"
date: 2007-02-06
forum: Desktop Environments
---

### Post by Efwis on 2007-02-06
Hi guys,

Hopefully someone can help me out here. I have a lot of stuff on here that I don't want to have to image and try to replace just to re-install Ubuntu.

I'm using 6.06 with Gnome, I recently installed a local server on it, and without thinking about it I used dovecot as an email server. I don't know why since this won't be hooked up to the net as a server so I really don't need the email server part.

anyway, I removed dovecot after unsuccessfully installing it, and I can't send any emails with any email program. I get the same error on all email system, I would prefer to stay with evolution since I prefer it over thunderbird.

Here is the error I get when I try to send an email. I replaced the email address with the [email]user@domain.com[/email].
> Error while performing operation.

RCPT TO <user@domain.com> failed: Requested action not taken: mailbox unavailable
When I run "iptables -L" I get the following output,
> Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

does this mean my iptables are screwed up??

I would rather fix this instead of re-installing Ubuntu so any help is appreciated.

---

### Post by Efwis on 2007-02-06
well, I needed this fixed fairly quickly, so I have managed to backup my Hdd and have reinstalled Ubuntu. Now i have to reconfigure my printer, and reinstall my server files and other programs I had to back up.

---

### Post by rajan on 2007-02-10
did this fix the problem? i am having the same problem, although i can actually send emails to accounts on the local server (my university server), i can't send any emails outside of this server. i get the same exact error when i try. 

and so did this guy:
[http://lists.ximian.com/pipermail/users/2003-March/008801.html](http://lists.ximian.com/pipermail/users/2003-March/008801.html)

but the solution that is proposed (i think) is found here;
[http://www.novell.com/support/search.do?cmd=displayKC&docType=kc&externalId=ximian438&sliceId=&dialogID=26676508&stateId=0%200%2026678926](http://www.novell.com/support/search.do?cmd=displayKC&docType=kc&externalId=ximian438&sliceId=&dialogID=26676508&stateId=0%200%2026678926)
and doesn't fix my problem.

this guy also had the same problem:
[http://www.clarkconnect.com/forums/showflat.php?Cat=3&Board=email&Number=76396&Searchpage=1&Main=76386&Words=+Oceria&topic=&Search=true](http://www.clarkconnect.com/forums/showflat.php?Cat=3&Board=email&Number=76396&Searchpage=1&Main=76386&Words=+Oceria&topic=&Search=true)
but again, no real solution.

this last post makes me think it's a ubuntu problem. if i find a solution, i'll post it back on here later.

---

### Post by rajan on 2007-02-10
these are some people having the same problem:

[http://www.ubuntuforums.org/showthread.php?t=338964](http://www.ubuntuforums.org/showthread.php?t=338964)

[http://www.ubuntuforums.org/showthread.php?t=153134](http://www.ubuntuforums.org/showthread.php?t=153134)

and a bunch of other people have too.

so i think it might be a problem with the particular SMTP server you are using. my university's web site says that you have to put the ISP's SMTP server instead of the university's server, even though i want to send email from my university account. i'm not sure how to do this and i'll have to call my ISP to figure out what their SMTP server is called. if i get this working, then i'll post back on here. if i haven't posted back on here, it's because i haven't figured it out and i'd appreciate a PM. TIA.

---

### Post by rajan on 2007-02-10
YES! problem solved! changing the outgoing SMTP server to that of my ISP instead of my university's actually worked. so basically i just had to put 

smtp.comcast.net

in for the outgoing mail server instead of the server name that i had in there before, which was my university server. i assume this is because the outgoing server does not really do anything besides forward the mail on and thus there is no reason to go through one particular one. whereas the incoming server has to authenticate the user and then pass the information on. if you know the answer, correct me please. but for now,

:guitar:

---

