---
title: "New SSO has &quot;issues&quot;"
date: 2013-07-30
forum: Forum Feedback &amp; Help
---

### Post by TheFu on 2013-07-30
The new SSO logins have issues, at least with the current Firefox.

* After login, the redirection back doesn't return to the exact forum post - just to the top level. That is broken.
* After login in 1 tab, the other tabs do not gain the login credentials. That is broken.

If I'd wanted an SSO login for everything Ubuntu - I would have created one before. I prefer to keep all my eggs in different baskets. Is having different email addresses the only way to accomplish that now?

Of course, these issues could be personal problems because of my security settings - like blocking 3rd party cookies. If so, I'll either learn to live with it or just stop posting here. I want to give back and this is 1 way that I try to help others.  Running a LUG is another.

---

### Post by wildmanne39 on 2013-07-30
*Thread moved to **Forum Feedback & Help**.*

---

### Post by Elfy on 2013-07-30
IT might take us a short while to get back to you - we've got logging in issues ;)

But we will. 

Bear with us please The Fu.

---

### Post by emdeem on 2013-07-30
> **TheFu said:**
> 
* After login in 1 tab, the other tabs do not gain the login credentials. That is broken.

I've seen this on other browsers too.  Specifically, Chrome Android.

---

### Post by CaptainMark on 2013-07-31
I can't stay logged in, is that a problem for everyone, I expect if it is, they're dealing with it

---

### Post by vasa1 on 2013-07-31
> **CaptainMark said:**
> I can't stay logged in, is that a problem for everyone, I expect if it is, they're dealing with it
+1. Let's give the admins time to iron out wrinkles :)

---

### Post by mc4man on 2013-07-31
Atm the 2 ? cookies associated with this are set to expire at browser session end. Is there any intention to allow a 'stay logged in' option?
(have edited those 2 here to expire in a year, works for now, for how long I guess I'll find out..

---

### Post by wildmanne39 on 2013-07-31
The admin's are seeing what can be done about changing the time limit for being signed in.

---

### Post by sandyd on 2013-07-31
threads merged

---

### Post by mc4man on 2013-07-31
> **sandyd said:**
> threads merged
Not sure that always works as intended.
( as far as the link from previous 'un-merged'  listing..

---

### Post by TheFu on 2013-07-31
> **vasa1 said:**
> +1. Let's give the admins time to iron out wrinkles :)

Definitely. Needed to report the issues - searched and didn't see anyone else reporting the same problems.

I've altered my workflow - instead of opening a new tab and replying for each _interesting_ thread, I open a new tab for each, login to 1 and make posts only in that single tab one at a time.

I've imagined what I'd do if our authentication system was penetrated - we don't have SSO, but we do have a single user/group/password store. If it becomes hacked, well, in short, I'm screwed. ;)

I've never run a forum - too afraid of forum spam to even make the attempt, plus most forum software seems to be written in PHP and our corporate CISSP will not allow PHP-anything on the internet - ever.  Any PHP webapp needs to only be accessible after a VPN connection or on the LAN only.  I'm not a webapp security expert, but I've learned to trust the paranoia from those guys.

I suppose we should also mention all the things that seem to be working as desired, to be fair.  Those 3 things are the only ones that I've noticed.  I don't allow 3rd party cookies and I limit all cookies to be session-only. The tiny extra hassle that causes is worth it to me.

**My Next Steps**
I need to prepare my email server for more spam (up the anti-spam rejection settings) AND actually change the password I use here from the old one? It was long, random, and complex. Need to create a new [email]UbuntuForums934@domain.com[/email] email address and switch over to that. Spam has a tough time being delivered to an address that no longer exists.  Did the same for LinkedIn, Lifehacker, and a few others. Not too much hassle.

---

### Post by JKyleOKC on 2013-07-31
> **mc4man said:**
> Atm the 2 ? cookies associated with this are set to expire at browser session end. Is there any intention to allow a 'stay logged in' option?
(have edited those 2 here to expire in a year, works for now, for how long I guess I'll find out..Care to tell us how you did this? I found them in Firefox, but could only remove them, not edit the expiration time...

---

### Post by Dave_L on 2013-07-31
> **JKyleOKC said:**
> Care to tell us how you did this? I found them in Firefox, but could only remove them, not edit the expiration time...

There's a firefox add-on, Cookies Manager+, that lets you edit cookies, including changing the expiry date: [https://addons.mozilla.org/en-US/firefox/addon/cookies-manager-plus/](https://addons.mozilla.org/en-US/firefox/addon/cookies-manager-plus/)

I haven't tried it on these particular cookies, though.

---

### Post by JKyleOKC on 2013-07-31
> **Dave_L said:**
> There's a firefox add-on, Cookies Manager+, that lets you edit cookies, including changing the expiry date: [https://addons.mozilla.org/en-US/firefox/addon/cookies-manager-plus/](https://addons.mozilla.org/en-US/firefox/addon/cookies-manager-plus/)

I haven't tried it on these particular cookies, though.I just did install and try it, and so far it's working. I shut down Firefox after editing the three cookies from ubuntu that were set to expire at the end of the session, making them expire on December 1 of this year, then shut down Firefox and launched it again. I'm posting this from the session that was still logged in.

Seems to be a viable workaround until they get things fixed at the servers. Thanks much!

EDIT: Three hours later, I have to log in again; apparently something has changed to create new cookies...

---

