---
title: "Evolution never fetches GMail"
date: 2009-03-01
forum: General Help
---

### Post by joey-elijah on 2009-03-01
Evolution is configured correctly for GMail, however even though i 'know' there are unread message on the server it fails to get them. It's not a wrong password or anything like that as it logs in fine - it just reports there are no messages to fetch.

Hotmail works fine, but GMail is my primary e-mail address. 

I'm currently using Spicebird, but i'd prefer to use Evolution because of Gnome intergration.

---

### Post by joey-elijah on 2009-03-02
deleted and reinstalled but still the same issue. Is this a bug?

---

### Post by abhilashm86 on 2009-03-02
> **joey-elijah said:**
> deleted and reinstalled but still the same issue. Is this a bug?

i don't think it is a bug, usually gmail has lot of security, so have you enabled pop forwarding, because it will be initially blocked from GMAIL,
You will find this in gmail: Settings - Forwarding and POP

---

### Post by joey-elijah on 2009-03-02
> **abhilashm86 said:**
> i don't think it is a bug, usually gmail has lot of security, so have you enabled pop forwarding, because it will be initially blocked from GMAIL,
You will find this in gmail: Settings - Forwarding and POP

Yes i have enabled pop forwarding as i am able to get my gmail in spicebird (as i mentioned in the first post).

I also can get my gmail fine in 'Mail' in OS X and in Spicebird on Windows 7.

---

### Post by theDaveTheRave on 2009-03-02
joey-elijah

I had a similar problem with gmail and evolution.

as abhilashm86 says you need to ensure that the settings in gmail are correct (mine come down to evolution just fine).

You also need to have the port configured correctly etc.

In my system gmail settings are as follows for evolution

Receiving:

Server type:  IMAP
server: imap.google.com
security: SSL Encryption

Obviously change your username etc as required.

Outgoing.

server type: SMTP
server: smtp.googlemail.com:587

again, personalise as required.

then check to see if you can at least send to yourself!

In GMAIL settings, on the forwarding and POP/IMAP option ...

Forwarding - change to your preferences

POP download: no selections made in this section.

IMAP access. select to enable IMAP.

With luck that should get you going.

David

---

### Post by joey-elijah on 2009-03-02
Bizarrely it seems to be working now.. i didn't do anything...

---

### Post by theDaveTheRave on 2009-03-02
Excelent..

I much prefere that to my "normal" experience of turning on the laptop in the morning and finding that my wireless has broken, but   " I haven't changed anything" (normally due to kernel updates!).

We'll mark that one up to another feather in the cap of Linux, when have you ever heard of windows suddenly doing what it is supposed to !? :P

David

---

