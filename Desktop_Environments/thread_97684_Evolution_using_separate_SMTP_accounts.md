---
title: "Evolution using separate SMTP accounts"
date: 2005-12-01
forum: Desktop Environments
---

### Post by groenland on 2005-12-01
Hi,

I would like to switch from Thunderbird to Evolution for its calendar support. However I experienced troubles when setting up my different mail-accounts. I Hva 4 different accounts - each having its own smtp server. I can't use one server for all mail-accounts, since the smtp server block foreign mail addresses. I can set up a different smtp account for each mail account. However, evoluation refuses to use the smtp account from the specific mail-accounts. Instead it always uses the smtp account from the mail account set as default. This is a pretty stupid behaviour. Anyone else already stumbled upon this problem?
Another quetsion: what the idea of this "On this Coumputer" account? Why is the first pop-mail account automatically inserted there?
Thanks for you help!
chris

---

### Post by ryu kun on 2006-11-13
bump

---

### Post by alec on 2006-11-13
I had a look at this a couple of weeks ago and there seems to be no intuitive answer to it. In the end I set Evolution up with three pop accounts and one smtp, so all mail goes out via the same source. This works ok for me, but can understand your frustration.

However, the KDE pim Kontact, with kmail, korganiser and so on. Will configure in the way that you want, and dose have good calendar integration with email. 

Sorry can't be more helpful

Alec

---

### Post by ryu kun on 2006-11-13
As a Dapper user I was happily using Evolution but if it isn't possible to find a way around, this disadvantage can cause me to switch to Mozilla Thunderbird, I am afraid.

I wonder the situation in Edgy.

---

### Post by dcstar on 2006-11-14
> **groenland said:**
> Hi,

I would like to switch from Thunderbird to Evolution for its calendar support. However I experienced troubles when setting up my different mail-accounts. I Hva 4 different accounts - each having its own smtp server. I can't use one server for all mail-accounts, since the smtp server block foreign mail addresses. I can set up a different smtp account for each mail account. However, evoluation refuses to use the smtp account from the specific mail-accounts. Instead it always uses the smtp account from the mail account set as default. This is a pretty stupid behaviour. Anyone else already stumbled upon this problem?
......

I also have 4 accounts set up (3 POP, 1 mbox) and this feature seems to work correctly in my system.

If I select my "Default" account for sending a message, it uses the SMTP server I have set up in that profile, if I select another profile it uses whatever I have for sending there.

---

### Post by groenland on 2006-11-14
Fo me this problem solved on its own: it was simply that the display of which smtp account Evolution is using when actually is sending a mail is always the one from the standard account - however, in the backend evolution takes the right one...
Hope that clarifies the situation
greetings!

---

### Post by ryu kun on 2006-11-14
> **groenland said:**
> Fo me this problem solved on its own: it was simply that the display of which smtp account Evolution is using when actually is sending a mail is always the one from the standard account - however, in the backend evolution takes the right one...
Hope that clarifies the situation
greetings!

Yes, I've realised it too. The "sending/receiving email" information is misleading, in fact it uses the right smtp server. :)

---

