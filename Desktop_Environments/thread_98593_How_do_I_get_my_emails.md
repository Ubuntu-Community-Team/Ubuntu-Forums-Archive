---
title: "How do I get my emails?"
date: 2005-12-03
forum: Desktop Environments
---

### Post by ardchoille on 2005-12-03
I am using Evolution installed with Synaptic in Ubuntu 5.10. I can send and receive email fine. But, when I send an email to myself (like ToDo's, reminders, etc), I see the sent email in the sent folder, but Evolution never downloads them into the inbox. I can check my gmail with Firefox and see the sent emails there in the inbox, but Evolution never downloads them to my inbox in Evolution. What's up? Is there a setting I need to change somewhere? If so, where?

---

### Post by GeneralZod on 2005-12-03
Is this using gmail's POP3 service? gmail has a *very* odd idea of how a POP3 server should behave.

---

### Post by ardchoille on 2005-12-03
[QUOTE=GeneralZod]Is this using gmail's POP3 service? gmail has a *very* odd idea of how a POP3 server should behave.[/QUOTE]
Yes, this is using gmail's pop3 service. But, Thunderbird never had problems downloading emails that I sent to myself, so I think it is an Evolution specific problem.

The thing is, if I send myself an email from the gmail web UI, Evolution will download it normally. The problem only seems to exist if I send myself an email from within Evolution.

---

### Post by GeneralZod on 2005-12-03
What you *might* be seeing is gmail not providing Evolution with e-mails that Thunderbird has already downloaded - this is what I mean by "gmail has a very odd idea of how a POP3 server should behave" - if an e-mail has been downloaded via POP3, then it *simply won't be offered* to any other client that attempts to download your gmail e-mails via POP3, unlike virtually every other POP3 server in existence :)

Basically, if you are trying to keep local copies of your inbox up-to-date with two different clients (either different e-mail apps, or the same apps on two different computers), you will have an annoyingly difficult time, sadly :(

Edit:

Actually, now that I read what you've written more closely, this probably isn't what's happening, after all :)

---

### Post by ardchoille on 2005-12-03
[QUOTE=GeneralZod]What you *might* be seeing is gmail not providing Evolution with e-mails that Thunderbird has already downloaded - this is what I mean by "gmail has a very odd idea of how a POP3 server should behave" - if an e-mail has been downloaded via POP3, then it *simply won't be offered* to any other client that attempts to download your gmail e-mails via POP3, unlike virtually every other POP3 server in existence :)

Basically, if you are trying to keep local copies of your inbox up-to-date with two different clients (either different e-mail apps, or the same apps on two different computers), you will have an annoyingly difficult time, sadly :([/QUOTE]
No, Evolution will not download email that I send to myself. This is regardless of whether I have gmail opened in FF or not. I had that thought too, and tested to make sure. At least you and I are thinking alike :)

---

### Post by GeneralZod on 2005-12-03
Heh - OK, I'm not sure why this isn't working for you, although it's interesting to note that I actually had the opposite problem, more or less - *Thunderbird* would never let me send e-mails to myself! Conclusion: all e-mail clients are equally nutty :D

---

### Post by ardchoille on 2005-12-03
[QUOTE=GeneralZod]Heh - OK, I'm not sure why this isn't working for you, although it's interesting to note that I actually had the opposite problem, more or less - *Thunderbird* would never let me send e-mails to myself! Conclusion: all e-mail clients are equally nutty :D[/QUOTE]
Equally nutty? I couldn't have put that better myself :)

---

### Post by Gray. on 2005-12-03
When I send myself an e-mail using Thunderbird, it never shows up when I try to "Get Mail". But when I go to check it on the internet thru G-mail it's there. This is similar to what you are experiencing I think. Maybe it has to do with the "Leave messages on server" option in Edit > Account Settings.

---

### Post by ardchoille on 2005-12-03
[QUOTE=Gray.]When I send myself an e-mail using Thunderbird, it never shows up when I try to "Get Mail". But when I go to check it on the internet thru G-mail it's there. This is similar to what you are experiencing I think. Maybe it has to do with the "Leave messages on server" option in Edit > Account Settings.[/QUOTE]
I tried that, but it didn't help.

---

