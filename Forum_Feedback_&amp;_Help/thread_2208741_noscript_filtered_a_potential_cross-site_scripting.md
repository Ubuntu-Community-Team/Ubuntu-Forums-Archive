---
title: "noscript filtered a potential cross-site scripting (XSS) attempt from [http://ubuntuf"
date: 2014-03-01
forum: Forum Feedback &amp; Help
---

### Post by Peter_Heft on 2014-03-01
I have no-script running in firefox in ubuntu 12.04. When I try to log in to the forums I get the above message.  I can see my account and change the password etc,  but not log in.  The only way to log in is to bypass no-scripts warning and reload the page "unsafely", can't recall the exact phrase.  What is the problem here?  What is the use of having no-script if I don't let it protect?
Please help,
Peter
didn't catch everything with the cut and paste, it's ubuntuforums.org

---

### Post by Peter_Heft on 2014-03-02
browser console message showed this;
22:24:33.394 [NoScript XSS] Sanitized suspicious upload to [[https://login.ubuntu.com/+openid]](https://login.ubuntu.com/+openid]) from [[http://ubuntuforums.org/login.php]:](http://ubuntuforums.org/login.php]:) transformed into a download-only GET request.

---

### Post by open2reason on 2014-03-02
I also noticed this very late last night so first thing this morning I removed and then reinstalled Noscript and could not force the error condition. 
A search via google only displayed this thread so I am at a bit of a loss to think what has happened.

---

### Post by bashiergui on 2014-03-02
It looks like noscripts thinks the login procedure is XSS. I guess in a way it is but it's the desired behavior. 

Did noscripts recently update?

Reinstall of noscripts should fix it.

---

### Post by open2reason on 2014-03-02
IIRC Noscript did update 2/3/2014 and I have 2.6.2.18 running now [http://noscript.net/changelog#2.6.8.16](http://noscript.net/changelog#2.6.8.16)

---

### Post by CharlesA on 2014-03-02
Just confirming I am seeing it as well, but if you don't allow it, you won't be able to login.

NoScript says:
> [NoScript XSS] Sanitized suspicious upload to [[https://login.ubuntu.com/+openid]](https://login.ubuntu.com/+openid]) from [[http://ubuntuforums.org/login.php]:](http://ubuntuforums.org/login.php]:) transformed into a download-only GET request.

This is what the page says if don't do anything.

> This is Ubuntu One, built on OpenID. The service enables you to use your Ubuntu One account to log into various sites run by Canonical and Ubuntu.

This page is meant to be called from an OpenID-enabled site and therefore has no user-facing functions.

Which means you won't be able to login.

It's part of the SSO, so I don't know if it is just the behavior of NoScript or what, but I do have ubuntuforums.org  whitelisted.

---

### Post by bashiergui on 2014-03-02
Have you whitelisted openid?

---

### Post by CharlesA on 2014-03-02
> **bashiergui said:**
> Have you whitelisted openid?

Yeah, I have ubuntu.com whitelisted too.

---

### Post by bashiergui on 2014-03-05
For those that were affected... did it resolve?

---

### Post by Peter_Heft on 2014-03-06
I was getting ready to do a reinstall on a new 1 TB HD.  No such problem in the new install.

---

### Post by Peter_Heft on 2014-03-20
New install now did same thing.  I reconnected unsafely.

---

