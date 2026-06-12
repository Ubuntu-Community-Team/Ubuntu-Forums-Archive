---
title: "Evolution Evolution Email - &quot;reports possible fake (?) IP number&quot; ?"
date: 2005-05-05
forum: Desktop Environments
---

### Post by davegahan on 2005-05-05
I have a weird problem. Using "sendmail" in Evolution works, using my smtp server results in a "Relaying denied.... IP name is probably forged" The popserver works, i have no problem receiving mail.

I have my administrator coming over later (sigh I am the only one with an Linux setup here) but could someone answer:

- what the difference is between sendmail and using an SMTP server (I know thats newbie but I am learning)
- what could be the cause I cant use my smtp server while I can receive mails from the pop server - why that strange error message "mail cannot be relayed due to a possibly fake IP number" ?

I am using my laptop on different sites so it has really become an annoyance.  ](*,)

---

### Post by ashgoodman on 2007-05-25
Don't know how applicable this is to your specifics but I had same problem. Spent some time online with tech support with my web host company and what we found was that we needed to enable ssl encryption for smtp. once that was done it worked fine.

The encryption works on port 465 which evolution uses by default (according to aplus tech support).
Previous to that I used thunderbird, no encryption on port 587.

Hope that helps!

---

