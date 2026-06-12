---
title: "Security? Even for login, no https://ubuntuformums.org??"
date: 2011-01-19
forum: Forum Feedback &amp; Help
---

### Post by DiagonalArg on 2011-01-19
Passwords are passed in the clear??

[Edited and re-edited because this thing had gotten posted 3x.  Now the other two are deleted ...]

---

### Post by bodhi.zazen on 2011-01-19
I moved your post as it seemed more forums related, please re-state your question.

---

### Post by robsoles on 2011-01-22
I think the OP is talking about having a secure session with ubuntuforums.org in our browser.

[http://ubuntuforums.org/showthread.php?t=1670965](http://ubuntuforums.org/showthread.php?t=1670965) is this thread but I cannot access anything, let alone the same, on [https://ubuntuforums.org/showthread.php?t=1670965](https://ubuntuforums.org/showthread.php?t=1670965)

---

### Post by DiagonalArg on 2011-01-25
Yes, this was exactly the point, thank you.  Even for login, there's no [https://.](https://.)  Even worse than the firesheep threat, passwords are passed in the clear!!

Seems not much security on this security forum. [-X

---

### Post by Joeb454 on 2011-01-25
As far as I'm aware, this is a limitation in vBulletin, not something that we chose to do.

---

### Post by robsoles on 2011-01-25
Look: [http://www.vbulletin.org/forum/showthread.php?t=135864](http://www.vbulletin.org/forum/showthread.php?t=135864)

If a valid SSL certificate is acquired and the web-server is configured to serve the site in HTTPS (on port 443) while HTTP is left on then that *should* allow users to choose to access the site in 'clear text' or with 'decent encryption' pretty much regardless of the script (or other sources) of the site.

Valid SSL certificate is probably the real tumbler. expensive buggers - I for one would gladly tell my browser to accept an unsigned certificate from ubuntuforums.org but to the masses that 'unsigned/invalid' certificate message is a killer.

---

### Post by Joeb454 on 2011-01-25
It's something we'd need to speak to Canonical about if we were to consider it, as they pay the bills ;)

---

### Post by dmizer on 2011-01-26
You can use the "Sign in using your Launchpad ID" option as launchpad uses SSL.

---

### Post by rajeev1204 on 2011-01-26
Are you telling me that my password is visible to admins here ?

---

### Post by robsoles on 2011-01-26
> **rajeev1204 said:**
> Are you telling me that my password is visible to admins here ?

No. What is being discussed is that passwords cross the internet in clear text here.

---

### Post by Joeb454 on 2011-01-26
> **rajeev1204 said:**
> Are you telling me that my password is visible to admins here ?

No, we cannot view any passwords

---

### Post by TheSqueak on 2011-01-26
> **Joeb454 said:**
> No, we cannot view any passwords

But the sysadmins of the servers that the forums live on could, if they so choose

---

### Post by Grenage on 2011-01-26
> **robsoles said:**
> Look: [http://www.vbulletin.org/forum/showthread.php?t=135864](http://www.vbulletin.org/forum/showthread.php?t=135864)

If a valid SSL certificate is acquired and the web-server is configured to serve the site in HTTPS (on port 443) while HTTP is left on then that *should* allow users to choose to access the site in 'clear text' or with 'decent encryption' pretty much regardless of the script (or other sources) of the site.

Valid SSL certificate is probably the real tumbler. expensive buggers - I for one would gladly tell my browser to accept an unsigned certificate from ubuntuforums.org but to the masses that 'unsigned/invalid' certificate message is a killer.

Single-domain certs are quite cheap.

---

### Post by robsoles on 2011-01-26
> **TheSqueak said:**
> But the sysadmins of the servers that the forums live on could, if they so choose

Passwords are encrypted where they 'live'.

---

### Post by TheSqueak on 2011-01-26
> **robsoles said:**
> Passwords are encrypted where they 'live'.

That may be true, but if they're transmitted in the clear then anyone who has ever used snoop, or tcpdump, or any of a number of programs, can get them.

---

### Post by robsoles on 2011-01-26
that is the concern the OP had for this thread.

The administrators of UF have plenty on their plates, right now, without us starting some sort of rally about this.

HTTPS shouldn't add to the issues the site is experiencing, the added "overheads" are slightly bigger for the client for instance (if I understood that lesson). But it would be something Canonical would have to be agreeable about and approaching them for more annual or bi-annual expenditure (pretty sure cert. authority is "rented") straight after the expenditure of these new servers, we are told will be implemented soon, probably wouldn't meet a warm reception.

I think it would be very professional of ubuntuforums.org to get a certificate and redirect all http requests to https but it won't stop me logging in and posting here if they never can/do. Anyway, as stated earlier in thread, if people are concerned about coming up with a 'throwaway' password to transmit in clear-text then they could use a launchpad id.

---

### Post by dmizer on 2011-01-26
> **robsoles said:**
> that is the concern the OP had for this thread.

The administrators of UF have plenty on their plates, right now, without us starting some sort of rally about this.

That, and if you have a launchpad ID, you can **already** log into the forums over SSL. Being able to log into the forums over SSL was one of the specific reasons for writing the Launchpad mod for the forums.

---

