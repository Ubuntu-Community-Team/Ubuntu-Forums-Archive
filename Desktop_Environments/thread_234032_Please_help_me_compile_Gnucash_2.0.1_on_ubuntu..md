---
title: "Please help me compile Gnucash 2.0.1 on ubuntu."
date: 2006-08-10
forum: Desktop Environments
---

### Post by ebeyer on 2006-08-10
I just downloaded the latest source for gnucash 2.0.1 and am trying to compile it on my x86 machine running 6.06.

I extracted the tar ball, cd'd to the directory and did ./configure, which, after installing a bunch of dependent libraries, now runs straight through without any errors.

However, when I then type 'make', the terminal says there are no make targets.

This is my second attempt to compile a source code.  The first one took several hours of hand-holding.  Any pointers or advice here would be truly appreciated.

EB

---

### Post by computergroove on 2006-08-10
Try this:
[http://wiki.gnucash.org/wiki/Building](http://wiki.gnucash.org/wiki/Building)

Wish I had my ubuntu machine here so I could try compiling myself and give you some advice. Im going to the office to get it now so I can. Post if the link helped and Ill see if I can get it done in a reasonable time. I have to install ubuntu in my laptop before I can try to compile it. Ill try to check back later. Good Luck.

---

### Post by ebeyer on 2006-08-11
> **computergroove said:**
> Try this:
[http://wiki.gnucash.org/wiki/Building](http://wiki.gnucash.org/wiki/Building)

Wish I had my ubuntu machine here so I could try compiling myself and give you some advice. Im going to the office to get it now so I can. Post if the link helped and Ill see if I can get it done in a reasonable time. I have to install ubuntu in my laptop before I can try to compile it. Ill try to check back later. Good Luck.

I have to confess to being stumped.  If you are able to compile this, maybe you could make the binary accessible to me somehow?

](*,)

---

### Post by Jagot on 2006-08-11
Do you need that specific version of GnuCash?  Is there any reason you don't want to use the version in the repositories?

---

### Post by ebeyer on 2006-08-11
> **Jagot said:**
> Do you need that specific version of GnuCash?  Is there any reason you don't want to use the version in the repositories?

Well, the version in the repositories wasn't working.  I did find a link on the forums that let me install an almost-new version (1.9.8) which is finally working.

Tell me this, though (if you know).  None of the financial management programs I've played with (GnuCash, Kmymoney, Moneydance) import the scheduled transactions I have in Quicken.  Is this a limitation of the .qif or a limitation in the ability of these programs to import things?

EB

---

### Post by drpaul on 2006-08-11
Gnucash will import qif files; it works with regular transactions. I have not tried with scheduled transactions.  There is a users list where you can ask questions.

email address is [email]gnucash-user@gnucash.org[/email]

If you don't register it will take quite a while for your post to get to the list.

HTH

Paul

---

### Post by kelly smith on 2006-08-12
there is also a bug in the 2.0.0 version in the edgy source repository where spaces are stripped in qif imports - this is reported to be fixed in 2.0.1 which I am about to try and compile under dapper but I new to this as well!

kelly

---

