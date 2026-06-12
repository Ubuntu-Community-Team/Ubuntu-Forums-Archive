---
title: "Blocking Contacts in Empathy 3.4.1 *still* not working?"
date: 2012-05-15
forum: Desktop Environments
---

### Post by arcterex on 2012-05-15
This was a bug in 11.10 and 11.04 and I can't believe that it's *still* not working and it must be a mistake on my part.  For the life of me I cannot block contacts in empathy on MSN!  Every morning I log in and get a ton of "hey baby" and "I'm bored, what you up to" from [email]randomhotchick454221@hotmail.com[/email] type addresses.  I click on contact->block, approve the block, and then close the window.  The next morning (or later on the same day) the same thing happens, and I see that the contact is already set as blocked.  I was under the impression this was a libpurple thing or something, but again I can't see that something this fundamental is still unfixed.
```

empathy       3.4.1-0ubuntu1
libpurple-bin 1:2.10.3-0ubuntu1
libpurple0    1:2.10.3-0ubuntu1

```

Any suggestions appreciated (or should I just move to another IM client?).

Ubuntu desktop 12.04 amd64 on a laptop, vanilla install, upgraded from 11.10.

---

### Post by Kelvari on 2012-08-05
Exact same happening with me. Any advice would be welcome.

```
empathy                                3.4.2.1-0ubuntu1 
libpurple-bin                          1:2.10.3-0ubuntu1.1
libpurple0                             1:2.10.3-0ubuntu1.1 
```

---

### Post by arcterex on 2012-10-18
And with a fresh install of 12.10 the same problem still exists months later.  *sigh*

```

ii  empathy                                                  3.6.0.3-0ubuntu1                           amd64        GNOME multi-protocol chat and call client
ii  empathy-common                                           3.6.0.3-0ubuntu1                           all          GNOME multi-protocol chat and call client (common files)
ii  nautilus-sendto-empathy                                  3.6.0.3-0ubuntu1                           amd64        GNOME multi-protocol chat and call client (nautilus-sendto plugin)
ii  gnome-noble-icon-theme                                   5.5.1-1ubuntu1                             all          purple variation of the GNOME-Colors icon theme
ii  libpurple-bin                                            1:2.10.6-0ubuntu2                          all          multi-protocol instant messaging library - extra utilities
ii  libpurple0                                               1:2.10.6-0ubuntu2                          amd64        multi-protocol instant messaging library
ii  shiki-noble-theme                                        4.6-1ubuntu2                               all          purple variation of the Shiki-Colors theme
ii  telepathy-haze                                           0.6.0-1                                    amd64        Telepathy connection manager that uses libpurple


```

---

### Post by arcterex on 2012-10-22
> **Kelvari said:**
> Exact same happening with me. Any advice would be welcome.


I think the advice is remove empathy and install pidgin.

---

### Post by Rex Bouwense on 2012-10-22
There may be a problem in Empathy.  I haven't used it in a while.  However, there is a better chance that the problem lies with MSN.  I moved from it to Google Talk and have zero problems.  I have also found that gmail is a lot more dependable that Microsof's hot mail anyway.

---

### Post by farbror_ace on 2012-11-28
Same problem for me, same 3 contacts spamming me at each logon even tho they are on my blocklist in Empathy.
As for moving to gmail sure, but that wont help if your friends are on msn.

It is beyond me that a chat client that is shipped as standard with a major OS in 2012 still dont have working blocking functionality.

---

