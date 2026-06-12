---
title: "mail-notification problem..."
date: 2005-06-24
forum: Desktop Environments
---

### Post by irusun on 2005-06-24
I've installed mail-notification 1.1-3 (Ubuntu Hoary - Gnome 2.10).

It works ok with one of my pop3 accounts, with the common setup of:
Hostname: mail.domain.com
Username: username

However, it doesn't work with my main pop3 account with the less common setup of (it's my own personal domain that I host through godaddy.com):
Hostname: mail.domain.com
Username: [email]username@domain.com[/email]

(obviously I substituted my actual username and domain name when setting it up in mail-notification).

There's no special authentication needed for either account.

I have both set up that way in evolution and it downloads mail fine (for many years).  The old mail notification applet in Gnome 2.8 worked fine.

Does anyone know of this issue or what I might be doing wrong?
Does mail-notification simply not recognize a Username of [email]username@domain.com[/email] (leaving out the @domain.com doesn't help)?
If this is a problem with mail-notification, does anyone know of any work-arounds?

Thanks!

---

### Post by Mez on 2005-06-24
First of all, I asusme you're using backports - so try support in the backports forums

Othersie - you amy want to try user+domain.com  that usually works for me

---

### Post by irusun on 2005-06-24
Thanks for responding!

I tried:
Hostname: mail.domain.com
Username: username+domain.com

Unfortunately, the '+' didn't work.

Any other ideas?  Any one else having this issue?

Regarding the Backports forum - thanks for pointing me to the correct forum.  It's not really really intuitive though -  I did check that forum out before posting, but almost all of the posts are requests for packages or issues using Backports - I didn't see much application support.  But I'll try posting there.  Thanks.

EDIT: I figured out the problem - Under Account Properties > Details > Authentication mechanism > USER/PASS is the proper setting for my web hosting/email provider (goddaddy.com).

---

