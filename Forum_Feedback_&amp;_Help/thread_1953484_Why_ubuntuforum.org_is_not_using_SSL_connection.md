---
title: "Why ubuntuforum.org is not using SSL connection?"
date: 2012-04-06
forum: Forum Feedback &amp; Help
---

### Post by abcuser on 2012-04-06
As I see when logging into ubuntuforums.org there is no SSL connection (https). So anyone on the network path may get access to userid/password users are logged with.

Any real reason not to implement the https? Please do not respond with "performance reason", because cite from [https://www.eff.org/https-everywhere/deploying-https](https://www.eff.org/https-everywhere/deploying-https) "Many site operators report that they can&#8217;t move to HTTPS for performance reasons. However, most people who say this have not actually measured any performance loss, may not have measured performance at all..." and Google measuring SSL overhead: "In order to do this we had to deploy no additional machines and no special hardware. On our production frontend machines, SSL/TLS accounts for less than 1% of the CPU load, less than 10KB of memory per connection and less than 2% of network overhead..."

What is the reason ubuntuforums.org is not using SSL like almost all of the web forums/sites that I visit?

---

### Post by hughr2005 on 2012-04-06
What's the point though? Why do you need https? http works perfectly fine for me, I don't really need my communication on this forum encrypted for any reason. And if I did, I'd use tor.

---

### Post by vasa1 on 2012-04-06
> **abcuser said:**
> ... What is the reason ubuntuforums.org is not using SSL like almost all of the web forums/sites that I visit?
Most of the forums I visit do not use SSL. In any case, I have different usernames and passwords for important sites.

---

### Post by coffeecat on 2012-04-06
> **abcuser said:**
> So anyone on the network path may get access to userid/password users are logged with.

The password is sent hashed, so even if someone were IP sniffing, they would only recover the hash.

If you want SSL sign-on, sign in via your Launchpad account.

---

### Post by vasa1 on 2012-04-06
> **coffeecat said:**
> ...
If you want SSL sign-on, sign in via your Launchpad account.
I have a Launchpad account. How do I sign in to the forum via Launchpad? Just curious. I mostly won't be doing so as I don't see the need.

Edit: found it.

---

### Post by Elfy on 2012-04-06
> **vasa1 said:**
> I have a Launchpad account. How do I sign in to the forum via Launchpad? Just curious. I mostly won't be doing so as I don't see the need.

logout - just above the login box is something that says login with launchpad

or something along those line

---

### Post by vasa1 on 2012-04-06
> **forestpiskie said:**
> logout - just above the login box is something that says login with launchpad

or something along those line

Thanks! I saw that after I logged out, something I don't normally do!

---

### Post by Elfy on 2012-04-06
Same :)

I have to logout each time to answer it - should try and remember :lol:

---

### Post by abcuser on 2012-04-08
> **hughr2005 said:**
> ...I don't really need my communication on this forum encrypted for any reason. And if I did, I'd use tor.
It looks like you don't really understand the difference between anonymity and privacy, or you are misinformed. Tor should be used for anonymity reasons not privacy reasons. Lets look into how Tor actually works:
a) User that is using Tor network enters the network with encrypted data.
b) Encrypted data are passed to first random Tor server
c) Encrypted data are passed to the second random Tor server.
d) Encrypted data are passed to the third random Tor server.
Note: All this passing is done on servers with different country or even continent. So far all the traces from where original post comes from are removed. So anonymity is now taken into a place.
e) The last (third) Tor server (officially named exit relay) passes the data (also password) to the target web server in UNENCRYPTED way. So if target web server is not using SSL/TLS (like https) then password can be easily seen between any Tor's exit relay and the bypassed servers to web server. You see Tor does not ensures PRIVACY. To make Tor to work anonymity plus privacy the target web server MUST use SSL connection.

> **vasa1 said:**
> Most of the forums I visit do not use SSL. In any case, I have different usernames and passwords for important sites.
You see you are FORCED to use different usernames/passwords because some of the forums (NOT ALL!) do not use SSL connection.

> **coffeecat said:**
> The password is sent hashed, so even if someone were IP sniffing, they would only recover the hash.

This is not safe. I have analyzed my own network packets (IP sniffed in your jargon) and I see password is being transformed with md5sum algorithm. This is not safe. I agree that reverse engineered md5 hash is very hard if not impossible, but there is no need of braking md5 to see the data. Let me explain, user that gets md5 password (IP sniffed) can write a program to generate all of the combination of lets say one to eight length password and then create md5 hash for all of this clear-text passwords. Now just compare the md5 sniffed password with md5 created database and just look at the original clear-text password. This is actually simple task to do to get a clear text password. Not safe.

> **coffeecat said:**
> If you want SSL sign-on, sign in via your Launchpad account.
This looks like a good idea, good work-around. Password is encrypted properly with SSL. The annoying thing is that this takes a lot of time to log-in, it is a slow opening Launchpad window etc. I hate to stay logged-in! This is also not secure (to stay logged-in), I use computer on public sites a lot. The second problem is privacy one. My Launchpad account and ubuntuforums.org account are different to ensure maximum privacy. When user links two IDs the privacy is reduced. Some system admins now knows the link between two different accounts. Not big issue, but if respecting end-user privacy, this practice is not good.

I think there is no big reason not to use SSL connection, except of buying a proper certificate witch are not expensive for single-domain. I would really like to know what is the reason not to implement SSL? The reason that other web sites (that are obviously insecure) do not use it, is a weak argument. It is just simple, you respect end-users privacy or you don't.

---

### Post by rectec794613 on 2012-04-08
> It looks like you don't really understand the difference between anonymity and privacy, or you are misinformed. Tor should be used for anonymity reasons not privacy reasons. Lets look into how Tor actually works:
a) User that is using Tor network enters the network with encrypted data.
b) Encrypted data are passed to first random Tor server
c) Encrypted data are passed to the second random Tor server.
d) Encrypted data are passed to the third random Tor server.
Note: All this passing is done on servers with different country or even continent. So far all the traces from where original post comes from are removed. So anonymity is now taken into a place.
e) The last (third) Tor server (officially named exit relay) passes the data (also password) to the target web server in UNENCRYPTED way. So if target web server is not using SSL/TLS (like https) then password can be easily seen between any Tor's exit relay and the bypassed servers to web server. You see Tor does not ensures PRIVACY. To make Tor to work anonymity plus privacy the target web server MUST use SSL connection.

Haha now *that's* how you get things straight.

---

### Post by hughr2005 on 2012-04-08
Hey abcuser.

I do understand the difference between anonymity and privacy, but the result of tor and encryption is the same. Using tor, nobody who is snooping will know what I'm doing because any data they see won't be associated with me. With https, nobody who is snooping will know what I'm doing because the data that is associated with me isn't readable to them. Is that a misconception?

Best regards

---

### Post by vasa1 on 2012-04-08
> **abcuser said:**
> ...
You see you are FORCED to use different usernames/passwords because some of the **forums** (NOT ALL!) do not use SSL connection.
...
Not forums but sites required for financial transactions.

One forum that does use https is the AdBlock Plus forum. I still feel that **most** and **not** some forums do not use https.

---

### Post by v1ad on 2012-04-08
unless it is a private forum with sensitive information i see no reason to use ssl the only thing ssl would accomplish at that point is use higher bandwidth. For sites without ssl just use a different password and you will be fine.

---

### Post by haqking on 2012-04-09
Yes i am very concerned that my account will become compromised and that someone may read the stuff i post !

oh wait

Doh !

---

### Post by sammiev on 2012-04-09
> **haqking said:**
> yes i am very concerned that my account will become compromised and that someone may read the stuff i post !

Oh wait

doh !

lol +1

---

### Post by ubuntu27 on 2012-04-09
In my humble opinion, it is reasonable to have a SSL connection for at least **login**, if not the whole site. And really, this shouldn't (wouldn't) overload the servers nor have a performance loss.

Of course, the site owner and the administrator has to make the final decision, but there is nothing to lose on voicing our ideas and opinions. :KS

---

### Post by bodhi.zazen on 2012-04-09
> **ubuntu27 said:**
> In my humble opinion, it is reasonable to have a SSL connection for at least **login**, if not the whole site. And really, this shouldn't (wouldn't) overload the servers nor have a performance loss.

Of course, the site owner and the administrator has to make the final decision, but there is nothing to lose on voicing our ideas and opinions. :KS

The site owner, Canonical, provides secure login via your launchpad account (OpenID) as has already been stated in this thread.

OpenID is the preferred login method.

---

