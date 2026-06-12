---
title: "Solved: Evolution 34.4 mails are not send directly anymore but stuck in outbox"
date: 2023-07-24
forum: Desktop Environments
---

### Post by pongraczi on 2023-07-24
Hi,

Recently I discovered (in the hard way), my Evolution changed its behavior and it does not send emails directly, using remote server, but it only saves the sent email into the On this computer/Outbox.
Email only will be sent, when I directly hit the Send/Receive.
Even email will be at Outbox for days if I do not hit send/receive of restart evolution.

As I tried to find the solution for this issue, I found that, this particular issue pops up several times since 2008, but I did not find any solution.

Just try to search this forum with the $subject, you will find several closed threads with no solution.

So, I post it again.

Do you have any idea?
Thnx.

---

### Post by pongraczi on 2023-07-24
Ok, turned out, it is a feature and not a bug.

I do not remember I changed any settings and I do not know, it is possible to Evolution can change it by itself.

There is a settings, where one can control, how to send email, it looks like this:
Send messages through folder [ Outbox ] and [^ Keep in folder       ]
                                            [^ Send immediately     ]
                                            [^ Send after 5 minutes ]

I changed it to Send immediately and it started to work as expected.

What could be the root cause?
* maybe I changed it (I do not remember, but I cannot rule out)
* as I have terrible internet connection (no alternative), my connection frequently extremely slow, disconnects and other issues - maybe I was offline for a while and Evolution changed its behavior?
* I also used to bring offline - online evolution when refreshing folders of 10 accounts getting slow (10 times per day)

---

### Post by ActionParsnip on 2023-07-24
Great share. Hopefully this will help others

---

