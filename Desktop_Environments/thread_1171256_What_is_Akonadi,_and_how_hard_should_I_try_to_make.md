---
title: "What is Akonadi, and how hard should I try to make it work?"
date: 2009-05-27
forum: Desktop Environments
---

### Post by skullmunky on 2009-05-27
I'm enjoying many things about the KDE 4.2 desktop in Kubuntu Jaunty.  I can't get Akonadi to work, though, but before I put a lot of effort into it, I thought I'd ask - 

What is it, really, and do I really need it?

When started from the desktop, it stops on step 9, and gives an error about not being registered on D-BUS.

When started with akonadictl, I get this better error:

```

Unable to open database "Can't connect to local MySQL server through socket '/home/me/.local/share/akonadi/db_misc/mysql.socket' (2) QMYSQL: Unable to connect"          

```

---

### Post by GeneralZod on 2009-05-27
Akonadi is barely used at all at the moment, and most people won't need it.  Eventually, it will be the backend for all KDE PIM-based apps, but porting these apps over to Akonadi seems like it will take a few more releases.

---

### Post by skullmunky on 2009-05-30
Thanks, that's good to know.  So it's still sort of a preview, I guess? 

Can I disable it somehow so it won't keep trying to start up and failing when I log in?

---

### Post by indigo42 on 2009-09-01
I've got akonadi working. I appear to have it connecting to my IMAP server.

I'm setting up Kontact and was wondering if I should have seen an Akonadi listing in there somewhere for server connections. 

I love the concept of centralized PIM storage and would like to start using it. I have heard of a Kmail 2.0 but cannot find it anywhere. Is the Kontact the comes with Kubuntu desktop the latest version? I can't even find the proper repository to use.

---

### Post by monkeyKata on 2009-09-05
> **indigo42 said:**
> I've got akonadi working. I appear to have it connecting to my IMAP server.

I'm setting up Kontact and was wondering if I should have seen an Akonadi listing in there somewhere for server connections. 

I love the concept of centralized PIM storage and would like to start using it. I have heard of a Kmail 2.0 but cannot find it anywhere. Is the Kontact the comes with Kubuntu desktop the latest version? I can't even find the proper repository to use.

Hello.  I was looking at Kmail as well today and I think it's now part of Kontact.  I think it combines the mail, calendar, and organizer apps.  Right?

I'm starting to dig some kde apps... anyone checked out Kword?

---

### Post by monkeyKata on 2009-09-05
oh, and the ppa to get the latest KDE 4.3 stuff should be this one:

[https://launchpad.net/~kubuntu-ppa/+archive/backports](https://launchpad.net/~kubuntu-ppa/+archive/backports)

---

### Post by indigo42 on 2009-09-06
Yes,
KMail is bundled with Kontact now. I have given up looking for a while and have turned off Akonadi for now.

I was getting some weird connectivity errors with KMail while Akonadi was running, and sometimes my mail would come in as already 'read'. I'm sure it was beacuase Akonadi was connected to the email server at the same time.
These issues stopped after I shut it down.

So the question is. What if anything, can we do with Akonadi now?

Thanks!

---

