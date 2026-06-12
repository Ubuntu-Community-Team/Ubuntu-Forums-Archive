---
title: "General Help Questions"
date: 2009-04-08
forum: General Help
---

### Post by rony2 on 2009-04-08
OK, this is the umpteenth time I've loaded Linux (Umnuntu). I would like to switch but I have problems I can't solve.
I can't access windows computers on my network even though they are set to share. I can access my Linus mache from the windows machines.

I can't import my Outlook.pst file into Evolution.

Evolution keeps nagging me for my keyring when I do a send/receive

Evolution won't retrieve my G-mail. In Outlook I had to change ports but can't find this option in Evolution

I can't scan from my HP all in one

Does Crossover slow down the execution of windows programs?

Any help out there?

---

### Post by lisati on 2009-04-08
For one way of setting up shares with Windows computers, see here: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by HermanAB on 2009-04-08
Don't bother trying to import Outlook mail.  Install Outlook in CrossOver and either keep using it, or start using Thunderbird - eventually you'll stop using Outlook and the old mail won't matter anymore.

SANE should be able to handle your HP scanner.

Crossover doesn't slow programs down.  The ones that work, work fine.  The ones that don't work, don't work at all.  It is binary.

---

### Post by FrankT-Qc on 2009-04-08
About Evolution not picking you mail... 

Gmail has two options : IMAP and POP3 but does not allow them by default. You have to go to your gmail (web) interface, go to your settings and enable either one you wish to use (or both) before you actually can use one. The best place to get instructions is in google's settings pannel.

By the way, have you tried thunderbird ? There's even an add-on to make connections to gmail easier...

About windows shares... 

I have found that on some XP Pro setups where no shares are publicly available (all are password protected), it happens that browsing reports no shares while there sould be a few. A quick and easy workaround is to have a public (readonly/empty/dummy) share that's accessible to everyone on the XP box. 

If you want to do a quick check, you can go in the panel under Places->Connect To Server and then enter your server info... While browsing may fail, if you can't connect directly, it's probably a connectivity problem (firewall ?).

About PST files... You might want to look at this : 

[http://kb.mozillazine.org/Import_.pst_files]("http://kb.mozillazine.org/Import_.pst_files")

It's not evolution, but once your data is in there, you can relay it elsewhere...

---

