---
title: "Launchpad login system... Need some details"
date: 2010-03-13
forum: Forum Feedback &amp; Help
---

### Post by kio_http on 2010-03-13
On Ubuntuforums there is an option to login using launchpad accounts by associating a user with a launchpad id.

I was wondering if I could get some details on how this add-on works or even source code (if possible)?

---

### Post by The Toxic Mite on 2010-03-13
Well, if you have a Launchpad account, you just type your Launchpad URL onto the sign-in page like so: [noparse]https://launchpad.net/~your-nick[/noparse]

:)

---

### Post by kio_http on 2010-03-13
> **The Toxic Mite said:**
> Well, if you have a Launchpad account, you just type your Launchpad URL onto the sign-in page like so: [noparse]https://launchpad.net/~your-nick[/noparse]

:)

@ The Toxic Mite
I was referring to how the system itself works not as to how the system is used.

In short I want to know how the plugin that enables users to use launchpad to login into vbullentin was created!

---

### Post by kio_http on 2010-03-15
Bump!

---

### Post by matthew on 2010-03-15
> **kio_http said:**
> @ The Toxic Mite
I was referring to how the system itself works not as to how the system is used.

In short I want to know how the plugin that enables users to use launchpad to login into vbullentin was created!

The Launchpad developers wrote the code. It basically uses the [Launchpad API]("https://help.launchpad.net/API") to authenticate and then confirms the identity based on details in the account here (email address/launchpad account info).

---

### Post by kio_http on 2010-03-15
> **matthew said:**
> The Launchpad developers wrote the code. It basically uses the [Launchpad API]("https://help.launchpad.net/API") to authenticate and then confirms the identity based on details in the account here (email address/launchpad account info).
Interesting principle. 

So I guess when the user logs in launchpad, it generates a cookie appropriate for logging in to Ubuntuforums.

Another possible path could be using an OpenID logon in general.

Anyway thanks thread solved.

---

### Post by matthew on 2010-03-15
> **kio_http said:**
> Another possible path could be using an OpenID logon in general.

FYI, Launchpad accounts may be used as OpenID logins. :)

[http://blog.launchpad.net/cool-new-stuff/openid-from-your-launchpad-profile](http://blog.launchpad.net/cool-new-stuff/openid-from-your-launchpad-profile)

---

### Post by koan on 2010-03-30
OpenID.  I have an openid already.  Why is the "Open"ID login for launchpad fenced off?

The whole point of OpenID is that I don't have to manage credentials in a bunch of different places.

So now everyone is making their own "open" authentication platform that is incompatible with everyone elses and using openID to do it.

That is just making a frustrating problem even more frustrating.  

I'll fix the Xen wiki page once I can login thanks.

---

