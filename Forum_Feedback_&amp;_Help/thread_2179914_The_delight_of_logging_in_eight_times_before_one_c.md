---
title: "The delight of logging in eight times before one can post"
date: 2013-10-10
forum: Forum Feedback &amp; Help
---

### Post by K7AAY on 2013-10-10
go to [http://ubuntuforums.org/](http://ubuntuforums.org/)
Sign in with SSO
Select a forum, I see my username in the orange ribbon at upper right.
Click on Post New
Prompted to sign in again
Sign in again
Return, not to forum, but to [http://ubuntuforums.org/](http://ubuntuforums.org/)
Select a forum, I see my username in the orange ribbon at upper right.
Click on Post New
Prompted to sign in again  but it remembers who I am so why am I logging in again?
Sign in again
Return, not to forum, but to [http://ubuntuforums.org/](http://ubuntuforums.org/)
Select a forum, I see my username in the orange ribbon at upper right.
Click on Post New
Prompted to sign in again but it remembers who I am so why am I logging in again?
Sign in again
Return, not to forum, but to [http://ubuntuforums.org/](http://ubuntuforums.org/)
Select a forum, I see my username in the orange ribbon at upper right.
Click on Post New
Prompted to sign in again but it remembers who I am so why am I logging in again?
Sign in again
Return, not to forum, but to [http://ubuntuforums.org/](http://ubuntuforums.org/)
Select a forum, I see my username in the orange ribbon at upper right.
Click on Post New
Prompted to sign in again but it remembers who I am so why am I logging in again?
Sign in again

On about the 8th time through this delightfully recursive process, I finally get in to post.

Happens with Chrome and IE10 on Win7. 
Happens from FF and Chromium from Xubuntu 13.04. 
Happens from Lubuntu 12.04 with Opera. 
Clearing the cache/cookies does not help.


Why are y'all doin' this to us?

---

### Post by Hylas de Niall on 2013-10-10
Works fine here.

---

### Post by coldraven on 2013-10-10
> Clearing the cache/cookies does not help.

Well that's my only idea scuppered. From day one it has worked fine for me.
Edit: Could this be a wifi problem?

---

### Post by K7AAY on 2013-10-10
_coldraven_ Since I do not use WiFi, no. 

What cookie-related settings are required? 

And, even though I see my username in the orange bar at top, once again I am told I must refresh the page and login before trying again.

---

### Post by TiberiusT on 2013-10-10
Not a very constructive response but....I'm on vanilla Xubuntu x64 13.04 with FF. No problems at all.

T

---

### Post by coldraven on 2013-10-11
> What cookie-related settings are required?

I'm using a fresh install of Ubuntu 12.04.3.
FF is set to accept cookies,accept third party cookies and keep until I close FF.
Closing FF also deletes the cache and history.
It should work on the default settings so I'm at a loss to explain your problems.
What happens if you try to log in from a different location?

---

### Post by K7AAY on 2013-10-11
Happens on three different machines as described in the original post.

---

### Post by K7AAY on 2013-10-17
Does _not_ happen from my phone using Chrome. However, that ain't a viable solution. Help for this problem is requested; I've answered every query and provided all requested information, and surely would like it to work.

---

### Post by whatthefunk on 2013-10-18
In the last few days, this has been happening to me too.  My sessions expire within minutes it seems.  This is becoming more hassle than its worth......

---

### Post by hloeung on 2013-10-21
Hi Guys,

As stated in another post, I've increased the default session timeout from 2 hours to 6. Is this still a problem?

---

### Post by K7AAY on 2013-10-22
Failed again within 5 minutes of login.

---

### Post by hloeung on 2013-10-23
Hmm, I'm wondering if it's because your ISP uses transparent proxies. vBulletin has a security feature "Session IP Octet Length Check" which we currently have set to /24 or 255.255.255.0. Sessions are invalidated if your IP address changes (or the IP of the transparent proxies) to another /24.

---

### Post by K7AAY on 2013-10-24
Well, I doubt my Fortune 100 employer is going to change their infosec policy for this one website.  However, that does not explain why it fails at home, where I have a CLINK (err, CenturyLink) plain-Jane proxyless DSL connection. So, *still not solved*.

---

### Post by K7AAY on 2013-11-04
:( Only took three logins to post this... still not fixed. :(

---

