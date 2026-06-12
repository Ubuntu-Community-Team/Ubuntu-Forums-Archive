---
title: "Kmail downloading every single message after IMAP connection error"
date: 2008-12-15
forum: Desktop Environments
---

### Post by MrE on 2008-12-15
I'm trying to use Kmail with my IMAP enabled Gmail accounts, which works fine initially, but at some point it seems to have trouble communicating with the server and times out, after which it reconnects to the server and starts downloading every single message at an extremely slow pace, and there seems to be no way to stop it.

Restarting Kmail doesn't solve the problem, cos as soon as it checks for new messages, or when I access a folder, it starts downloading again and taken 30% of my CPU.

Between Kmail and nepomukservices (which eats nearly 100%), this turns my PC into something that reminds me of 'the other OS' on a PC 5 years old i.e. unworkably slow

I've tried purging Kmail (which doesn't actually truly purge it, cos after a reinstall Kmail mysteriously seems to have remembered all my account settings), and this doesn't stop the problem either.

I managed to get things working again by purging Kmail (aptitude purge) and then manually removing the ~/.kde/share/apps/kmail/ folder. as well as ~/.kde/share/config/kmail.eventsrc and ~/.kde/share/config/kmailrc, however this means I have to set up all 5 IMAP accounts again which is cumbersome and annoying. Furthermore, the problem comes back at some point although not necessarily with the same account, and deleting only the files related to the problematic account doesn't solve the problem.

I would really like to switch to Kmail/Kontact, instead of Thunderbird and Lightning, but it looks like I'll be forced to stick with Thunderbird cos 'it just works'.

Any ideas?

PS I've got nothing against Thunderbird perse and it works well for me. I would just like to use Kontact because of the tight integration between the various components (this is what made me switch from Gnome to KDE, KDE is all about integration), and because of the better integration into KDE as a whole. So please, no 'helpful' suggestions like 'why don't you stick with Thunderbird if it works so well'.

---

### Post by ellgor on 2008-12-15
Hi,

Noticed that your using the imap setup, sorry I cant help on that, however, I use the pop3 setup (works well with gmail,and others) and have had no issues whatsoever, hope this of use.

Regards, Ellgor.

---

### Post by MrE on 2008-12-15
Thanks Ellgor,

I have to use IMAP though, as I use several computers as well as a mobile phone to access my e-mail and with POP3 that just becomes a mess, with all your messages scattered over the various PCs.

---

