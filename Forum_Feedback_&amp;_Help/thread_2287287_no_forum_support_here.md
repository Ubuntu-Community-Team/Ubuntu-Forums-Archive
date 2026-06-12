---
title: "no forum support here?"
date: 2015-07-18
forum: Forum Feedback &amp; Help
---

### Post by Skaperen on 2015-07-18
i was having troubles with Ubuntu One and could not get logged in.  the trouble looked a web programming error in the password change which i was doing because it no longer associated my password with my email.  it wanted me to login with my email instead of my nick.  the password change was failing with "Bad Request" in all black like a web server error. i tried to access their support form but all it would offer is to tell me to use the password change form, which was broken.  so i sent email to support@ there and cc'd here which was rejected as no such address.  most forums have a support subforum the does require login to handle support issues ... but not here.

i repeated submitting my password change many times, many ways, and eventually it worked, but i don't remember what it was i did to get it to work.  maybe they fixed the bug.  in any case this all showed to me a lack of support.

it would be nice if this place at least has a place to post support issues if here is not it.  then it would be practical to allow non-logins to support login issues.

---

### Post by TheFu on 2015-07-18
Ubuntu One was killed off a year ago (31 July, 2014). Guess they didn't have a critical mass of paid users.
[http://blog.canonical.com/2014/04/02/shutting-down-ubuntu-one-file-services/](http://blog.canonical.com/2014/04/02/shutting-down-ubuntu-one-file-services/)

BTW - it is best to post the EXACT URLs and EXACT email addresses used, though in this case it appaers that won't matter.

---

### Post by Skaperen on 2015-07-19
> **TheFu said:**
> Ubuntu One was killed off a year ago (31 July, 2014). Guess they didn't have a critical mass of paid users.
[http://blog.canonical.com/2014/04/02/shutting-down-ubuntu-one-file-services/](http://blog.canonical.com/2014/04/02/shutting-down-ubuntu-one-file-services/)
that refers to "file services".  this place uses its OpenID service for login, presumably for a pan-Ubuntu [Single Sign-On]("https://en.wikipedia.org/wiki/Single_sign-on"). 
> **TheFu said:**
> BTW - it is best to post the EXACT URLs and EXACT email addresses used, though in this case it appaers that won't matter.the issue of my thread starter post is how this place can handle support issues regarding the forum itself.  e.g is "General Help" the expected place?  i *NOW* see a link for "Forum Feedback & Help" but, i did not see that when i _had the issue_ and was _not logged in_. maybe my bad. unless logged in, one cannot post in FF&H.  is the issue related to [Staying logged in to Forums and Bad Request]("http://ubuntuforums.org/showthread.php?t=2273359")?  i did not get that message and i do not know of my IP changing.  i have exactly ONE static IPv4 and a static /64 of IPv6. maybe IPv6 was being tested then and my browser used it? i get no AAAA record today.

---

### Post by sudodus on 2015-07-19
[s]Near the bottom of the Ubuntu Forums web pages there is a link [Contact Us](http://ubuntuforums.org/sendmessage.php) that you can use, if you cannot log in or you have other problems with the forums.[/s]

There are other people who know better than I how to help you in this particular case with logging in.

---

### Post by coffeecat on 2015-07-19
From your description, this sounds like a temporary server issue with the Ubuntu One SSO service. I have to emphasise that we don't administer Ubuntu One SSO. So, even if you could have posted on the forum, we wouldn't have been able to resolve the immediate problem. Nevertheless, you raise an important point &#8211; that of people being unable to log into the forum and needing to contact the forum admins. The forum admins are looking into how we can best do this so that those in your situation, unable to log in, can contact us. At least we could have pointed you in the right direction.

If you go to [https://login.ubuntu.com/](https://login.ubuntu.com/) and scroll to the bottom of the page, whether or not you are logged into Ubuntu One SSO, you will see a support link. This takes you to [https://forms.canonical.com/sso-support/](https://forms.canonical.com/sso-support/) . Choosing &#8220;resetting my password&#8221; takes you to a page that I guess you may have been trying to access anyway, but &#8220;other&#8221; gives you a form to send to Ubuntu SSO support.

Were you able to find that link?

---

### Post by coffeecat on 2015-07-19
> **sudodus said:**
> Near the bottom of the Ubuntu Forums web pages there is a link [Contact Us](http://ubuntuforums.org/sendmessage.php) that you can use, if you cannot log in or you have other problems with the forums.

@sudodus, the contact us link is not visible to those not logged in, which left the OP in a catch 22 situation. That's the issue I refer to in my previous post and which we are looking into. Simply making the contact us link visible to those not logged in is probably not viable, since that would mean that the Forum Council mailing list would get inundated with spam and sundry weird emails. We are looking for a viable solution.

---

### Post by Skaperen on 2015-07-19
> **coffeecat said:**
> @sudodus, the contact us link is not visible to those not logged in, which left the OP in a catch 22 situation. That's the issue I refer to in my previous post and which we are looking into. Simply making the contact us link visible to those not logged in is probably not viable, since that would mean that the Forum Council mailing list would get inundated with spam and sundry weird emails. We are looking for a viable solution.

viable, *if **vBulletin supports it*, is a subforum of **FF&H** that allows posting without login.  it would then be _the place for login issues_.   stickies would guide people to how to figure out where the failure is and how to get *Ubuntu One support* for cases of Ubuntu One problems.  a Captcha to post might be good. a direct link when a user is not logged would help.

---

### Post by coffeecat on 2015-07-20
There is now a "contact an admin" link in the Quick Links drop-down menu of the navigation bar, which takes you to a new relevant section of the forum FAQ. That's visible both to logged in members and guests.

> **Skaperen said:**
> viable, *if **vBulletin supports it*, is a subforum of **FF&H** that allows posting without login.  it would then be _the place for login issues_.   stickies would guide people to how to figure out where the failure is and how to get *Ubuntu One support* for cases of Ubuntu One problems.  a Captcha to post might be good. a direct link when a user is not logged would help.

That's an interesting idea, and thanks for it. We (the Forum Council) discussed it, but we won't be pursuing it. It is possible with vBulletin, but even with a good Human Verification stage before guests can post, prior experience shows that such a section would still become a magnet for human spammers, trolls, and sundry nuisances. Also, a child forum of FF&H would be fairly hidden and might not be found by those who really need it. Also, sad to say, bitter experience shows that those who need to read stickies, don't. Very frustrating.

By the way, captchas are rubbish, in my opinion, but we do have a tried and tested method of Human Verification that kept the bots away pre-SSO login, although not the human variety of spammers.

---

