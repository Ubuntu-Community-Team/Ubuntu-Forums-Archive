---
title: "kmail using addressbook - &quot;Recent addresses problem&quot;"
date: 2005-12-10
forum: General Help
---

### Post by daller on 2005-12-10
Hi There,

I have a problem with kmail.

I have a large addressbook, and I have some problems with it!

When I open the "e-mail dialog" and press "Choose..." (Right of the "To"-field!)

Here I see all my contacts + recent addresses (the onces i've written to, but haven't added!) - How do I edit those?

I can choose "resource" under "addressbook" (instead of all) - But I'd really appreciate to be able to edit the recent ones! (Or make it choose "resource" per default - Like kabc)

Thanks...

---

### Post by mlomker on 2005-12-11
That's a good question.  There's a pick for Tools, Address Book but it doesn't do anything when I click on it.  

I know that you're running KDE3.5, so not sure if it's the same or not.  I'm going to upgrade again in a minute and see.

---

### Post by limit223 on 2005-12-11
I don't think it is implemented in Kmail to do this yet.
Take a look at: Modifying KMail distribution list here 

[http://lists.kde.org/?l=kdepim-users&w=2&r=1&s=recipient&q=b](http://lists.kde.org/?l=kdepim-users&w=2&r=1&s=recipient&q=b)

although you may edit manually each of your contacts

---

### Post by daller on 2005-12-12
There must be a way to edit the "recent recipients"!

Any ideas?

...they are not located in "~/.kde/share/apps/kabc/std.vcf"

---

### Post by limit223 on 2005-12-12
This is the most recent KDE mail list regarding this settings and if you have read all the replies of it you'll find out that one of KDE developer replied:

"Damn, I forgot to mention that this only happens when KAddressbook is
opened from within Kontact. Ther's already a bug report stating that
this is fixed for KDE 3.5. (I'm using 3.4.1):
[https://bugs.kde.org/show_bug.cgi?id=102094](https://bugs.kde.org/show_bug.cgi?id=102094)

Nontheless I definitely find this a pretty complicated and
unconsistent way of editing distribution list. Maybe this is some area
for openusability people to give some suggestions on how to enhance
usability...

cheers,
Till"


If you find a way to do this setting I'd be interested as well to know it...:KS

---

### Post by mlomker on 2005-12-12
[QUOTE=daller]There must be a way to edit the "recent recipients"!

Any ideas?
[/QUOTE]

It's odd...I greped my entire ~/ and couldn't find where it's being stored.  Regarding limit223's suggestion...kmail and kontact aren't the same, so I don't think that's it.  

The problem is the automatically populated recent contacts and not people that are actually in the address book.  I wonder if that list is dynamically generated from messages that you have stored in folders?  That might explain why it isn't in a separate file.

---

### Post by limit223 on 2005-12-12
The reply was for the topic:
Modifying KMail distribution list 

not for Kontact and kaddressbook specially...

---

### Post by daller on 2005-12-12
Just backed up my std.vcf, and deleted all my "sent mail" - Still, I have a lot of "recent recipients" :(

---

### Post by lzap on 2006-09-11
kmailrc

---

