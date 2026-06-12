---
title: "Evolution to Outlook?"
date: 2006-06-27
forum: Desktop Environments
---

### Post by madevries on 2006-06-27
Fearful of being ostrasized from the Linux community, I regretably have to ask this dreadful question…I can't seem to find a way to make it work, and I need to do this…I am looking for a way to convert my email from Evolution to Outlook…I am using two computers…One Ubuntu with Evolution as the mail client, and the other a Windows XP machine f (for my Wife) with Outlook 2000 as the mail client …She wants to have the email on the Windows machine until she grows more accustomed to the Ubuntu machine (and until I figure it out inside and out too of course)…She rules the roost, so what she says goes (hahaha)…But if only I knew how!  I have found a bajillion tutorials on how to transfer from Outloot to Evolution (with a detour through Mozilla first mind you…) but nothing on the reverse…help!  Anyone?  Please don't hate me, I am still going to use Ubuntu (haha).  Not sure if it matters…I am using a 64 AMD processor on the Ubuntu machine, and regular processor on the Windows machine (32 bit).

---

### Post by psycho78 on 2006-06-27
do you have an email provider with imap support? I guess that is the easiest way to migrate mails by just drag and drop them...

You could move all the mails from evolution to the imap server of your provider and then connect outlook to the imap server and copy them locally to a pst file....

---

### Post by madevries on 2006-06-27
Hey nice idea!  I sent my ISP an email explaining my situation and asking them about it...We'll see what they say - I only have about 100MB of email files that I need to transfer.  If this doesn't work or they will not cooperate, do you know of any other way to do this?

Thanks again!

md

---

### Post by psycho78 on 2006-06-27
i found something interesting: 
[http://shellter.sourceforge.net/evolution/](http://shellter.sourceforge.net/evolution/)

this is evolution for windows, maybe you can simply use this? :)
you could eventually import the mails from you linux partition using this: [http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm](http://uranus.it.swin.edu.au/~jn/linux/ext2ifs.htm)  

just an idea... i never used evolution for win..... 

Regards,
psycho78

---

### Post by madevries on 2006-06-27
I am using two separate computers for this, they are not on the same machine unfortunately, so I can't dump them over a partition.  Can't get Samba working properly either.  I can access the Windows machine from the Ubuntu machine, but I can't access the Ubuntu machine from the Windows machine - it pops up with a username and password box, and I have tried every bloody combination I know of (even my admin account) and it still doesn't allow me access…It doesn't even say I have the wrong name or passwrod or anything, it just goes away and pops up instantly again blank…That's a project for later though, heh...

---

### Post by madevries on 2006-06-29
Aahhhh yes, success!  IMAP account idea worked perfectly!  Thanks a lot for the input, so simple yet so obvious and I never would have though of it in a million years!

---

### Post by psycho78 on 2006-06-29
you're welcome, this was also a solution for me when switching from kmail to evolution.... :) 

Regards,
psycho78

---

### Post by psycho78 on 2006-06-29
if you got the possibility, leave all the messages on the imap server anyway, this way you can access the mails from both windows and linux all the time....

---

### Post by shane2peru on 2006-09-22
I don't understand how this works.  I read something similar to transfering from outlook to evolution too, but there was no solid explanation for us more simple flok!  Help.  How do I know where to find an imap thing, and how to I get my contacts there? and How do I get them into the other program?  Sorry some of us are a little less experienced.  Thanks for the help.  Also will this transfer all my contacts too with the categories, and tasks and calendar?  Thanks.

Shane

---

### Post by psycho78 on 2006-11-04
you have to have an email provider that supports imap. Check with your mail provider. You will get the server address from them. For example, I am using Arcor in germany, my imap server address is imap.arcor.de and the outgoing mail server is mail.arcor.de ... with this information you are able to setup your mailclients to use imap instead of pop3.

Regards,
Psycho78

---

### Post by hartdg on 2007-08-12
> **shane2peru said:**
> I don't understand how this works.  I read something similar to transfering from outlook to evolution too, but there was no solid explanation for us more simple flok!  Help.  How do I know where to find an imap thing, and how to I get my contacts there? and How do I get them into the other program?  Sorry some of us are a little less experienced.  Thanks for the help.  Also will this transfer all my contacts too with the categories, and tasks and calendar?  Thanks.

Shane

Have a look at:

[http://www.howtoforge.com/converting_outlook_pst_to_maildir](http://www.howtoforge.com/converting_outlook_pst_to_maildir)

It describes setting up an IMAP server on a Linux machine to facilitate migration from Outlook to Evolution, but** I think** it would work just as well the other way around. Obviously you need at least 2 PCs, one running Linux and the other running Windows.

The description appears fairly comprehensive and is broken down into small steps, but it will be intimidating to those of us who are less experienced in Linux (take a deep breath, take your time, do some research and be prepared to ask for help if you get stuck).

I've not answered your question about transfering calendar, contacts and tasks, but I'm not sure which way you want to move them (from Evolution to Outlook, or the other way around).

Dave

---

