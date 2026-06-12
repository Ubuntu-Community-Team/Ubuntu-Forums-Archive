---
title: "Evolution and Yahoo"
date: 2009-05-02
forum: General Help
---

### Post by nathang1392 on 2009-05-02
is there any way i can make evolution work with yahoo? i have been trying for hours. i would rather just use gmail, but all of my important stuff comes to yahoo. i hit a brick wall reading old forums. if anyone knows please contribute.

---

### Post by michy99 on 2009-05-02
At one time I had it working using ypops, but I dont use it anymore. Do a search for Yahoo Evolution ypops.

---

### Post by BslBryan on 2009-05-02
Ypops! does work.  If you want real advice, though, I'd suggest anything but using it.

I assume you live in the USA, because everywhere else (for example [email]emailaddress@yahoo.co.uk[/email]) provides free pop mail and forwarding.  

I don't know why Yahoo! hates America so much, but using Ypops! is very buggy and not comfortable.

After over a year of talking about converting, I recently sent out a massive email to all of my contacts telling them of a new email address.  Then, I went to every forum, social networking site, website, whatever, where I had an account, or received mail, and changed my email address.

I now use Gmail, and it works flawlessly in Evolution and (I prefer) Mozilla Thunderbird.  

Configuring Ypops! is easy, though, if I haven't convinced you.  :)

Just download it, 
```
sudo apt-get install ypops
```

and configure the mail in Evolution like this:
```
Server Type: POP
Server: localhost:5110
Username: Your Yahoo! Id.
Authentication Type: Password


Server Type: SMTP
Server: localhost:5025
Authentication Type: Login
Username: Your Yahoo! Id. 
```

Hope this helped. :)

---

### Post by todak on 2009-05-02
Unfortunately, some time ago Yahoo decided to do away with free POP access. Now you must pay for that service. It is (still) free using gmail. That is why I switched.

---

### Post by lisati on 2009-05-02
> **todak said:**
> Unfortunately, some time ago Yahoo decided to do away with free POP access. Now you must pay for that service. It is (still) free using gmail. That is why I switched.

That's sad: some years ago, I had a yahoo.com email address, which I used to be able to access using POP but would now have to pay for. As has been noted, everywhere else Yahoo seems to provide free pop access.

---

### Post by nathang1392 on 2009-05-02
does anyone think that yahoo did this to try to keep you with them instead of just forwarding all of your email to a gmail like i thought of doing?

---

### Post by BslBryan on 2009-05-02
Of course, however it's had the opposite effect, I'm sure.  Plenty of other email clients to choose from that offer just as many benefits as Mail Plus.

---

