---
title: "Evolution 2.22.1 and Exchange LDAP"
date: 2008-05-05
forum: Desktop Environments
---

### Post by DouglasAWh on 2008-05-05
First off, as an aside, I like the old "check if already posted" better.

This is something I was working on a while back, but it got put on the back burner due to several other projects.  I am using Evolution 2.22.1 on 8.04 (thought the upgrade might fix the issue) and I can't get it to connect to the Exchange LDAP at work.  It connects with e-mail and gets my personal contacts just fine.  What do I need to do to make it get the global address list?  I know the IP address of the Exchange server as well as the fully qualified domain name.

Thanks in advance for the help.

---

### Post by DouglasAWh on 2008-05-05
Ok, this is not an Evolution issue, but related:

[quote=http://forums.msexchange.org/m_30659100/tm.htm]
The Address Book UI in Thunderbird is just clumsy. You CANNOT search an LDAP directory by simply selecting it on the left hand side and then entering your search in the "Name or Email contains" textbox. You MUST click the Advanced button to define an LDAP search. After you find your desired address(es) in LDAP, you "should" be able to copy it to your local addresses but the stupid UI only lets you look at the Properties or add it to the recipient list for a new message (by clicking the Write button).
[/quote]

That post is from 2004.  Is that still the case?

---

### Post by DouglasAWh on 2008-05-07
Ok, I'm going to no longer watch this post, but I wanted to post that the Exchange server is NOT where Active Directory is.  This was my problem.  AD sits on the domain controller.  Thunderbird still doesn't work, but that's not a big deal for me.

EDIT: I was going to mark solved, but I don't currently see that under the tread tools...

---

### Post by tomvoss on 2011-02-15
I wrote up [_detailed step-by-step instructions for connecting Evolution to Exchange 2007 Global Address List via LDAP_]("http://tomvoss.blogspot.com/2011/01/connecting-evolution-to-exchange-2007.html").

---

