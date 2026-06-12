---
title: "Kmail GPG problem needs to be solved ... what did i do wrong?"
date: 2005-12-14
forum: Desktop Environments
---

### Post by drx on 2005-12-14
At the moment i am again trying to get GPG encryption/decryption working with kmail. I had no success with KMail version 1.8 on, also installed KDE 3.5 ... in Kmail 1.7.2 everything was dreamingly working.

I have installed gpg, kgpg and the gnupg-agent from the repositories.

There are three kind of errors i receive:

1. I cannot decrypt GPG inline messages. Kmail tells me that i entered a wrong passphrase, although it did not even offer me to enter one.

2. I cannot decrypt GPG Mime messages. Kmail just displays the blue message, that the crypto module openpgp was not able to decrypt the data.

3. When i send messages and encrypt them, recipients complain they are garbled base64 encoded stuff, but not a gpg message of any known format.

The crypto-setup of Kmail reports that under GpgME OpenPGP (gpg) and S/MIME (gpgsm) are available. Chiasmus is not available, but i am not really interested in chiasmus :) So no matter how i enable or disable these crypto backends, nothing changes.

I wonder what happened, as said, in Kmail 1.7.2 it was a no-brainer. Mozilla Thunderbird with Enigmail as well is greatly working. But i would prefer running Kmail for the sake of its great integration into the desktop.

Can anybody help me?

---

### Post by editrix on 2006-01-03
Hi drx:

Since no one's answered you in 2 weeks ...

Have you seen this? [http://lists.debian.org/debian-qt-kde/2005/10/msg00177.html](http://lists.debian.org/debian-qt-kde/2005/10/msg00177.html)

It's about a bug in kmail with mime & pgp. I have no idea what it means, but I found it when trying to solve my own kde/mime problem.

---

### Post by Flane on 2006-01-09
hi,
i don't have an answer but i can confirm this strange behaviour.

Did you find a solution?

Thanks
Flane

---

### Post by drx on 2006-01-11
I think we will have to wait until the bug is being fixed.

---

### Post by Jon V on 2006-01-19
Hi,

OK, just spent quite a bit of time trying to fix this problem, and I now have it working.

Here's what I did:

(assuming kgpg and gnupg already installed)

sudo aptitude install gnupg-agent gnupg2 pinentry-qt

note: gnupg2 does not overwrite existing gnupg, but provides another interface for the agent (I think).

gnupg-agent installs /etc/X11/Xsession.d/90gpg-agent, which starts gpg-agent running as a daemon.

**Important:** This script checks whether you have 'use-agent' enabled in /home/username/.gnupg/gpg.conf, so open that file in an editor, find 'use-agent'.  It's commented out by default, so remove the '#' from the front.

OK, that should be all.  End your KDE session, do ctrl-alt-backspace at the login screen to restart X completely, log back in and try it.

Let me know if you still dont have any luck

Jon

---

### Post by GeneralZod on 2006-01-19
[QUOTE=Jon V]
Stuff
[/QUOTE]

Haven't tried this yet (still at work :() but I'll try it when I get home.  Anyway, thanks for your efforts, and for sharing!  You may want to send this to Team Bahamut or another documentation team as (if it works!) it is very useful information.

---

### Post by GeneralZod on 2006-01-26
[QUOTE=GeneralZod]Haven't tried this yet (still at work :() but I'll try it when I get home.  Anyway, thanks for your efforts, and for sharing!  You may want to send this to Team Bahamut or another documentation team as (if it works!) it is very useful information.[/QUOTE]

Oops - forgot about this.  Anyway, it works perfectly here; thanks very much indeed, Jon V!

---

### Post by Zerlinna on 2006-02-19
It didn't work for me, I had to create a little script myself which starts gpg-agent at the beginning of the kde session.

Anybody having the same problem have a look  [here,]("http://zerlinna.blogspot.com/2006/02/get-gpg-decryption-working-within.html")

---

### Post by drx on 2006-02-20
thanks zerlinna, your instructions did the trick! i feel like i am in 2006 again with my emails!

---

### Post by Zerlinna on 2006-02-21
I'm glad I could help you :) 

Z.

---

### Post by zojas on 2006-08-06
it works for me now too, using gnupg-agent.

I'm paranoid though, and I can't figure out how to control how long gnupg-agent remembers (my passphrase|my decrypted private key). I don't want anyone who gets my keyboard for a few minutes able to read my encrypted email.

anyone know how to tell gnupg-agent how long?

there seems to be almost zero docs on it, not even google knows.

there is mention of a gnupg-agent.conf file in ~/.gnupg/ but again, no docs on it I can find.

thanks

---

### Post by zojas on 2006-08-06
oops, I posted too quickly. the gentoo forums knew the answer:

[a doc file about gnupg linked to from gentoo forums]("http://www.gentoo.org/doc/en/gnupg-user.xml#doc_chap4")

---

### Post by jonsson on 2007-08-21
> **Jon V said:**
> Hi,

OK, just spent quite a bit of time trying to fix this problem, and I now have it working.

Here's what I did:

(assuming kgpg and gnupg already installed)

sudo aptitude install gnupg-agent gnupg2 pinentry-qt

Jon

I had the same problem on my fully updated Kubuntu Feisty. 

Installing gnupg-agent and pinentry-qt and uncommenting the use-agent line was enough, though. gnupg2 was not needed. Now I have to figure out if I might *want* gnupg2 ;-) But it was not needed to make KMail work.

---

