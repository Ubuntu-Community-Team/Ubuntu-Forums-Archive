---
title: "SSO login page doesn't like the underscore in my user name."
date: 2016-06-29
forum: Forum Feedback &amp; Help
---

### Post by yetimon_64 on 2016-06-29
Hi staff and admins,

I just ran into a log in problem with the SSO login page and was locked out of logging into this site for a few hours. There seems to have been some sort of recent changes on the SSO login page that rejected my user name with an underscore in the name.

Every time I tried to log in it kept asking for and then rejecting the name when entered correctly. I have been logging in with the same user name since I opened this account in February last year and only got it rejected for the first time tonight. I could not contact the SSO login admins, the contact page over there seemed to go nowhere, but "thanked" me for the contact etc and said someone would contact me (though there was no way they could know how to do so, as there was no way to input my details :confused:). 

I tried the email address here to contact an admin on the mailing list but have since cancelled the posting there when I got a "moderation" notice as not being a member etc via the email address I used.

As a last resort and by "trial and error" I removed the underscore from my forum user name on my SSO account page and tried logging in here again. It worked. 

This is just for your info and for anyone else who gets their (valid) log in suddenly rejected by the SSO page. Remove any underscores (and I would assume other non standard characters) and try logging in again, it worked for me this time luckily.

Regards, yetimon**_**64. (Note the underscore ! :))

---

### Post by &amp;KyT$0P# on 2016-06-29
The underscore is not the whole story, I was rejected too and it wanted me to change username, email address, and password (I think all for my Ubuntu Forums account).  Not sure how I got around it without making any changes but I'm afraid to log out now :o

EDIT OK I figured out how I got logged in:
1) Go to [https://login.ubuntu.com/]("https://login.ubuntu.com/"), and login to SSO from there
2) Click the "Login with SSO" button here on the forum
3) The page asking to change all this information, now has a link to "exit without updating".  Clicking that goes to the normal SSO confirm login page.

EDIT2 Wait, maybe it's the SSO site itself asking for a "username" now, and nothing to do with Ubuntu Forums account?
EDIT3 Yep that's it - they've added a "username" to the SSO. (Looks like it's OK with my forum username.)

---

### Post by yetimon_64 on 2016-06-29
> **halogen2 said:**
> The underscore is not the whole story, I was rejected too and it wanted me to change username, email address, and password (I think all for my Ubuntu Forums account).  Not sure how I got around it without making any changes but I'm afraid to log out now :o

Yeah, there seem to be some changes going on at the moment over there by the looks of things. Just remember there is a (I think) 24 hour non activity automatic log out in place for this forum. You may need to open a page here at least once a day to retain the same log in, if I recall correctly.

Edit: > EDIT3 Yep that's it - they've added a "username" to the SSO. (Looks like it's OK with my forum username.)
Yes, that is the field on the SSO page that caught me out with the underscore in my username.

---

### Post by coffeecat on 2016-06-29
This has taken us (or me at least) by surprise as well, so I&#8217;m not sure what&#8217;s going on, but I&#8217;ve tested login and I can confirm what you are seeing. However, there&#8217;s an easy way round, as halogen2 describes in one of their edits.

After logging into your Ubuntu One account, you are taken to the &#8220;Personal Details&#8221; page which appears to be asking you to add a &#8220;username&#8221; and reset the password. Ignore all that and click on the &#8220;exit without updating&#8221; link to the right of the orange &#8220;save changes&#8221; button.

That takes you to the Personal Data Request page where you click on the &#8220;Yes, log me in&#8221; orange button, which in turn takes you to the forum, logged in.

Once we have any further details, one of us will post again.

---

### Post by yetimon_64 on 2016-06-29
> **coffeecat said:**
> ... Ignore all that and click on the “exit without updating” link to the right of the orange “save changes” button...
I am pretty sure I tried that early on in the process a couple of times, but kept getting sent back to the page telling me "The site Ubuntu Forums requires that you set a valid username" (see first attached screenshot, email masked). 

It was only when I finally removed the underscore that I was let to log in. (second screenshot, again email masked)

You can see on the second screenshot how by simply removing the underscore the username is now accepted, and even though the underscore is still part of my username here removing it on the SSO page now lets me in.

Cheers, yeti.

---

### Post by TheFu on 2016-07-02
Was just forced to add a "username" to my account here - another useless field. Had to be all lowercase, which is fine, but would be nice to know that BEFORE letting me type something in.

Was also forced to set a password, without providing my old password.  I set a trivial password, which was accepted. Boooo.  Hopefully, the forum mods can do something about this.

It accepted it and logged me in here.

Someone else could do the same thing for other accounts. Don't see how that would be prevented.

---

### Post by coffeecat on 2016-07-02
Threads merged. Please see my response in post #4.

---

### Post by TheFu on 2016-07-02
I feel for you guys today.
Nobody will see these until after they've already navigated the forced login/password change.  I did try to cancel out, BTW. Then tried to reply to a post and was sent back again to add a username and password.  Need to see which password was stored - my old GREAT, no-way-I-can-remember it password or the bonehead one I just set 5 min ago. ... firejail to help me.

Just tested it.  bonehead password has taken over my account.  Ouch.  Time to see if I can take over someone else's account?  Spinning up vpn now.

---

### Post by &amp;KyT$0P# on 2016-07-02
If you're already signed in to SSO, and you fill in the username at [https://login.ubuntu.com/]("https://login.ubuntu.com/") instead of the page to sign-in to Ubuntu Forums, you can keep all other details as-is (and not enter any password)

---

### Post by TheFu on 2016-07-02
> **halogen2 said:**
> If you fill in the username at [https://login.ubuntu.com/]("https://login.ubuntu.com/") instead of the sign-in page, you can keep all other details as-is (and not enter any password)

I was forced to enter "some" password ... just had to be 8 characters or more ... before any username would be accepted.  **Was not asked to enter the old password.** THAT is my concern with this forced process.  Lots of people don't login to the forums for months. What prevents someone else from taking over their account?

---

### Post by coffeecat on 2016-07-02
[size=3]**Reality check time.**[/size]

> **TheFu said:**
> **Was not asked to enter the old password.**

With the page you are talking about, you have already logged into Ubuntu One **with your old password**. There is no security issue, unless you make one. If you are unwise enough to set a "bonehead" password (as you put it) there is nothing that we, Canonical sysadmins, or anyone on planet Earth can do about it. That would be your choice to reduce the security of your account. 

Let's take this slowly.

First of all you log into your Ubuntu One account with your email and your existing password - hopefully a sensible one. If you have not already set an Ubuntu One username (as distinct from the full name field) you are then taken to the Ubuntu One page headed Personal Details where you can add a username and/or change your password. You don't have to, as already pointed out.

The thing that worries me on that page is the phrase, "The site 'Ubuntu Forums' requires that you set a valid username" at the top. Well - I can say that this is not so. This page is nothing to do with Ubuntu Forums. And I notice, when checking the process a few moments ago, that the phrase is no longer showing. So perhaps this is a work in progress by the Ubuntu One people.

> **TheFu said:**
> What prevents someone else from taking over their account?

The only way someone could take over a forum account is if they managed to get hold of the login credentials for the linked Ubuntu One account. And as I have already explained, your concerns about the Ubuntu One password are based on a misunderstanding.

Please, everyone, let's keep clear heads, and try to avoid spreading misinformation.

---

