---
title: "Bandwidth efficiency"
date: 2006-03-10
forum: Forum Feedback &amp; Help
---

### Post by psusi on 2006-03-10
Based on the new message on the forums, it seems there are some bandwidth issues with it.  I just thought I'd point out that it looks like every page contains embedded CSS rather than linking to an external style sheet.  If this one change were made it would lower the bandwidth usage by ~15% ( the style sheet makes up ~15,000 bytes of every page ).  It also looks like there is quite a bit of space used for common things that appear on every page, which could be moved to a shared external linked document.  These two changes are not very hard to make and could cut bandwidth usage by as much as 50%.

A more difficult change would be to change the pages to be generated in XML with a linked XSL style sheet.  The client only needs to download the style sheet once, then each page they visit is very small chunk of XML data that is transformed to html on the client side.  The server can be configured to detect clients that don't understand XSL and perform the translation for them, and cache the results.  I think that at this point though, most modern web browsers support this.  This could potentially cut bandwidth usage by as much as 90%.

Not only would these things help keep the costs of running the servers down, but it makes browsing the forums faster for the users.

---

### Post by kassetra on 2006-03-10
We are limited in what we can do about any of these items by the forum software itself.

In order to actually do most of the items you have described, we'd have to rewrite the forum software itself, actually.

---

### Post by psusi on 2006-03-10
Externalizing the CSS should be a rather simple change to make to it.  

I guess what it comes down to is how much does 1000 GB a moth cost, and is it worth it to improve the forums.

---

### Post by az on 2006-03-10
AFAIK, vBuletin is proprietary, but open source for this purpose - for people to be able to contribute.  Is that so?  And do you think a group from this community would want to collaborate on such a project?

Can Launchpad host projects for non-free-libre software?  Does anyone know?

It would be interesting...

---

### Post by kassetra on 2006-03-10
[quote=psusi]Externalizing the CSS should be a rather simple change to make to it.  

I guess what it comes down to is how much does 1000 GB a moth cost, and is it worth it to improve the forums.[/quote]

Not exactly.  Vbulletin uses an internal templating system - so it's a little difficult to externalize the CSS without having to make the forum software jump through a bunch of extra hoops (currently) - which wouldn't justify the change.

---

### Post by kassetra on 2006-03-10
[quote=azz]AFAIK, vBuletin is proprietary, but open source for this purpose - for people to be able to contribute. Is that so? And do you think a group from this community would want to collaborate on such a project?

Can Launchpad host projects for non-free-libre software?  Does anyone know?

It would be interesting...[/quote]

Open-Source... if you purchase a license to get the source first - and the license prohibits distribution of the source in any fashion, so posting it on launchpad is probably not going to fly.

Now, if every 'developer' purchased a license and the source was put onto a special password-protected site where only people that had purchased a license could get access to the code (or where a developer was a non-profit and other developers were his employees...) ... then it might be ok.  These would be issues that would need to be discussed with Jelsoft first.

---

### Post by Lord Illidan on 2006-03-10
Will removing fancy avatars help? I am willing to sacrifice my beloved ogre mage jumping on a peon..

---

### Post by kassetra on 2006-03-10
[quote=Lord Illidan]Will removing fancy avatars help? I am willing to sacrifice my beloved ogre mage jumping on a peon..[/quote] 
LOL no no no.  We're fine now.  :)  (As we've tried to say numerous times.)

We have over 12,000 registered users that visit the forums daily, along with search engines crawling our data and an unknown number of guests visiting. 1000Gb worth of bandwidth wasn't enough at this point to sustain the forums.

It has nothing to do with code, images, or css files. We could be stripped clean of everything and we'd still have had issues - we simply outgrew our training wheels. ;)

---

### Post by Trel on 2006-03-17
Let me throw my two cents in.. ;)

While vBulletin has its template system it also has to play by the normal HTTP specification rules. You might not be able to make the CSS external (which I am almost certain you can) but, for the sake of this post I'll just assume it can't be done.

Modules such as mod_expires and mod_deflate will be able to help improve the bandwidth situation here while also decreasing loadtime for those of us on slower connections sometimes.. (Treo 650 as an EDGE modem via bluetooth).

Lets assume for a moment that everyone views the forum via a broadband connection (DSL or faster) so compressing it for the sake of speed of loading is a nonissue. What kind of bandwidth savings might be possible?

In my experience with large active forums over the course of the month at least 60% of the membership will visit 5 - 10 forum pages. Taking this into account we can assume that 48,000 out of 80,000 members will visit at least 5 pages over the course of 30 days.

With each page averaging 100KB of HTML/text content (I checked 10 different pages and averaged them) that is 22GB just for text content for 5 pageviews for 60% of the members. That doesn't include any slashdotting, guest users, users that browse 100 or more pages each week.. or any image content at all.

So what kind of savings could be expected from compression?

By my calculations the estimated 22GB could be made into 3.38 - 3.14GB with proper compression. Multiply that up as far as you like and you can see the bandwidth savings not to mention page load savings will be massive.

Just a thought.

---

### Post by psusi on 2006-03-20
Why is it that the ubuntu forums are using a not only a non free buletin board system, but one that also apparently is horribly inefficient and poorly written such that it is too hard to fix to not waste so much bandwidth?

It really is rediculous that more than 50% of each page served is redundant formatting that should be an external stylesheet.  

Wouldn't it behove the ubuntu community to use the same kind of software ( f/oss ) for it's message board as it promotes in the distribution itself?

---

### Post by kassetra on 2006-03-20
[quote=psusi]Why is it that the ubuntu forums are using a not only a non free buletin board system, but one that also apparently is horribly inefficient and poorly written such that it is too hard to fix to not waste so much bandwidth?

It really is rediculous that more than 50% of each page served is redundant formatting that should be an external stylesheet.  

Wouldn't it behove the ubuntu community to use the same kind of software ( f/oss ) for it's message board as it promotes in the distribution itself?[/quote] 
This has been discussed many, many times on this forum.

The simple answer is that we cannot use any other software because the features we require are only available in the software we are using.

You can read more [here]("http://ubuntuforums.org/showthread.php?t=23695&highlight=vbulletin+forum+software"), [here]("http://ubuntuforums.org/showthread.php?t=85464&highlight=vbulletin+forum+software"), and [here]("http://ubuntuforums.org/showthread.php?t=47391&highlight=vbulletin+forum+software").

If you would like to make suggestions, please remember that negative comments are not the best way to get noticed.

---

### Post by Trel on 2006-03-21
[QUOTE=kassetra]This has been discussed many, many times on this forum.

The simple answer is that we cannot use any other software because the features we require are only available in the software we are using.

You can read more [here]("http://ubuntuforums.org/showthread.php?t=23695&highlight=vbulletin+forum+software"), [here]("http://ubuntuforums.org/showthread.php?t=85464&highlight=vbulletin+forum+software"), and [here]("http://ubuntuforums.org/showthread.php?t=47391&highlight=vbulletin+forum+software").

If you would like to make suggestions, please remember that negative comments are not the best way to get noticed.[/QUOTE]

Really the excuse you've given isn't valid. While vBulletin might have these features integrated already we can (for the most part) build a phpBB installation with many AJAX features, quick replies, and other features just like vBulletin.

Some suggesting phpBB likely know that and are a bit.. :rolleyes: over the reason.

A valid reason in my eyes would be to say that phpBB isn't ready yet and while the debate might continue a bit we can agree that phpBB 2.0.x isn't ready to compare to vBulletin 3.5.x.

With all that said phpBB 3.0.x will be ready in the future and is entering its first betas. I hope the staff here considers moving to it once it has been proven stable and solid. :)

---

### Post by kassetra on 2006-03-21
[quote=Trel]Really the excuse you've given isn't valid.
With all that said phpBB 3.0.x will be ready in the future and is entering its first betas. I hope the staff here considers moving to it once it has been proven stable and solid. :)[/quote] 
As we have said, far too many times, no other software has the features we need.

If phpBB had these features, we would consider it.  phpBB does *not* have the features we require, in any way, shape or form.

Since no other software has these features we require, we are not moving.  It has nothing to do with stability.

Call it an excuse if you like, but it will not change the reality; we cannot use anything else currently.

---

