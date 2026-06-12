---
title: "Forum SEO issue: duplicate content; profile spam"
date: 2011-02-18
forum: Forum Feedback &amp; Help
---

### Post by Charybdisz on 2011-02-18
Yo,

you should eliminate duplicate content on this forum, like these:

```
www.swiss.ubuntuforums.org
www.backports.ubuntuforums.org
www.uluga.ubuntuforums.org
georgia.ubuntuforums.org
ubuntu-virginia.ubuntuforums.org
ubuntu-ky.ubuntuforums.org
art.ubuntuforums.org

+ the printer friendly pages
```

This is very harmful in terms of SEO. Please eliminate these sub domains, because they have duplicate content.

And it is a problem that the profile pages of the forum members are publicly viewable, and it is possible to insert dofollow links into profiles. So a lot of people register at this forum, drop a link to his website, then never comes back. That's why there are 1.2 million registered members :)

There are programs which can fully automate forum profile spamming, google "sick submitter" or "xrumer". These tasks are fully automated: registering, breaking the captcha, confirming email, waiting 1-2 weeks, then inserting links into the profiles.

Solution: utilize the nofollow attribute, or make profile pages private (only visible to logged in members).

---

### Post by Joeb454 on 2011-02-18
The subdomains are merely apache redirects. You could access the forum via [http://charybdisz.ubuntuforums.org](http://charybdisz.ubuntuforums.org) if you really wanted to ;)

As for the spam, we are looking at ways to reduce the amount we have as always, however, I'm not sure that some of your suggestions are possible without editing vBulletin code directly.

---

### Post by Charybdisz on 2011-02-18
> **Joeb454 said:**
> The subdomains are merely apache redirects. You could access the forum via [http://charybdisz.ubuntuforums.org](http://charybdisz.ubuntuforums.org) if you really wanted to ;)

Yes, that's the problem. You should redirect charybdisz.ubuntuforums.org permanently to ubuntuforums.org (301 redirect), or exclude it from crawling via the robots.txt file, or utilize the canonical tag. This is what I am talking about, the duplicate content is when you have exactly the same content on different pages or subdomains, and you do not 301 redirect the duplicate pages to the original page. Same thing with the printer friendly pages.

**More info: [Duplicate content - Google Webmaster Tools Help]("http://www.google.com/support/webmasters/bin/answer.py?hl=en&answer=66359")**

> **Joeb454 said:**
> As for the spam, we are looking at ways to reduce the amount we have as always, however, I'm not sure that some of your suggestions are possible without editing vBulletin code directly.

[www.vbseo.com](www.vbseo.com) is your friend.

---

### Post by dh04000 on 2011-02-18
> **Joeb454 said:**
> The subdomains are merely apache redirects. You could access the forum via [http://charybdisz.ubuntuforums.org](http://charybdisz.ubuntuforums.org) if you really wanted to ;)

As for the spam, we are looking at ways to reduce the amount we have as always, however, I'm not sure that some of your suggestions are possible without editing vBulletin code directly.


I don't remember where, but in a stickied thread you explained that the reason WHY vBulletin is used in this forum, it is because the source is provided and since your allowed to modify it anyway you want as long as you don't redistribute it. (And cuz it has features we need)

So, anything to reduce spam, and therefore help with the current server issues and prevent future would be welcome.

Just my 0.02 cents.

---

