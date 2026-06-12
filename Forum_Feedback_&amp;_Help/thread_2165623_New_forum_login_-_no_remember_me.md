---
title: "New forum login - no remember me?"
date: 2013-07-31
forum: Forum Feedback &amp; Help
---

### Post by ajgreeny on 2013-07-31
Under the old forum setup I was always logged in automatically whenever I opened a forum page.

That no longer happens and after logging in I am not taken back to the page I was previously viewing but to the main page of the forum; not very useful!

Is this simply a problem related to the new setup being exactly that, ie new, and not yet completely finished, or am I missing some simple way of auto-logging in whenever I visit the forum?

---

### Post by CharlesA on 2013-07-31
I think it's due to SSO.

So far I am able to close the browser and just click the login with SSO button and it logs me in after verifying what information I want to share.

---

### Post by cariboo on 2013-07-31
As far as I recall, the time-out is set to 2 hours, and we are still investigating the remember me option.

---

### Post by coffeecat on 2013-08-01
> **ajgreeny said:**
> Under the old forum setup I was always logged in automatically whenever I opened a forum page.

I don't remember any auto-login. Did you perhaps use remember me and never closed the browser and/or not cleared cookies? In which case you would have been permanently logged in. 

There is a security angle of course. If a non-staff member was permanently logged in and a malicious person gained access to the machine, then the worst that could happen is that spam or abusive posts could have been posted in your name.

However, if an admin or moderator was permanently logged in and a malicious person gained access to the machine.... Well. :(

We'll be guided by Canonical sysadmins on this.

---

### Post by mips on 2013-08-01
Have to agree that this clicking, opening a new page, being redirected, unselecting info, clicking and being directed back to the forums is a bit of a pita and a long way to get into the forums.

---

### Post by Zill on 2013-08-01
The Ubuntu Desktop Team has a "[Mission Statement]("https://wiki.ubuntu.com/DesktopTeam/Mission")" that defines usability as "A usable desktop aids the user in their work, but does not give them challenging obstacles."

IMHO, the hoops that SSO requires us to jump through just to login (and stay logged-in!) to the forums currently falls somewhat short of this worthy objective. :-(

---

### Post by Sector11 on 2013-08-01
> **mips said:**
> Have to agree that this clicking, opening a new page, being redirected, unselecting info, clicking and being directed back to the forums is a bit of a pita and a long way to get into the forums.

+1 on that.

They know who we are, proof is; we get emails saying a new post ... blah blah ...

... but when I click on it, it doesn't take me to the new post.  I have to SSO log in, then click on the link again.  :(

I've had to do that three times in the past hour ... testing trying to get it to remember me.  ](*,) ](*,)  NO GO!

---

### Post by ventrical on 2013-08-01
Looks like it just got fixed.  I opened a new tab, ubuntuforums.. an voila' auto logon... no more clicking SSO :)

---

### Post by mips on 2013-08-01
> **ventrical said:**
> Looks like it just got fixed.  I opened a new tab, ubuntuforums.. an voila' auto logon... no more clicking SSO :)

+1 Just tried it now and it seems to work. I'll let my wrath subside for now :D

---

### Post by Sector11 on 2013-08-01
> **ventrical said:**
> Looks like it just got fixed.  I opened a new tab, ubuntuforums.. an voila' auto logon... no more clicking SSO :)

If you had your browser open that doesn't count.  Closed down and come back ... it still required a log in through OSS.

Time with patience --- I'm sure they will get it fixed.

---

### Post by ventrical on 2013-08-01
> **Sector11 said:**
> If you had your browser open that doesn't count.  Closed down and come back ... it still required a log in through OSS.

Time with patience --- I'm sure they will get it fixed.


Well.. no .. it is not logging me out anymore like it did. I can stay on line .. go do something else (which I have been doing all day) and I am not bumped anymore, so I don't really have to log back in. I can then close an ubuntuforums tab. reopen it and I am back online.

however .. I'll try a re-boot... but just a note .. I never close my browser or my tabs. A versatile  thing about ff and Ubuntu, on re-boot and I am right back where I was.

---

### Post by ventrical on 2013-08-01
Ok .. I rebooted and of course had to log on with SSO (no remember me option) but then I closed the tab and reopened a new tab with UbuntuForums and it remembered me, no click SSO. It was not doing this before .. plus it was bumping off after about 2 minutes of inactivity.

Regards..

---

### Post by ajgreeny on 2013-08-01
Like a lot of users, I do **not** keep my browser permanently open and have no intention of doing so; when I have finished browsing I close it down, but leave my xubuntu session running.  At the next start of my browser (note; just the browser, not a new xubuntu session or reboot) I have to jump through the same SSO login hoops again, which as I said previously was not required with the "remember me" option available previously.

---

### Post by ELD on 2013-08-05
So this may be a dumb question but it wasn't stated anywhere that I can see, will we get an auto login back? Quite annoying having to re-login everytime.

---

### Post by bapoumba on 2013-08-05
Moved to FFH.
As per the new login method, as long as you are logged into UOne in your browser session, you can return to the forums without login in again.

---

### Post by ELD on 2013-08-05
That also has no stay logged in function, this is a major drawback of this new login system.

Are there plans to allow us to stay logged in? I fear this will make a few people move.

---

### Post by bapoumba on 2013-08-05
I believe so, but it is not very high on the pile because there are other more urgent things that need to be taken care of.

---

### Post by markbl on 2013-08-06
> **bapoumba said:**
> I believe so, but it is not very high on the pile because there are other more urgent things that need to be taken care of.
C'mon, having to log in everytime we visit this site is an absolute PITA. Surely somebody please tell me this is a high priority issue?

I don't know of any other forum which forces you through such a rigmarole every time you visit.

---

### Post by bapoumba on 2013-08-06
Please read these :
[http://ubuntuforums.org/showthread.php?t=2164064](http://ubuntuforums.org/showthread.php?t=2164064)
[http://ubuntuforums.org/showthread.php?t=2164051](http://ubuntuforums.org/showthread.php?t=2164051)

It is part of the new login process that was setup after the forums were compromised.

---

### Post by Uncle Spellbinder on 2013-08-06
I think we all know WHY this was instituted. Nevertheless, logging in each time is an UNNECESSARY precaution to protect the forum userbase. At least in my opinion. There are far more popular forums who've been hacked and or compromised in the past. NONE of them force their users to log in each time they arrive. It makes NO SENSE AT ALL that if I leave the forums and come back a few minutes later, I'm forced to log in again. Quite ludicrous. 

Just my 2 cents. Not trying to be confrontational with any of the forum mods.

---

### Post by orb9220 on 2013-08-06
Yep agree and as a user don't like the "Low priority" tag given it.
And personally don't care if it's only a couple of extra clicks.
But is annoying enough to be an issue every time I check the forums.
.

---

### Post by vasa1 on 2013-08-07
It's possible that this is a temporary measure until they get things sorted out. It's possible their first priority was getting the Forums back online.

Other "Ubuntu" resources, Ask Ubuntu (not owned by Canonical), help.ubuntu.com, and Launchpad, still remember us after shutting down the browser and so I feel UF will come around. BTW, I sign into those sites with a Google account, not a Ubuntu One account, if it matters.
 
Even if it's a permanent measure, while it certainly is a few clicks more, it's really not a big deal, just unusual..

---

### Post by varunendra on 2013-08-07
> **ELD said:**
> Quite annoying having to re-login everytime.Indeed.

> **bapoumba said:**
> As per the new login method, as long as you are logged into UOne in your browser session, you can return to the forums without login in again...then I have a bug report to submit - My last or second last post on the forums required me to re-login to submit my post, although I was already logged in on the "login with SSO" page. So I only needed to confirm the details I wanted to share, but then it redirected me to the forums index page. A "back > back > copy content > refresh > submit" did the job, but it was obviously quite annoying and could be a major let down if I had to type the post again.

The "required to re-login" thing was same as old login method when the "remember me" option was not checked and there was a long gap between starting and finishing a post (usual for me). But the redirect to the index page was a shock.

> **ELD said:**
> I fear this will make a few people move.
..or at least make them far less interested, like me.

> **bapoumba said:**
> I believe so, but it is not very high on the pile
Disappointing. I hope the time comes soon when it'll be taken care of.

PS: Very nice to see you back bapoumba :)

---

### Post by coffeecat on 2013-08-07
> **Uncle Spellbinder said:**
> I leave the forums and come back a few minutes later, I'm forced to log in again. Quite ludicrous.

Not a few - 120. Until this has been looked at properly by sysadmins, the session timeout has been increased to 2 hours. I certainly don't experience any problem coming back to the forum a "few" minutes later.

> **varunendra said:**
> My last or second last post on the forums required me to re-login to submit my post, although I was already logged in on the "login with SSO" page. So I only needed to confirm the details I wanted to share, but then it redirected me to the forums index page. A "back > back > copy content > refresh > submit" did the job, but it was obviously quite annoying and could be a major let down if I had to type the post again.

This should only happen if your last activity - a page refresh, move to another page or any activity - was more than 2 hours previously. Are you sure that you had been continuously active up until a few minutes before that happened?

---

### Post by varunendra on 2013-08-07
> **coffeecat said:**
> This should only happen if your last activity - a page refresh, move to another page or any activity - was more than 2 hours previously. Are you sure that you had been continuously active up until a few minutes before that happened?
No, there was quite a long delay in between. Although I believe it was less than an hour *(was just one line of answer, only I moved away for a while before inserting the link and hitting the "submit" button)*, but right now, I'm not sure about the duration of the inactivity.

What I can confirm is that just a few minutes ago, I submitted another post with almost an hour of inactivity between starting and submitting the post *(had to move away again)*, and the logout issue didn't occur this time. So you may be right about the 2 hr thing.

But the redirect to index page thing is still an issue, for example, when you are browsing threads without being logged in, click on "Reply with quote" > log in and get redirected to index page instead of the the thread you were trying to answer.

---

### Post by erasmusp on 2013-08-07
I am not sure why this should be an issue. First of all the forum gets compromised because the rules were laid back and made things "easier" to reconnect to the forum. Now that the rules are strengthened to try and block any compromise that might happen everyone complains because it takes a extra click or two to get to the forum. Are we as humans really that lazy that we are prepared to risk being hacked just to make life a bit easier?
 This is like airport security - it really has been beefed up in the last 10 years to protect us, yet a lot of people will squeal because it is inconveniencing them...

Phill

---

### Post by bapoumba on 2013-08-07
> **varunendra said:**
> 
PS: Very nice to see you back bapoumba :)

Hello varunendra :)

---

### Post by Pinoy Tux on 2013-08-08
> **erasmusp said:**
> I am not sure why this should be an issue. First of all the forum gets compromised because the rules were laid back and made things "easier" to reconnect to the forum. Now that the rules are strengthened to try and block any compromise that might happen everyone complains because it takes a extra click or two to get to the forum. Are we as humans really that lazy that we are prepared to risk being hacked just to make life a bit easier?

+1

Users only need to login if they want to reply to a thread.  I don't see a reason to log in when I just want to read threads.

It's a minor inconvenience though, when the redirection after login goes to the index page instead of the actual thread.  Hopefully, the admins will fix this.  In the meantime, all it takes to get back on track is right-click the browser's back button, choose the original thread, then refresh the browser.  Three easy clicks that takes only a moment to do.  Now, is that such a big deal?  I don't think so, at least in my book.

Usually, I open several tabs when I get forum notifications.  Naturally, all those tabs are not logged in.  If I need to reply to more than one of those non-logged-in tabs, I just log in on one tab, then refresh the other tabs (F5 key or the refresh button) and that takes care of it.  Again, is that such a big deal?

**Users, you need to _ADAPT_.** #-o

---

### Post by bapoumba on 2013-08-08
> **Pinoy Tux said:**
> 
Usually, I open several tabs when I get forum notifications.  Naturally, all those tabs are not logged in.  If I need to reply to more than one of those non-logged-in tabs, I just log in on one tab, then refresh the other tabs (F5 key or the refresh button) and that takes care of it.  Again, is that such a big deal?


This is how I do it from notifications. Otherwise, I just log into Ubuntu One first, even before going to the forums.

---

### Post by mc4man on 2013-08-08
Don't see it as a big deal either as the main reason (here) for remember me is no longer an issue. 
Between the increased timeout & autosave being logged out & possibly losing a post/reply is fairly unlikely.

That being said it was convenient & I'd certainly use if returned. (old dog habits are hard to change
I don't see how it affects security when used by users, I'm perpetually logged into Launchpad, Ask Ubuntu & Discourse with no issues.

In lieu of it being returned I'd love to see the timeout increased to 8 -12 hrs or so, then for those that choose there would be a workaround, for at least  firefox users, to allow closing the browser session but stay logged in for the timeout length

---

### Post by Buntu Bunny on 2013-08-09
I realize there is a session timeout in place, but I find that sometimes I'm logged out in the middle of a task, such as writing a post or PM. Having to log back in loses the data. I don't suppose anything can be done about that(?)

---

### Post by coffeecat on 2013-08-09
Post moved - please see previous discussion.

---

### Post by prodigy_ on 2013-08-09
> **Pinoy Tux said:**
> Users only need to login if they want to reply to a thread.
Except those of us who prefer our customized forum view settings.

---

### Post by mc4man on 2013-08-09
> **Buntu Bunny said:**
> I realize there is a session timeout in place, but I find that sometimes I'm logged out in the middle of a task, such as writing a post or PM. Having to log back in loses the data. I don't suppose anything can be done about that(?)
You should get an option to restore saved content, at least for replies to a thread. For example I started this reply, closed the browser, re-opened, logged in, came back to same thread, replied again to your post & there was the option to restore in red at bottom of reply box.
(obviously not an ideal path back but works.

This was using FF on Win7 which does have some other issues with the new methods, FF on linux is a bit better.

If I know I'll be here a while, (on FF with linux), then I'll edit the bb_sessionhash cookie & give it a date to expire
(only lasts for 2 hrs of inactivity so date chosen is irrelevant

In the past when being logged out during a reply (with the very short time out) I believe replies weren't being seen as activity, maybe that's still the case?? (though you should still get 2 hrs to retrieve & complete a post, ect.

---

### Post by sgage on 2013-08-09
Is there any way to make the SSO login persistent across boots, as of old? I find it annoying to have to sign in all the time...

---

### Post by mikewhatever on 2013-08-09
Try allowing cookies for [https://login.ubuntu.com/](https://login.ubuntu.com/). It should remember you that way.

---

### Post by QIII on 2013-08-09
*Moved to Forum** Feedback & Help***

The Ubuntu + 1 forum is for discussion of the development version of Ubuntu -- currently 13.10.

Not really an Ubuntu Forums issue either, actually.  This is one for Canonical IS.

The Admins have been in discussion with Canonical IS about this.  If one of them stops by, they can give you any details that they might be willing to.

---

### Post by sanderj on 2013-08-09
> **mikewhatever said:**
> Try allowing cookies for [https://login.ubuntu.com/](https://login.ubuntu.com/). It should remember you that way.

Is that something I should set in my browser (Chromium)? AFAIK I do not block cookies. I do run Ghostery, but that does not say anything other than blocking a facebook thing.

---

### Post by coffeecat on 2013-08-09
Threads merged.

---

### Post by ikt on 2013-08-10
> **sanderj said:**
> Is that something I should set in my browser (Chromium)? AFAIK I do not block cookies. I do run Ghostery, but that does not say anything other than blocking a facebook thing.

I don't believe that will work, as coffeecat said:

> **coffeecat said:**
> Not a few - 120. Until this has been looked at properly by sysadmins, the session timeout has been increased to 2 hours.

The cookie or session is set to expire after 2 hours anyway.

As someone who is logging in 3-10 times a day at the moment you're not the only one who is eagerly waiting for the 'remember me' option.

---

### Post by wildmanne39 on 2013-08-10
Indeed!!!>  As someone who is logging in 3-10 times a day at the moment you're not the only one who is eagerly waiting for the 'remember me' option. We are all in the same boat at the moment so please do not rock it.:P

---

### Post by Cavsfan on 2013-08-11
I don't see any problem. If your browser stores the passwords, it's just a couple extra clicks and viola you're in! ;)
I used Firefox exclusively and it worked fine but, now using Chromium and it stores the passwords as well and it's just a couple of extra clicks.

That is not that bad if that is what it takes to prevent another take down of this forum. That seemed like months when this thing went down. :(

---

### Post by Cavsfan on 2013-08-11
I just double click in the web address at the top until it's all highlighted. Then type "ub" and when I see the forum I click on it. 
Then I click "Login with sso", then I pause until I see "You are logging in to http://ubuntuforums.org" and I click on "Yes, log me in" and I am there.
That is not really that bad is it?

Haven't ever seen it time me out. :P

---

### Post by squakie on 2013-08-14
I hope I'm not rocking the boat with this reply - it is meant as something for the Is team at C. to see.

I also have problems with this.  I have a lot of threads bookmarked in my browser and with the old way I could click them and go right to the thread and post a reply.  Now it makes me go through the login, which in turn dumps me onto the Forum sub-forum index page - not what I had bookmarked.

Please understand - I know this isn't the forum's fault.  I know how much work it was for forum staff to work with C. IS staff and get things going again.  I know the new login is in place for EVERYONE'S protection - hopefully no more stolen email addresses, etc..

So, not direct to the forum staff at all - just C. IS staff:  I appreciate the work done for a more secure site, but some of us are indeed paying a most inconvenient price for it.  Please, if possible, find a way to remember us beyond a few hours and most importantly across reboots.

I'm just a small fish in a pond full of big fishes who have much more pressing needs than to have to deal with complaints on this.

---

### Post by ELD on 2013-08-14
This is really annoying, i came back after getting the above reply, went to login and was sent back to the forum index again. This new login isn't great.

What is so hard about letting us stay logged in? Cookies are not difficult, if the canonical guys find it hard to create a stay logged in function for SSO then they need new staff.

Sorry but it's true and it's fracking annoying me to the point that i visit here far far far less often. It's not just the login issue it's the redirection of having to damn find where you last where when you wanted to login.

---

### Post by bapoumba on 2013-08-14
A ticket with Canonical IS is in the tubes on the remember me status.

For now, as has already been said earlier by others, I've adopted new routine. First of, even before going to UF, log into U1 (I always clear everything when I quit the browser) > then log into main UF page > then open whichever page I want from my email notifications or bookmarks. I do not have a better alternative to offer for now. Maybe others have different routines.

---

### Post by Cavsfan on 2013-08-14
> **bapoumba said:**
> A ticket with Canonical IS is in the tubes on the remember me status.

For now, as has already been said earlier by others, I've adopted new routine. First of, even before going to UF, log into U1 (I always clear everything when I quit the browser) > then log into main UF page > then open whichever page I want from my email notifications or bookmarks. I do not have a better alternative to offer for now. Maybe others have different routines.

+1
Login first and then go to your bookmarks. That works.

---

### Post by varunendra on 2013-08-14
There are always workarounds...

...workarounds are not fixes.

There is a good reason why people seek fixes despite the existence and knowledge of workarounds.

---

### Post by Elfy on 2013-08-15
This thread can go round and round in circles for as long as people want.

The ticket has been done for IS - they will look at it when they look at it - we have no control over them at all.

When it's done or being physically looked at by then - until then talk amongst yourselves.

Thanks.

---

### Post by varunendra on 2013-08-15
> **Elfy said:**
> This thread can go round and round in circles for as long as people want.
..agreed, and it will unless the thread is locked, not that I'm recommending that ;)

---

### Post by squakie on 2013-08-15
Sorry if I rocked the boat - I really didn't mean to.  I'll follow your advice until Canonical IS comes up with something.  Thanks again for all your hard work!

---

### Post by Elfy on 2013-08-15
> **squakie said:**
> Sorry if I rocked the boat - I really didn't mean to.  I'll follow your advice until Canonical IS comes up with something.  Thanks again for all your hard work!

No-one's rocking the boat :)

Believe me when I say I want Remember Me back as well, I have to login twice to admincp in ADDITION to anything you might have to do.

All I'm doing is putting the real position here - rather than hearsay.

---

### Post by apollothethird on 2013-08-22
Can anyone tell me if there is a way to stay logged in to the forum?  In the past I was able to save my info in the browser and use the stay logged in feature.  That means any time I visit I'd automatically be logged in.  If I clicked on a bookmark from my browser or a link from the Web I'd already be logged in.

The feature is missed most when I get an email notification with a like to a subscribed thread.  In the past clicking on the link from my email would take me directly to the page of the first unread message.  Now I come to a screen with an option to "Login with SSO".

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by oldos2er on 2013-08-22
Moved to FF&H.

---

### Post by mc4man on 2013-08-22
discussed here, maybe it'll come back, maybe it won't
[http://ubuntuforums.org/showthread.php?t=2165623](http://ubuntuforums.org/showthread.php?t=2165623)
Atm you have a 2 hr limit of inactivity to stay logged in as long as you don't exit the browser 
(in firefox that session cookie can be edited to allow ending the browser session & staying logged in but the 2 hr. limit remains

---

### Post by vasa1 on 2013-08-22
> **mc4man said:**
> discussed here, maybe it'll come back, maybe it won't
[http://ubuntuforums.org/showthread.php?t=2165623](http://ubuntuforums.org/showthread.php?t=2165623)
Atm you have a 2 hr limit of inactivity to stay logged in as long as you don't exit the browser 
(**in firefox that session cookie can be edited to allow ending the browser session & staying logged in** but the 2 hr. limit remains
Could you please explain the part in bold?

---

### Post by SeijiSensei on 2013-08-22
Why was two hours chosen?  For most of us that visit the forums multiple times each day, that's way too short.  Why can't the cookie length be something like 12 or 24 hours?  (I'd prefer it to be a month myself.)  

I've read [both]("http://ubuntuforums.org/showthread.php?t=2164051") [postings]("http://ubuntuforums.org/showthread.php?t=2164064") about the breach and do not really see how any of that relates to the length of a browser session in the forums.

---

### Post by apollothethird on 2013-08-22
> **vasa1 said:**
> Could you please explain the part in bold?

The problem that we are having now isn't related to the browser timeout limit.  It's related to a feature that is included with most boards that allows autologin.  I'm sure the autologin has something to do with a cookie saved on the server which retains session information where the user can continue auto logging in from that computer until he logs out.

This is what made the clicking on the NewPost link from an email notice work.

You can demonstrate this by choosing the autologin feature from any other forum such as [http://linuxquestions.org](http://linuxquestions.org), [http://forums.apollo3.com](http://forums.apollo3.com), [http://stackoverflow.com/](http://stackoverflow.com/), [http://www.google.com](http://www.google.com), [http://mail.yahoo.com](http://mail.yahoo.com) etc.

Notice that you can select the remember me or autologin feature, then the next day, week, or month that you click on the link from that same computer, you'll already be logged in.  You won't be prompts to log in and start a two hour session.

I would consider it a security concern to have to tamper with the browser sessions to try to figure out how to stay logged in or autologged into this forum.  I hope this would be a feature and convenience that you will bring back.  It was always like that in the past.

Thanks in advance if the administrators will look into this (possibly along with the VBulletin board support team) and try to restore this convenience.

Thanks in advance for any consideration.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by cariboo on 2013-08-22
Merged two similar threads.

---

### Post by mc4man on 2013-08-22
> **vasa1 said:**
> Could you please explain the part in bold?
See screen here, I'm sure you can figure out, the date chosen is irrelevant, I click the + sign once & save edit. All you're doing is changing the expire from session end to a date
[http://ubuntuforums.org/showthread.php?t=2165623&p=12751053&viewfull=1#post12751053](http://ubuntuforums.org/showthread.php?t=2165623&p=12751053&viewfull=1#post12751053)

With no autologin it's of limited value but does help for those like myself you close FF out all the time out of habit.
(If the inactivity timeout was substantially longer then it could replace autologin until such time as it returns, if it does.

---

### Post by vasa1 on 2013-08-22
> **mc4man said:**
> See screen here, I'm sure you can figure out, the date chosen is irrelevant, I click the + sign once & save edit. All you're doing is changing the expire from session end to a date
[http://ubuntuforums.org/showthread.php?t=2165623&p=12751053&viewfull=1#post12751053](http://ubuntuforums.org/showthread.php?t=2165623&p=12751053&viewfull=1#post12751053)

With no autologin it's of limited value but does help for those like myself you close FF out all the time out of habit.
(If the inactivity timeout was substantially longer then it could replace autologin until such time as it returns, if it does.
Okay, thanks for explaining! I don't have Cookie Manager installed and so didn't understand the " click the + sign once & save edit" but now it's clear.

---

### Post by apollothethird on 2013-08-23
I had searched for a thread such as this before I posted my message.  I'm glad for the merge of the two threads.  I was surprised (when I couldn't find a reference to this problem) that it wasn't being discussed.  For a while I thought that I was the only one that was noticing this.

I read all the messages.  Some of the messages are suggesting that this issue isn't considered a high priority item.  There are numerous workarounds  that are tossed into this thread, as if that should be the fix.

I already had workarounds that were annoying, and work just as well as the other workarounds that are posted.  I can't use the one that appears to be the most accepted, “FF the loading of a Cookie Manager and specific settings”.  I have FF installed, but I use Opera for my serious forum participation.  Opera has some word warp features that makes forum reading much easier than the other 4 browsers I have, and use for other purposes.

I also have 915 book marks in Opera.  Many of them are reference form threads where I pickup where I left off.  I only have a few 10's in the other browsers.

It would be a shame for me to loose the convenience of my forum browsing over something that I believe could easily be resolved on the server side it the matter were given serious attention.

The remember-me features is very important.  Many people use those features/conveniences and don't even realize what they are doing.  When the convenience is missing, they would never make a comment.  The would have a hard time finding the workaround threads (as I did), and many would never be able to think of descriptive words to even report it as a problem.  So the masses will go without the convenience.

After posting a question, when they come back they will stumble on their answer with trial and error.  If the fix works it would be come less likely that would put so much energy into coming back and finding out where they left off so that they could mark the topic solved.  So I'm sure, followups will suffer.

People will also often find themselves rereading things they have already read, because they are not performing the steps and workarounds to get back to the new messages.  Some people will have 15 or 20 minute windows to spend on the forum and spend most of that time trying to figure out where they left off.  By the time they locate their place, they have spent their computer time and may be off to something else.

I know I'm spending a lot of words to describe something that I consider very simple.  But I'm trying to stress the importance of bringing back the remember-me feature.  Unless enough people understand the importance of it, it'll stay something of low priority that will cause such a lost to our community.

If the managers can't figure out how to incorporate this with SSO, maybe they should go back to the vBulletin board database, or use some different database.  One of the forms I used to frequent so much, [http://www.vatsim.net](http://www.vatsim.net) ) uses a different database from the original vBulletin board database and they have no problems with the remember-me function.  They use a database that manages a flight server and a number of other versions of bulletin boards from their many divisions.

Many forum systems use Facebook, Google and other authentications and the remember-me feature works.

I can't believe this functionality would be so hard if it were taking serious, by the people who are actually developing the most powerful OS on the planet.

Again, when someone has a question, they will go through anything possible to go through to get their message posted and find their answer.  But they won't go though that maze as a casual thing when it comes to followup and giving back to the community after their emergency or issue is resolved.  We need to make it easy and convenient for them to perform that next step.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by coffeecat on 2013-08-23
> **apollothethird said:**
> 
I can't believe this functionality would be so hard if it were taking serious, by the people who are actually developing the most powerful OS on the planet.


The Ubuntu developers have absolutely nothing to do with this, and perhaps you missed this:

> **Elfy said:**
> This thread can go round and round in circles for as long as people want.

The ticket has been done for IS - they will look at it when they look at it - we have no control over them at all.

When it's done or being physically looked at by then - until then talk amongst yourselves.

Thanks.

@everyone, a ticket has been raised for Canonical IS, the sysadmin team who deal with all servers in the Canonical/Ubuntu ecosystem, to deal with this. As Elfy said, you are welcome to talk amongst yourselves, but it won't make it happen any faster, since the sysadmin team have their own set of priorities and a very large number of support tickets to work through, not just ours.

---

### Post by apollothethird on 2013-08-23
> **coffeecat said:**
> The Ubuntu developers have absolutely nothing to do with this, and perhaps you missed this:

Actually I didn't miss that:

> 
Originally Posted by Elfy  
This thread can go round and round in circles for as long as people want.

 The ticket has been done for IS - they will look at it when they look at it - we have no control over them at all.

 When it's done or being physically looked at by then - until then talk amongst yourselves.

 Thanks.

 I read it and thought my detailed message had addressed that, plus a number of other messages from the thread.  I read all of them.  I believe you missed the gist of my message.

As far as the developers having nothing to do with it, I don't think that is fully correct.  Also, if the developers are not involved or concerned I believe that is another element of the problem that needs to be addressed.

There are some people that are working with development (webpage development, Ubuntu One, Development, the server and support).  I believe all that should be somehow worked in as such as to resolve the issues.  The web managers won't be able to interface the SSO into the web without some cooperation from whoever is maintaining and giving support for this.

I might not be able to express the exact words/terminology for fixing the problem.  The gist of what I'm trying to express is the urgency of it.

A number of the messages has suggested that this is of low priority.  Whether it's low priority or should be considered high priority is a matter of opinion and my change from person to person.  Of course I don't have the power to set the priority, but I'm hoping to place insight with people who do have the power or influnce to have this serious matter addressed.

> 
@everyone, a ticket has been raised for Canonical IS, the sysadmin team who deal with all servers in the Canonical/Ubuntu ecosystem, to deal with this. As Elfy said, you are welcome to talk amongst yourselves, but it won't make it happen any faster, since the sysadmin team have their own set of priorities and a very large number of support tickets to work through, not just ours.

Again, when I referred to developers, I meant (Canonical IS, sysadmin team, and anyone else that might be able to come into play in fixing the issue.  I also meant to include the developers of vBulletin.  I had read somewhere (I can look up the information and post a like to if you you think I'm making it up) that the people responsible for getting the forum back up had contacted vBulliten for some type of assistance/support.

I appreciate that you're also mentioning in your message above that it's alright for us to have a discussion on this while it's being worked on.

It was my intentions to point out elements of importance which I hadn't saw referenced yet.  There might be other elements of importance that even I might fail to mention.  Then again, some people (such as you) might see this as a very low priority, and stress that the workarounds are sufficient.  Some people might feel that we don't need to make it easy for people who fail to understand how to activate these workarounds.

For some, easily picking up where you left off doesn't matter.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by houstonbofh on 2013-08-23
So...  When will we be able to stay logged in?

I am really tired of having to click 4 pages to log in when I stepped away from a post to eat dinner and than tried to reply, found I was logged out, lost my reply and than decided not to bother.  I also check the forums a lot less often because it is more of a pain than it needs to be.

---

### Post by Elfy on 2013-08-24
Bumped the ticket again this morning.

---

### Post by coffeecat on 2013-08-24
> **houstonbofh said:**
> So...  When will we be able to stay logged in?

I am really tired of having to click 4 pages to log in when I stepped away from a post to eat dinner and than tried to reply, found I was logged out, lost my reply and than decided not to bother.  I also check the forums a lot less often because it is more of a pain than it needs to be.

I've moved your post to a more appropriate thread. Please read the foregoing.

---

### Post by varunendra on 2013-08-24
> **Elfy said:**
> Bumped the ticket again this morning.

Thanks for the efforts and the updates Elfy. :)

I appreciate it more than things I got after 'resurrection' of the forums.

I wish they had bestowed more trust and power on forum admins than they currently have. I wonder if such issues make anyone besides me think about advantages of decentralization of powers. :|

---

### Post by apollothethird on 2013-08-24
> **houstonbofh said:**
> So...  When will we be able to stay logged in?

I am really tired of having to click 4 pages to log in when I stepped away from a post to eat dinner and than tried to reply, found I was logged out, lost my reply and than decided not to bother.  I also check the forums a lot less often because it is more of a pain than it needs to be.

Just think of the novice, mothers and grandmothers who can't figure out the 4 pages to click.

> **Elfy said:**
> Bumped the ticket again this morning.

Thanks, Elfy, for keeping this important issue on top.

I had forget to do my tedious clicks and found that I had read all the new message, but they were still marked unread until I tried to post.  That's because, at times, the browsing is seamless and you don't realize your two hours has expired and you're nolonger logged in.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by apollothethird on 2013-08-25
> **Elfy said:**
> [COLOR=#0000ff]**Bumped the ticket again this morning.**[/COLOR]

With this morning bumping of the ticket this morning, I would like to add, that while it's extremely frustrating getting the clicks right to pick up where I left off, I'm still more concern for the issues that novice are having trying to do this than my own problems.  I hope this gets fixed for them.

I'm sure the management who logs in should see the problem and notice a serious lost that ubuntuforums.org is suffering.  If you visited other places that are plagued with this affliction, you'd probably visit those places less because of the annoyance in having to log in so frequently.

Also, it wouldn't bother me if the forum weren't so important in using Linux.

Of course if the popularity dropped far enough, it might be replaced with a forum that is easier to use.

If someone things the remember me function isn't important, take a look at:

Hundreds of request for "Remember-Me" Support over the years:
[https://www.google.com/#fp=724e09b709030885&psj=1&q=site:ubuntuforums.org+%22remember-me%22&start=210](https://www.google.com/#fp=724e09b709030885&psj=1&q=site:ubuntuforums.org+%22remember-me%22&start=210)

 There you will find hundreds of request for "Remember-Me" support over the years.  That was when it was easy, just one click and you were in with any browser.  Now you have to go through 4 or 5 pages, and you still might not get it right to find where you left off at.

I'd love to hear from some of the forum's administrators who are working on this.  I'm sure I could help to resolve this serious problem.  I'm surprised if they can't see it as a serious problem.  If they don't, I'd still love to hear their rational.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by apollothethird on 2013-08-25
> **ajgreeny said:**
> Like a lot of users, I do **not** keep my browser permanently open and have no intention of doing so; when I have finished browsing I close it down, but leave my xubuntu session running.  At the next start of my browser (note; just the browser, not a new xubuntu session or reboot) I have to jump through the same SSO login hoops again, which as I said previously was not required with the "remember me" option available previously.

I don't know how many different threads there are on this subject, but it might interest you to look also at this thread:


New forum login - no remember me?:
[http://ubuntuforums.org/showthread.php?t=2165623](http://ubuntuforums.org/showthread.php?t=2165623)

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Elfy on 2013-08-25
It is quite simple.

We, the Forum Council are not the ones dealing with these issues - Canonical IS are. 

Repeating the same things over and over will get you nowhere as we can't do anything about it.

It is probably the truth to say that you have no idea how annoying either the Remember Me option missing is, nor the need for SSO from where I am sitting - you don't have to use that AND a vBulletin password to access the vBulletin control panels - you might have some idea how often WE are having to do so currently.

---

### Post by apollothethird on 2013-08-25
> **Elfy said:**
> It is quite simple.

We, the Forum Council are not the ones dealing with these issues - Canonical IS are. 

Repeating the same things over and over will get you nowhere as we can't do anything about it.

It is probably the truth to say that you have no idea how annoying either the Remember Me option missing is, nor the need for SSO from where I am sitting - you don't have to use that AND a vBulletin password to access the vBulletin control panels - you might have some idea how often WE are having to do so currently.

Elfy.  Thanks for noticing my plea and giving some type of feedback.

I don't know who is dealing with the issue, but on most of my post, I get a message stating who is not dealing with it, such as this one that is saying the "Forum Council" are not the ones.

Without feedback and suggesting, it would be less likely that whoever (if anyone) can deal with it will actually get the important message about the problem.  The forum has been back online for three weeks.  If someone interested communicated with the right party about the problem, I'm sure it could be resolve within minutes, at least within a couple days.

Someone else posted a message (that might have been you) telling me the developers don't work with these issues.  However, I don't think our developers would deny a request from someone who actually manages the board to help to resolve the issue.  After all, in my opinion, we do have the highest level of developers on earth associated with Ubuntu.

If no one else had gotten a notion to invite them to help fix the forum, there's a chance some of this discussion might make it to them, and the people (if any) who are actually dealing with the problem.

By the way, I'm glad to see that people are starting to realize the problem is on the end of the forum and not the user's browser or browser settings such as which were suggested in previous messages.  Those messages could confuse users who are already having problems.  They really shouldn't tamper too far with the security of their normal browser settings to try to resolve this issue which might make them become vulnerable to other threats while just generally browsing the Internet.

Also, in all the messages I've read so far, I don't see any evidence that the problem is even being addressed at all.  I keep being told that it's being dealt with by someone else.

Ultimately it's the someone else who my message is probably intended.  If you have some ability, hopefully you'd use this thread in your report to the people who can deal with the issue.

If someone told me they were having a problem with the forum, I'd take their suggestion and help them to organize the description of the problem and pass it along to the proper channels.  I wouldn't just tell them they are stuck because I'm not the one who push the button or type in the code.  I'd try to be part of the solution, even though I have not official "Testing, Development, or Support" affiliation.  I'd just do it as a concerned affiliated member.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by cariboo on 2013-08-25
@apollothethird, you seem to br repeating your self, we the Forum Council cannot do anything about the problem, except to prod Canonical IS. They are normally to busy to read the forum, so your hope that they see your posts aren't doing any good either. All we can do is wait until the problem is solved, and the General Membership will know shortly after we do.

As Elfy said, we the Admins are far more annoyed at the lack of Remember Me, than any of the Forum membership can possibly be. We have to log into the Forum, then if we need to do some administration work, we have to log in using SSO a second time, then enter a password, the time out makes this really old, really quickly.

---

### Post by cariboo on 2013-08-25
Merged two similar threads.

---

### Post by apollothethird on 2013-08-25
> **cariboo907 said:**
> @apollothethird, you seem to br repeating your self, we the Forum Council cannot do anything about the problem, except to prod Canonical IS. They are normally to busy to read the forum, so your hope that they see your posts aren't doing any good either. All we can do is wait until the problem is solved, and the General Membership will know shortly after we do.

As Elfy said, we the Admins are far more annoyed at the lack of Remember Me, than any of the Forum membership can possibly be. We have to log into the Forum, then if we need to do some administration work, we have to log in using SSO a second time, then enter a password, the time out makes this really old, really quickly.

Hi, Cariboo.  I didn't know before this message that you had done anything.  From this message you made a reference to "prod Canonical IS".  I don't fully know what that means, but I believe it means that something initiative is happening.

I have tried not to repeat myself and to add things that I might have missed or know known during the time of a previous message.

I'll wait a week or so and hopefully the membership and council might not mind if I bump (after a week) to ask for any development.

In my next message I may try to find out how to contact the Canonical IS (which all respect, whatever that is), since as you say, they don't frequent the forum.

I'm sure that might explain why it has being broken in this regard for a month since, the ones who deal with it are directly affected, if they are not using the system.

Thanks you kindly for this update!

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by apollothethird on 2013-10-27
I don't know how long the “remember me” feature has been fixed, but it appears to be working in my environment.  I hope someone will comment and confirm that it's working.

I'm very pleased if it's working.  I always knew, the maintainers of the best OS resource could provide this feature.  I hope it's really fixed and working and not just a flute in my environment that might fail.

Thanks in advance for any comments.  If it's still failing for anyone I'd be glad to compare my environment with yours to try to help you have the resolution.

 It's a relief to be able to pick up where I leave off with a single click from my email notice just like other sites.

Maintainers and support staff I salute you!

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by CharlesA on 2013-10-27
Yep, someone from IS got it working a while ago. :)

---

### Post by Sector11 on 2013-10-27
So where is this "Remember me?"

I'm still jumping hoops here

1. I get an email that apollothethird posted his post:
```
Dear Sector11,

This is a notification email. PLEASE DO NOT REPLY TO IT. 

apollothethird has just replied to a thread you have subscribed to entitled - New forum login - no remember me? - in the Forum Feedback & Help forum of Ubuntu Forums.

This thread is located at:
http://ubuntuforums.org/showthread.php?t=2165623&goto=newpost

Here is the message that has just been posted:
***************
I don't know how long the “remember me” feature has been fixed, but it appears to be working in my environment.  I hope someone will comment and confirm that it's working.

I'm very pleased if it's working.  I always knew, the maintainers of the best OS resource could provide this feature.  I hope it's really fixed and working and not just a flute in my environment that might fail.

Thanks in advance for any comments.  If it's still failing for anyone I'd be glad to compare my environment with yours to try to help you have the resolution.

 It's a relief to be able to pick up where I leave off with a single click from my email notice just like other sites.

Maintainers and support staff I salute you!

-- L. James

-- 
L. D. James
ljames@apollo3.com
www.apollo3.com/~ljames (http://www.apollo3.com/~ljames)
***************


There may also be other replies, but you will not receive any more notifications until you visit the forum again.

All the best,
Ubuntu Forums

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Unsubscription information:

To unsubscribe from this thread, please visit this page:
http://ubuntuforums.org/subscription.php?do=removesubscription&type=thread&subscriptionid=2107672&auth=767bf4572499f079f350c25f580f76e1

To unsubscribe from ALL threads, please visit this page:
http://ubuntuforums.org/subscription.php?do=viewsubscription&folderid=all
```

2. - I click on the link and I'm taken to the thread ... but never the post!

3. - In the upper right I click on the Ubuntu One SSO button and log in ... it always takes me back to the  [Index page]("http://ubuntuforums.org/index.php")

4. - Now I go back to my email, click on the link and I'm taken to the post as I am logged in with 3 Ubuntu pages open in Iceweasel.

I feel like a seal jumping hoops for someone's entertainment. ](*,)

It's time consuming and annoying to say the least.
But I still keep doing it!

---

### Post by hloeung on 2013-10-28
apollothethird, [http://ubuntuforums.org/showthread.php?t=2178096&p=12825161&viewfull=1#post12825161](http://ubuntuforums.org/showthread.php?t=2178096&p=12825161&viewfull=1#post12825161) ;-)

---

### Post by hloeung on 2013-10-28
Sector11, seems to be hard coded to the home/index page in the vBulletin OpenID plugin. I've added some extra logging and will hopefully spend a bit more time looking into fixing this sometime this week.

---

### Post by apollothethird on 2013-10-28
> **Sector11 said:**
> So where is this "Remember me?"

As far as I can see there isn't a "remember me" button.  It's a "remember me" feature.  On all the computers I tested (after your message I fired up a Windows 7 computer) the feature words.  Once logged in you stay logged in until you click on the log out button.

> 
I'm still jumping hoops here

1. I get an email that apollothethird posted his post:
...

2. - I click on the link and I'm taken to the thread ... but never the post!

3. - In the upper right I click on the Ubuntu One SSO button and log in ... it always takes me back to the  [Index page]("http://ubuntuforums.org/index.php")

4. - Now I go back to my email, click on the link and I'm taken to the post as I am logged in with 3 Ubuntu pages open in Iceweasel.

I feel like a seal jumping hoops for someone's entertainment. ](*,)

It's time consuming and annoying to say the least.
But I still keep doing it!

Did you click on the "Log Out" link between sessions?  I'm trying to duplicate the problem you describe.

I can't see that it would matter, but can you also tell us which browser you're using.  I've tried it with Opera, Firefox, Chrome, and Microsoft IE and it works the same with all of them for me.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by sandyd on 2013-10-28
Note that it apparently only works if you keep the same IP Address throughout the session

---

### Post by Sector11 on 2013-10-28
**@ apollothethird**

Well I'll be .... I'm in ... I never "log out" but I don't keep Iceweasel (Debian SID) open either.  Today it worked, I am logged in.  Good news....

Tossin' some catnip sandyd's way too ... some of good stuff!international for that 'international' smile!

**@ hloeung** *Thank you for your work on this.  Seems to be a go for me now too.*

---

### Post by apollothethird on 2013-10-28
> **sandyd said:**
> Note that it apparently only works if you keep the same IP Address throughout the session


Thanks, Sandyd.  I tested by using my tethered phone as my network connectivity and see that this is indeed a glitch.

I won't harp on this flaw at this time.  However, I hope the developers will work on fixing it.  People who don't have dynamic IP address shouldn't be locked out of this feature.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by apollothethird on 2013-10-28
> **Sector11 said:**
> **@ apollothethird**

Well I'll be .... I'm in ... I never "log out" but I don't keep Iceweasel (Debian SID) open either.  Today it worked, I am logged in.  Good news....

Tossin' some catnip sandyd's way too ... some of good stuff!international for that 'international' smile!

**@ hloeung** *Thank you for your work on this.  Seems to be a go for me now too.*

I'm glad to see the feature works for you.

Have a good one!

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by JKyleOKC on 2013-10-28
> **hloeung said:**
> Sector11, seems to be hard coded to the home/index page in the vBulletin OpenID plugin. I've added some extra logging and will hopefully spend a bit more time looking into fixing this sometime this week.There still seems to be something intermittent about it. I have bookmarks to the forums on two different machines on my little LAN; one of them seems to be working properly, the other seems to lose the login cookie(s?) from time to time but I've not yet found any pattern to it. Both machines are configured the same with regard to cookie maintenance, so far as I can tell. The LAN goes through a single router to reach the internet, and that router has a static IP address so all of my logins should appear to be from the same address, at your end of the line.

One difference is that I routinely log out of the one that keeps its cookies (though it runs 24/7), while the one that sometimes drops them is up and logged in 24/7.

I'm not complaining; even with the intermittent fallback to the many-clicks situation, it's far better than it was a couple of weeks ago. However I feel that keeping you advised of any strangeness that I experience is the only way that you have any chance of getting rid of it...

---

### Post by Cavsfan on 2013-10-28
I believe it is like a 24 hour timing thing. I have never had to login with SSO more than once per day on any of my installs. And I do not mind that at all. ;)
BTW I have a static IP address.

---

### Post by Sector11 on 2013-10-28
Just so people know ... prior to yesterday it had been some time since I logged in ... it was a pain after the 'unfortunate incident' of the forum going down.

As of today, everything is working as it was before the downtime.

**KUDOS!** *to the people who have worked on this and continue to debug the system.*

My system: is Debian SID with Iceweasel 24.0

---

### Post by varunendra on 2013-10-28
Can it be kept across IP changes as well like Launchpad?

There are certain times of day/night when I have to re-login every minute or two because my GPRS gets disconnected and the IP is changed after reconnecting.
Very frustrating but of course not enough to keep me away from forums. :P

---

### Post by hloeung on 2013-10-30
> **varunendra said:**
> Can it be kept across IP changes as well like Launchpad?

There are certain times of day/night when I have to re-login every minute or two because my GPRS gets disconnected and the IP is changed after reconnecting.
Very frustrating but of course not enough to keep me away from forums. :P

Last I checked, it was configured to keep across a /24 network. Our awesome Forum Admins have access to increase this to something larger (or even disable, which isn't something I recommend :-)).

---

### Post by apollothethird on 2013-10-31
> **hloeung said:**
> Last I checked, it was configured to keep across a /24 network. Our awesome Forum Admins have access to increase this to something larger (or even disable, [COLOR=#008000]**which isn't something I recommend**[/COLOR] :-)).

Maybe I'm missing something.  I would like to know what.  I'm looking at a scenario of a different IP network and can't see the problem.  Ok yea, the computer was stolen and the owner is saying, oh no, someone i going to read the forum messages in my name.

Out of all the things that might be doing with the comprised computer, it might actually be a benefit if the culprit typed a forum message from the computer.  It might actually help to track the computer's location.

I didn't complain before because I thought it was something technical and the maintainers was trying to figure out how to fix it.  I didn't know it was an intentional glitch/feature.

I hope this become a provision for us at Ubuntu Forums that we can soon appreciate just as we do from all the other forums we visit.

A person really concerned will already have their computer set with a password to get into his user account.

Please **[COLOR=#008000]recommend a computer specific remember me[/COLOR]**, not IP specific.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by Elfy on 2013-10-31
> **hloeung said:**
> Last I checked, it was configured to keep across a /24 network. Our awesome Forum Admins have access to increase this to something larger (or even disable, which isn't something I recommend :-)).

Just so that it is completely obvious.

_The only thing that we have access to does not JUST increase the 'timeout' but also affects other things._

In addition to which - it being set to 30 minutes BEFORE SSO was never ever an issue with anyone. It's set at 2 hours now, which is sufficient given that the remember me works for 24 hours, in fact I'm not sure that changing it back to 30 minutes will make any difference.

The fix needs to be in the mechanics of SSO not in fiddling with a timeout in vBulletin. 

What I'm failing to understand here is that AskUbuntu and Launchpad uses SSO/OpenID - I'm logged in/remembered there even after 2 months - why can we not just have exactly the same thing as they have.

---

### Post by varunendra on 2013-10-31
> **Elfy said:**
> What I'm failing to understand here is that AskUbuntu and Launchpad uses SSO/OpenID - I'm logged in/remembered there even after 2 months - why can we not just have exactly the same thing as they have.

This ^ exactly.

Just logged in to reply a post, and got disconnected. Reconnected, and of course had to ..
refresh (to get "login with sso") > ----wait----> sso > login > -----wait/redirect -------> back > back > back > refresh.

It hurts ! A lot when you're on a 4-5 KB/s gprs !!

[I](and while I'm typing this, nload is again showing 0/0 ul/dl... :()
(yup, again.. ](*,)](*,) )[/I]

---

### Post by sandyd on 2013-10-31
> **hloeung said:**
> Last I checked, it was configured to keep across a /24 network. Our awesome Forum Admins have access to increase this to something larger (or even disable, which isn't something I recommend :-)).

That explains it, it was beyond a /24, it was a different /8 ip block

---

### Post by hloeung on 2013-11-19
> **hloeung said:**
> Last I checked, it was configured to keep across a /24 network. Our awesome Forum Admins have access to increase this to something larger (or even disable, which isn't something I recommend :-)).

> **Elfy said:**
> Just so that it is completely obvious.

_The only thing that we have access to does not JUST increase the 'timeout' but also affects other things._

I was actually talking about vBulletin's "Session IP Octet Length Check" option meant for making it harder to hi-jack existing sessions. So that's:

AdminCP -> Settings -> Options -> Server Settings and Optimizations

It's currently set to 255.255.255.0.

> **Elfy said:**
> 
In addition to which - it being set to 30 minutes BEFORE SSO was never ever an issue with anyone. It's set at 2 hours now, which is sufficient given that the remember me works for 24 hours, in fact I'm not sure that changing it back to 30 minutes will make any difference.

The fix needs to be in the mechanics of SSO not in fiddling with a timeout in vBulletin. 

What I'm failing to understand here is that AskUbuntu and Launchpad uses SSO/OpenID - I'm logged in/remembered there even after 2 months - why can we not just have exactly the same thing as they have.

Nope, it's needed in vBulletin because vBulletin implements code to clean out sessions older than a certain period of time. AskUbuntu and Launchpad doesn't do this.

If you, and the rest of the forum administrators, feel that 24 hours isn't long enough for the "Remember Me" feature please file a ticket to have it increased.

---

### Post by apollothethird on 2013-11-28
> **hloeung said:**
> I was actually talking about vBulletin's "Session IP Octet Length Check" option meant for making it harder to hi-jack existing sessions. So that's:

AdminCP -> Settings -> Options -> Server Settings and Optimizations

It's currently set to 255.255.255.0.



Nope, it's needed in vBulletin because vBulletin implements code to clean out sessions older than a certain period of time. AskUbuntu and Launchpad doesn't do this.

If you, and the rest of the forum administrators, feel that 24 hours isn't long enough for the "Remember Me" feature please file a ticket to have it increased.

The remember me works sometimes and sometimes it doesn't.  This is really frustrating.  I don't understand why we should have to beg for this feature which exist with every other forum I visit.  I can't see what it has to do with security.

This is what baffles me.  The administrators apparently blocking the remember me for "security" while the SSO survives IP changes and months without logging in.  What is the security component when a person clicks "Login with SSO" and is in.  Except for the distraction and aggravation of the extra steps to get in, can still log into the forum by the computer user's name.  In fact, it's easier now than before.  If I click "Log out" because I possibly don't want anyone to use the forum in my name.  The next person at the computer just click on "Login with SSO" and they are in anyway.

Again, I'm very baffled that the administrators are trying to block use of the forum for security, but the Login with SSO is giving the person access to much more sensitive data, please a host of other forums.

I hope someone doesn't read this "flaw" and break Ubuntu One.  I hope they just provide that we can have the same "remember me" functionality with the Forum that we have with Ubuntu One.

I don't believe I'm missing anything.  But if I am, will someone please enlighten me.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by cariboo on 2013-11-28
Remember me works well for me  on all 4 system I use. As far as your problem with Ubuntu One login goes, it's basically your own fault, because you told your browser to remember the password.

Clear your browsers cache, and when asked if you want to save your Ubuntu One password, say no. I'm not sure how this will work with the Forums remember me feature, so you'll just have to try it.

---

### Post by apollothethird on 2013-11-28
> **cariboo907 said:**
> Remember me works well for me  on all 4 system I use. As far as your problem with Ubuntu One login goes, it's basically your own fault, because you told your browser to remember the password.

Clear your browsers cache, and when asked if you want to save your Ubuntu One password, say no. I'm not sure how this will work with the Forums remember me feature, so you'll just have to try it.

Hi, Cariboo.  You're miss understanding my point.  I tried to make it clear that I like the way Ubuntu One works.  This is the way it should.  There should be an option to remember so that the user doesn't have to go through loops to get in to the services.

If I were going to be concerned about a remember me, it would be Ubuntu One, not reading and posting messages on the forums.

The forums works the same way for me that it works for you until I and logged on VIA a different network.  There are occasions where I tether my computer to my phone's hotspot.  When I use that, I have to go thought the loop to access the forums.  I don't have to do that with Ubunto One.  I'm hopping we can get this same convenience moved over to the forums.

After I have changed my IP back to the original one, I have to go through the loop again.

It works the same way on all 10 of my computers as well as my tablets.

If you're saying you have tested this and can verify that you retain the "remember me" if you log in from a different network, then I would like to figure out how it's working for you, but not from the others who happen to use multiple networks.

I'm glad to explain if you still don't see the point.  And again, the only way you can tell is by logging in from a different network.  If you only log in on one network you would experience the problem.  I don't think anyone would experience the problem as long as their IP doesn't change.

SSO where my real valuable information and resources survives an IP change.  The communicating ubuntuforums.org doesn't survive an IP change.  I don't want them to take away the persistence from Ubuntu One... I'm hoping they will add this convenience to the forums as with all the other forums I frequent.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by varunendra on 2013-11-28
> **apollothethird said:**
> I tried to make it clear that I like the way Ubuntu One works....
....
.. I'm hoping they will add this convenience to the forums as with all the other forums I frequent.

..in short, there is no explicitly provided "Remember Me" feature on the forum (while it is quite desirable), and whatever alternative is there, doesn't survive IP changes while it does on all other related sites/services.


Frustrating indeed, but we should remember that **there is nothing that the 'Forum Administrators' can do about it except raising tickets and waiting for it to be addressed**. That seems to have been already done (probably many times now), and the outcome seems to be just a ridiculously increased timeout which is a _no solution_ for people like apollothethird and me who suffer frequent IP changes.

In fact we suspect increasing timeout is helping nothing and no one at all as pointed out by elfy earlier -
> **Elfy said:**
> ....In addition to which - it being set to 30 minutes BEFORE SSO was never ever an issue with anyone. It's set at 2 hours now, which is sufficient given that the remember me works for 24 hours, in fact I'm not sure that changing it back to 30 minutes will make any difference.

The fix needs to be in the mechanics of SSO not in fiddling with a timeout in vBulletin....

We are thankful to **hloeung** for communicating with us on behalf of the canonical IS team (please correct me if I misunderstood). Unfortunately, the major issues are still there (unnecessary extra steps to login, incorrect redirection adding 4-5 extra unnecessary steps to it, and login persistence being totally out of user's control).

I hope against hope that our concerns are not only being listened to, but are also being taken into consideration by the IS team.

---

### Post by Cavsfan on 2013-11-29
How I handle this login as well as any login I want to make easy is this: on Firefox I have an add-on called Biscuit which has an option to "opt in" for a site's cookies and preserve them. The other cookies are all deleted upon browser shutdown.
On Chromium, there is an add-on called Vanilla cookie manager that allows you to white list a site's cookies and all other cookies are also deleted upon browser shutdown.

So after I have the cookies in Firefox I just click on Preferences > Privacy > remove individual cookies, expand login.ubuntu.com and ubuntuforums.com and put a checkmark on each cookie and they are kept.
On Chromium, while I am on each site that I want to save the cookies I click on the icon in the address bar and select that site to white list.

Once every 24 hours I go through the SSO login with the 3 or 4 clicks and other times it stays logged in. I don't have to remember passwords although I have them on a text file for when I need them.

This is very reasonable to me doing it this way. I also have a static IP address. One cannot expect that if their IP address changes that they will not have to go through this process more often.
But, with the cookie saving methods I mentioned it is not as bad as it could be. ;)

---

### Post by apollothethird on 2013-11-29
> **Cavsfan said:**
> How I handle this login as well as any login I want to make easy is this: on Firefox I have an add-on called Biscuit which has an option to "opt in" for a site's cookies and preserve them. The other cookies are all deleted upon browser shutdown.
On Chromium, there is an add-on called Vanilla cookie manager that allows you to white list a site's cookies and all other cookies are also deleted upon browser shutdown.

So after I have the cookies in Firefox I just click on Preferences > Privacy > remove individual cookies, expand login.ubuntu.com and ubuntuforums.com and put a checkmark on each cookie and they are kept.
On Chromium, while I am on each site that I want to save the cookies I click on the icon in the address bar and select that site to white list.

Once every 24 hours I go through the SSO login with the 3 or 4 clicks and other times it stays logged in. I don't have to remember passwords although I have them on a text file for when I need them.

  This is very reasonable to me doing it this way. I also have a static IP address.  [COLOR=#008000]**One cannot expect that if their IP address changes that they will not have to go through this process more often.**[/COLOR]
But, with the cookie saving methods I mentioned it is not as bad as it could be. ;)

Actually I disagree.  This is so common, it's a fact with **every single forum** I frequent except for this one.  It's even common with Ubuntu One itself.  I don't understand why we can't have this convenience with this forum.

Many people including you have workarounds.  We shouldn't have to use workarounds.  We should have the convenience with is the norm.

What you and a few others many not understand is that there was no element of "Remember Me" on this forum (after it came back up) until people like me described the inconvenience.  Our request and suggestions are not falling on deaf ears.  If no one explains the problem then we'll keep get reoccurring questions for workarounds that shouldn't have to be required.

As far as your workaround, it isn't needed.  You can have the same thing you described by the new provision, in that the "remember me" works as long as you use the same (in your case static) IP.  The time you spend describing it can confuse some of the users into thinking that could use it to have the "remember me" functionality.  You have it because of your static IP, not because of your workaround.

The full remember me hasn't been restored yet because the problem isn't clear enough to the ones who has the power to fix it.  I'm trying to participate in helping to explain the problem, and to comment when it has been resolved.  I don't think the administrators are delibately giving us these loops.  They are not experiencing them because they, like you, either have static IP's or IP's that doesn't change regularly.

They don't realize that there are people who's IP changes on almost every bootup.  I don't know if AOL's internet access still do it, but their IP address used to change even while online continuously.

Static IP service cost more than dynamic IP services.  On other forum that I know of require a user to have a static IP for the "remember me" to work.  The fact that it's required with this forum is a design oversight that I'm sure will eventually be fixed just as they have worked on providing the "remember me" surviving a computer reboot.

Before that provision, your cookie workaround would never be working at this time.  If our users had been complacent and not explained the problem, you'd most likely still be suffering the loop every time you turn on your computer.

Not going through the loop is important to you.  That is why you spent time working on your workaround.  If it weren't important you would never have invested that time.  Apparently while you were creating your workaround, the "remember me" started working around the same time, and now you think it's because of your workaround.  It's because part of the issue has been resolved.

Now I hope you can consider how the people that don't have static IP's feel when they don't have a workaround for the convenience that you are describing that works for you.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by Cavsfan on 2013-11-29
> **apollothethird said:**
> Actually I disagree.  This is so common, it's a fact with **every single forum** I frequent except for this one.  It's even common with Ubuntu One itself.  I don't understand why we can't have this convenience with this forum.

Many people including you have workarounds.  We shouldn't have to use workarounds.  We should have the convenience with is the norm.

What you and a few others many not understand is that there was no element of "Remember Me" on this forum (after it came back up) until people like me described the inconvenience.  Our request and suggestions are not falling on deaf ears.  If no one explains the problem then we'll keep get reoccurring questions for workarounds that shouldn't have to be required.

As far as your workaround, it isn't needed.  You can have the same thing you described by the new provision, in that the "remember me" works as long as you use the same (in your case static) IP.  The time you spend describing it can confuse some of the users into thinking that could use it to have the "remember me" functionality.  You have it because of your static IP, not because of your workaround.

The full remember me hasn't been restored yet because the problem isn't clear enough to the ones who has the power to fix it.  I'm trying to participate in helping to explain the problem, and to comment when it has been resolved.  I don't think the administrators are delibately giving us these loops.  They are not experiencing them because they, like you, either have static IP's or IP's that doesn't change regularly.

They don't realize that there are people who's IP changes on almost every bootup.  I don't know if AOL's internet access still do it, but their IP address used to change even while online continuously.

Static IP service cost more than dynamic IP services.  On other forum that I know of require a user to have a static IP for the "remember me" to work.  The fact that it's required with this forum is a design oversight that I'm sure will eventually be fixed just as they have worked on providing the "remember me" surviving a computer reboot.

Before that provision, your cookie workaround would never be working at this time.  If our users had been complacent and not explained the problem, you'd most likely still be suffering the loop every time you turn on your computer.

Not going through the loop is important to you.  That is why you spent time working on your workaround.  If it weren't important you would never have invested that time.  Apparently while you were creating your workaround, the "remember me" started working around the same time, and now you think it's because of your workaround.  It's because part of the issue has been resolved.

Now I hope you can consider how the people that don't have static IP's feel when they don't have a workaround for the convenience that you are describing that works for you.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

Actually I've had this "work around" setup like it is probably since I figured out what cookies were used for; which was a while ago. 
Plus this is not a "work around", it is just the way I have my entire 7 operating systems setup. 
I daily clear the cache, cookies, tmp files, trash, etc. before I reboot or logoff and I figured out a way to keep the cookies I want to keep and delete the rest of them.

I offered you a way to login to this forum with 3-4 clicks since you have a dynamic IP address. 
You can either use my method, come up with another method, or complain some more. 
But, like the admins have said over and over again complaining about it will get you no where.

We all had to go the long route every time we left the forum and came back until **hloeung** fixed it so it would last 24 hours.
I'm thankful for that myself. But, even before when we had to go through the several screens, it wasn't that much of a problem to me because of the way I handle my cookies.

Sure I could not go straight to a link but, in 3-4 easy clicks I was in and went to where it was I wanted to go in the first place.
I would hate to have a sheet of paper or whatever sitting there with my userid and password on it entering it at each screen and any place that needed a userid/password.

I have a few sites that I have set the cookies up for like this; my bank is one of them.
Otherwise I would have to answer a bunch of questions like "what was the name of my grandmother's dog's maiden name" all the time.
I do not have the patience for that. :p

---

### Post by apollothethird on 2013-11-29
> **Cavsfan said:**
> Actually I've had this "work around" setup like it is probably since I figured out what cookies were used for; which was a while ago. 
Plus this is not a "work around", it is just the way I have my entire 7 operating systems setup. 
I daily clear the cache, cookies, tmp files, trash, etc. before I reboot or logoff and I figured out a way to keep the cookies I want to keep and delete the rest of them.

I offered you a way to login to this forum with 3-4 clicks since you have a dynamic IP address. 
You can either use my method, come up with another method, or complain some more. 
But, like the admins have said over and over again complaining about it will get you no where.

We all had to go the long route every time we left the forum and came back until **hloeung** fixed it so it would last 24 hours.
I'm thankful for that myself. But, even before when we had to go through the several screens, it wasn't that much of a problem to me because of the way I handle my cookies.

Sure I could not go straight to a link but, in 3-4 easy clicks I was in and went to where it was I wanted to go in the first place.
I would hate to have a sheet of paper or whatever sitting there with my userid and password on it entering it at each screen and any place that needed a userid/password.

I have a few sites that I have set the cookies up for like this; my bank is one of them.
Otherwise I would have to answer a bunch of questions like "what was the name of my grandmother's dog's maiden name" all the time.
I do not have the patience for that. :p

Hi, Cavsfan.  I appreciate your concern to help me.  My post are my concerns to help everyone.  As far as static IP's I have over 20 of them in my shop.  My computer is normally on a static IP.  We had a wind storm in my area where there were lines down.  I had to use my phone's tethering system to continue a lot of my work for a few hours until the lines were back up.  During that time all the forums I frequent except for this one worked with the IP change including Ubuntu One.  This forum was the only one where the remember me failed.

All the conveniences you provide me with in your workaround works for me without your workaround.  I'm not trying to be rude, just explaining a fact.  You have to use your workarounds because you delete your cookies.  I use the convenience of my cookies with this site as well as all the other sites I frequent... and again, it works without any workarounds.  If I wanted cookies removed, I could easily manage having them removed.  I understand them and use the convenience as they are by default.  It works perfectly.

What you don't appear to understand is that if you change your IP's your cookies will not provide you with the remember me convenience.  You'd have to perform the loop to get in.  If your workaround actually worked on this forum, I'd probably use it and promote it as a workaround until the problem is fixed.

Please be advised that a workaround, yours, and all the others are not needed.  The system has been updated in such a way to work like other forums except for the fact it does not survive IP changes.  That (the not surviving IP change) is another step that I have discovered and am reporting.  You can call it complaining, but I'm trying to help.  Most of the people who has influence might not know this.  It's clear that you think that your cookies resolution is something to pass on to help people with this "remember me" problem.  However, the people with the problem are not deleting their cookies as you are.  If they were deleting their cookies it would be because they are not trying to use the "remember me" feature.

The people with the problem are currently having the problem because the "remember me" doesn't survive the IP change.  It's not a problem that immediately affect me when working in my shop.  But if I used a Laptop and traveled, the feature would be broken for me just as it is with the people who has dynamic IP's.  This is not the norm.  The norm is the way you describe:

> **Cavsfan said:**
> 
I have a few sites that I have set the cookies up for like this; my bank is one of them.
 Otherwise I would have to answer a bunch of questions like "what was the name of my grandmother's dog's maiden name" all the time.
 I do not have the patience for that.


What you describe above is the norm which we all enjoy everywhere except on this forum.

You have the convenience of your cookie system working because they updated that part, which is a step closer to having it fixed.  The people who have static IP's or don't have their IP's change very often like me and like you can enjoy this convenience.  If you used a Laptop and traveled this site's remember me would become broken for you just as it is for many of our users who's ISP change their IP's frequently.

If you think your cookie system can survive and IP change, I'd install it and promote it.  But it wouldn't.  If you can understand the problem, you might be able to help to communicate it to the people who has the power to fix it.

Slowly more and more people are starting to understand the problem.  Slowly the forum is approaching the convenience that all other forums including Ubuntu One has.

If someone with understanding doesn't make it clear, the problem would never really be discussed or addressed.  You're able to enjoy the convenience of the cookie solution because enough people asked for and explained the "remember me" problem..  Now some have it and some don't.  Most of the responses to my message are people who don't appear to understand there is still a problem or what the solution is.  I understand both and am trying to participate as a concerned member for the good of the system, in the resolution.

I understand we have a great group of provider (of this forum) which are very hard at work.  They are doing a great job and great service.  If someone sees a component of the system which is broke, I'm sure they would appreciate feedback on the matter.

Your message suggested that I was complaining rather than make user of your solution.  It's clear from your message that you don't fully understand the problem.  So, again, I don't mean to sound like a complainer or an ungrateful person.  I'm very grateful to the providers of this forum as well as your effort to share what you think is a resolution.  But again, your resolution is to restore the cookies that you delete.  Most of us have no need to restore the cookies because we don't delete them in the first place, so there's nothing/no need to restore.  The cookies are already here, but won't provide the remember me feature after an IP change.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by cariboo on 2013-11-30
The way vBulletin and SSO implement **remember me** seems to be where the problem lies, and until this problem is resolved, the login problems will continue.

We will not revert to the former behaviour, as the thought of someone being able to steal all the passwords and email addresses again scares the heck out of me, and the rest of the Forum Council.

---

### Post by apollothethird on 2013-11-30
> **cariboo907 said:**
> The way vBulletin and SSO implement **remember me** seems to be where the problem lies, and until this problem is resolved, the login problems will continue.

We will not revert to the former behaviour, as the thought of someone being able to steal all the passwords and email addresses again scares the heck out of me, and the rest of the Forum Council.

I don't recall anyone suggesting to use the system in the formal manner.  If you think that is my suggestion, it's not.  The SSO isn't the problem.  The remember me works with the SSO.  The forum could also use the same functionality.

There were people that was suggesting that we were stuck with there was no element of remember me before users such as I pointed out the flawed inconvenience.  The developers continued and added a comment of remember me of which many (including me) are enjoying.  If no one pointed out this current flaw, it would never be considered.

Since it's unlikely that you are among the members affected by this current flaw, you can't imagine it as a problem.  Some users are having the problem and have pointed it out.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Elfy on 2013-12-01
I've bumped the support ticket with this IP renewing/wifi issue, which appears to be what you're saying.

---

### Post by cariboo on 2013-12-01
> **apollothethird said:**
> I don't recall anyone suggesting to use the system in the formal manner.  If you think that is my suggestion, it's not.  The SSO isn't the problem.  The remember me works with the SSO.  The forum could also use the same functionality.

There were people that was suggesting that we were stuck with there was no element of remember me before users such as I pointed out the flawed inconvenience.  The developers continued and added a comment of remember me of which many (including me) are enjoying.  If no one pointed out this current flaw, it would never be considered.

Since it's unlikely that you are among the members affected by this current flaw, you can't imagine it as a problem.  Some users are having the problem and have pointed it out.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

Sandyd as well as a few other members, mentioned the problem earlier in the thread, with remember me being forgotten when the IP address was changed. I'm not saying it isn't a problem, I just don't personally find it a problem.

---

### Post by apollothethird on 2013-12-01
> **cariboo907 said:**
> Sandyd as well as a few other members, mentioned the problem earlier in the thread, with remember me being forgotten when the IP address was changed. I'm not saying it isn't a problem, I just don't personally find it a problem.

That's because, your having a static IP, it doesn't affect you.  It affect the users who don't have a static IP.  There's a change your ISP provides you with a static IP at no extra charge.  Many ISP's change more for static IP's.  Some ISP will not provide static IP's even if the user request and is willing to pay more.  There just isn't enough static IP's for everyone it the world to have their own.  So in many cases they are dynamically assigned as needed.

Someone really needs to have concern for the users who don't have static IP's whether it's because they can't include it in their budget, or that it's just not available in their area.

Many people will brush the problem off and ignore it, just because they are complacent.  If everyone is complacent, the people who could fix this might never realize it's a problem.

And again, it having "remember me" functionality weren't a big deal to most people, you wouldn't be able to enjoy this benefit, because it might have been left out altogether.

Imagine how it was when you couldn't just click on an email notice and be at where you left off with your forum activity.  I know you are experienced enought to do the loop to figure out how to get to where you left off.  But that isn't so easy for some novice.  While reading the messages I just noticed that a user was "scolded" for posting new threads every time he had an updated message.  They user might have been posting new threads because he was having problems finding out where he left off.  For you and for me (who are experts) we have a single click from our email notices.  I'm trying to present the necessity for providing this convenience to the other users.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljkames](www.apollo3.com/~ljkames)

---

### Post by apollothethird on 2013-12-01
> **Elfy said:**
> I've bumped the support ticket with this IP renewing/wifi issue, which appears to be what you're saying.

Thanks, Elfy.  The last time someone said this about forwarding the issue we soon get the functionality that we currently are able to enjoy.  Pointing to this thread might help the people with the controls understand the issue and how to consistently duplicate it.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Elfy on 2013-12-02
> If you, and the rest of the forum administrators, feel that 24 hours isn't long enough for the "Remember Me" feature please file a ticket to have it increased.  Appears that we'll need to do this. No idea of time scale I'm afraid.

---

### Post by apollothethird on 2014-10-19
> **Elfy said:**
> Appears that we'll need to do this. No idea of time scale I'm afraid.

It's been almost a year since your message.  The "remember me" is still missing functionality.  I have to go through a hoop every time I log on.  This used to be one of my top sites.  It's very low on the list at this time, because of this lack of functionality.  This is the only site at all that I visit that doesn't have a functioning remember feature.

I use Ubuntu and strongly promote it.  But the support is lacking because of the skewed/lack of functioning remember me.  I'm sure many people are not getting their topics updated because they don't feel like going through the hoop of logging in to pick up from where they left off.  They are reading recent messages... threads not being marked because they are not logged in, and the community is loosing.

Seeing that Ubuntu is the cutting edge of OS' it's extremely baffling to me that the IT forum administrators can't get a industry standard remember me.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by ELD on 2014-10-19
Couldn't agree more. I practically never visit now due to going through like...what 4 screens to login every damned time?

It ruined the experience for me, and since this became an issue I saw much less people posting, so the forum is dying.

---

### Post by Elfy on 2014-10-19
> **apollothethird said:**
> It's been almost a year since your message.  The "remember me" is still missing functionality.  I have to go through a hoop every time I log on.  This used to be one of my top sites.  It's very low on the list at this time, because of this lack of functionality.  This is the only site at all that I visit that doesn't have a functioning remember feature.

I use Ubuntu and strongly promote it.  But the support is lacking because of the skewed/lack of functioning remember me.  I'm sure many people are not getting their topics updated because they don't feel like going through the hoop of logging in to pick up from where they left off.  They are reading recent messages... threads not being marked because they are not logged in, and the community is loosing.

Seeing that Ubuntu is the cutting edge of OS' it's extremely baffling to me that the IT forum administrators can't get a industry standard remember me.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

We asked, they'd do no more. 

We don't want SSO anymore than you but we can do no more. 

Take it up with IS yourself - see if you can get anywhere.

> **ELD said:**
> Couldn't agree more. I practically never visit now due to going through like...what 4 screens to login every damned time?

It ruined the experience for me, and since this became an issue I saw much less people posting, so the forum is dying.From a logged out state the most screens I see when logging in here is 3 - and that includes having to login to admincp seperately.

---

### Post by coffeecat on 2014-10-19
> **ELD said:**
> I practically never visit now due to going through like...what 4 screens to login every damned time?

I you want to be taken seriously, it's best not to exaggerate.

---

### Post by ELD on 2014-10-19
Well I get 4, as I have to keep authorising my details instead of just logging in, this time I tried it and I only got 3, but that must be because of how recently i authorised my email.

It's a pita having to keep doing it, hell I removed my bookmark and only come when i get a reply I'm subscribed to now. Every other forum/site I visit has this ability. It's a joke.

---

### Post by ELD on 2014-10-19
> **coffeecat said:**
> I you want to be taken seriously, it's best not to exaggerate.
I'm really not, and the other staff member above also confirmed they get 3 screens, I seem to get one more as my other post notes.
<snip>

---

### Post by Zill on 2014-10-19
After many years as a happy Ubuntu user, I too have moved on from Ubuntu.  The main trigger was the change to Unity but my second reason was the hassle of maintaining an active forum logon, making participation in the forums more of a pain than it should be!

---

### Post by Elfy on 2014-10-19
> **ELD said:**
> I'm really not, and the other staff member above also confirmed they get 3 screens, I seem to get one more as my other post notes.
<snip>

I get 3 - and I have to use to login to admincp - I know for fact you don't.

If I login with my test user - I see 1 screen.

What are these 4 screens? 

Screenshots perhaps will help us understand you.

---

### Post by ELD on 2014-10-19
Fine, here's 3 shots of what happens, 5 if you count having to click login in the first place from the main page, since you shouldn't even have to do that, you should just be able to come back logged in and go about your business.

So it's forum -> redirect -> authorise - > another redirect -> forum -> can finally do what i wanted to

Here's a link to 3 pics of the middle sections which I shouldn't have to do:
[http://imgur.com/z39DmxW,9OZKzDD,sY3jft1](http://imgur.com/z39DmxW,9OZKzDD,sY3jft1)

The fact that I am having to do this is also a joke. You guys know it's an issue and it's an extremely simple feature to have.

---

### Post by coffeecat on 2014-10-19
To log into Ubuntuforums from the home page, and so long as you are already logged into Ubuntu One (which doesn't time out): 2 mouse clicks.

[size=5]**Two Mouse Clicks.**[/size]

Why all the drama?

---

### Post by ELD on 2014-10-19
> **coffeecat said:**
> To log into Ubuntuforums from the home page, and so long as you are already logged into Ubuntu One (which doesn't time out): 2 mouse clicks.

[SIZE=5]**Two Mouse Clicks.**[/SIZE]

Why all the drama?

Some of us just want to get straight to it and reply to what we came here for? Or to quickly get help? Without the added hoops of multiple pages to sift through before we can actually do what a forum is for?

Also does it make you feel big using big bold letters? Either we touched a nerve or you really don't want to try to understand people?

---

### Post by Elfy on 2014-10-19
No - it's not that.

It's because we keep saying that we can't do more - but people don't listen.

I've said in post 114 to talk to IS - see if you can do it.

Edit - seriously - go talk to them - if you can manage to get them to do it - we'll be as happy as you.

---

### Post by ELD on 2014-10-19
If the forum admins can't get it changed why would they even listen to a user?

Anyway "gg" i'm out as it's obviously a dead end. Going to unsubscribe now, so don't reply to me :)

---

### Post by coffeecat on 2014-10-19
As Elfy has already explained - this is out of our control. After the security breach last year, SSO was forced on us. The admins like it less than the users - in fact we hate it.

---

### Post by Cavsfan on 2014-10-19
I've got 6 Linux systems on this box and each time I switch from one to another I have to go through the 3 click login. But, that is all it is for me.
I use an extension on FireFox called Biscuit that allows me to delete all cookies when I close FireFox but it is set up to "preserve" certain cookies.
So I don't have to continually enter userid and password; just click through the 3 screens.

Here is the FireFox addon: [https://addons.mozilla.org/en-US/firefox/addon/biscuit-220876/](https://addons.mozilla.org/en-US/firefox/addon/biscuit-220876/)
For Chromium I use Vanilla Cookie Manager to preserve the cookies I want to keep: [https://chrome.google.com/webstore/detail/vanilla-cookie-manager/gieohaicffldbmiilohhggbidhephnjj](https://chrome.google.com/webstore/detail/vanilla-cookie-manager/gieohaicffldbmiilohhggbidhephnjj)

After 24 hours or so, when I get into the forum if I see the logon with SSO button, I just click on it and go through the 3 screens. No big deal.

Then as I said If I go from Utopic to Mint Qiana I have to go through the process again; the 3 screens. No big deal.

You have to set it up but it's pretty simple as I see it. It's also a convenient way to preserve cookies for all the websites you regularly visit while at the same time deleting all the extra cookies that accumulate.

[ATTACH=CONFIG]257360[/ATTACH] Those cookies that are checked will not be deleted. 

[ATTACH=CONFIG]257361[/ATTACH] Here is how Biscuit is setup to delete cookies at shutdown and preserve the ones that have a check mark.

Best thing for Linux cookie management.

---

### Post by apollothethird on 2014-10-19
I haven't counted the screens, but for me 1 extra screen is too much.  I am a very experienced computer user, have been using computers more than many of the users I'm familiar with has been living.  Two or three screens to reach where I left off is too much and it's a very big deal.  I actually type over a hundred words per minute.  However, if I have to type extra words, it's a burden to me.

To me a lot of those hoops is what the computer is for.  If I perform a task more than a couple of times I might spend an hour writing and debugging a script to do it so that I won't have to spend quality time being distracted on performing the sequence.  Since I already have multiple terminals running, I just run the script and save two or three key strokes.

Novice Linux users don't have this luxury of experience.  The two or three pages that isn't a big deal to you gets many people lost.  They have to use Google to find where they typed their message because they can't fully understand the hoops.  The messages are usually not marked read because they are not logging in.  It's too much trouble.

I can't believe the administrators are trying to say browsing three pages to get to where you left off isn't a big deal.  It actually is.

As far as telling us to go to someone else besides the actually support contacts on the forum doesn't sound very feasible either.  I have no idea where to go other than posting the problem in the forum.  I understand that you're saying you can't fix it.  I appreciate that, at least, you're acknowledging that you don't like the hoops either, you just tolerate them.

It's not like we are posting beating the horse daily.  Asking for a review once or twice a year shouldn't be a bad thing.  If you have some type of access to the providers of the forum, I'd hope that you would appreciate the feedback threads and have something to present to the powers that be.

My post is for the good of the site.  I tried to get used to the 2 or 3 pages, but I can't get used to it.

The problem isn't the SSO login.  The SSO always allowed me to have access to my cloud files without going through hoops.  There were always one click access.  So it they wanted to use SSO, they could still give us remember me functionality.  I'm certain that the problem is that the people responsible isn't seeing this as a concern.  If someone can make it clear enough, I'm sure it'll become fixed.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by BlinkinCat on 2014-10-19
This being my favourite site, I consider any extra effort to logon is worthwhile!

Yes, it could be better, but for this laid-back user all is O.K.

---

### Post by lisati on 2014-10-20
@apollothethird: I, too, have been using computers of one form or another for a long time, quite likely longer than some of the current forum members have been alive. I'm thankful that we don't have to resort to punched cards, paper tape, or even toggling switches on the front of our main system unit! :D

---

### Post by Cavsfan on 2014-10-20
> **lisati said:**
> @apollothethird: I, too, have been using computers of one form or another for a long time, quite likely longer than some of the current forum members have been alive. I'm thankful that we don't have to resort to punched cards, paper tape, or even toggling switches on the front of our main system unit! :D

+1 ^
I believe there are quite a few of us who fit that category. I was in the Air Force going to school for computer electronics learning on some computers that had flashing lights that went so slow you could almost count them if you were good with binary. :D

---

### Post by apollothethird on 2014-10-21
> **Elfy said:**
> We asked, they'd do no more. 

We don't want SSO anymore than you but we can do no more. 

Take it up with IS yourself - see if you can get anywhere.

From a logged out state the most screens I see when logging in here is 3 - and that includes having to login to admincp seperately.

Elfy.  Please look at the link below.  If I logged in multiple times a day, it would just be one click.  I don't know how long it takes for the remember me to time out, but after a couple of days when I get a notification from a subscribed thread or click on a hit from a Google search, I can't get it below 4 clicks.  Then I have to remember exactly what to do to get there, otherwise it'll take even more time and navigating.

I'd appreciate if you would tell me what I might be doing wrong after you look at the video.  But then, even if you could teach me how to get it down to lower than 4 clicks, I see it as a problem that we should have to teach some special method of how to access a forum, with there is a standard that works with thousands of forums.  I believe we should have concern for a new user who is already overwhelmed by having a new OS environment to contend with.

Please look at: [https://www.youtube.com/watch?v=SPvlL5L85Vk](https://www.youtube.com/watch?v=SPvlL5L85Vk)

Please show it to the IT people (or give me their email address and I'll try to communicate with them directly to help to fix this critical issue).

> **coffeecat said:**
> I you want to be taken seriously, it's best not to exaggerate.

Hi, Coffeecat.  I don't think Eld was exaggerating.  Please look at the youtube link above.  I understand that the forum admins are saying you don't have any control.  But if you could be a little more sensitive to actually view for yourself the issues the users are experiencing and describing, it would become more likely to fall a little more open to the ears of the ones who have the power to fix the problem.

> **ELD said:**
> I'm really not, and the other staff member above also confirmed they get 3 screens, I seem to get one more as my other post notes.
<snip>

As you can see from the youtube video link above, it takes me more than the 4 that you mentioned.  I'll keep working and see if I can get it down to less.  But, I'm hoping the administrators can see by the link that you are not exaggerating.

> **Elfy said:**
> I get 3 - and I have to use to login to admincp - I know for fact you don't.

If I login with my test user - I see 1 screen.

What are these 4 screens? 

Screenshots perhaps will help us understand you.

As per your request.  The video link above.  Thanks in advance for your attention to this.

I can't imagine a novice being able to get to his thread in less than 4 or 5.  I'm sure that many give up when trying to find their threads to proceed with followups.

I don't read the forums as much as I used to, but I'd be surprised the sight isn't overwhelmed with novice posting new threads as followups because they can't easily find their original thread, of which an email notice works on other forums.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by bapoumba on 2014-10-21
> **apollothethird said:**
> I see it as a problem that we should have to teach some special method of how to access a forum, with there is a standard that works with thousands of forums.
This is where you have to consider our login method is not standard. Like it or not, it is not. The current login method was set up after a forums breach, to prevent it from happening again. Is it the best ? I do not know. This is the one canonical-sysadmins who run and administrate the servers came up with and are supporting. They do all the infrastructure work. If this is what they are comfortable with regarding security, I'm not going to discuss it. There are many points we would like to have access to, including application functionalities, we do not. If the price is too high for you, then I'm sorry you cannot afford it. We cannot make it cheaper.
> **apollothethird said:**
> 
I don't read the forums as much as I used to, but I'd be surprised the sight isn't overwhelmed with novice posting new threads as followups because they can't easily find their original thread, of which an email notice works on other forums.

Many sites have reinforced their access regarding security (random number based on timestamps, sms confirmation) that require another device to confirm your identity. If you prefer comfort over security, we do not have anything to offer. If the login method drives you away from the forums, then it drives you away from the forums. We are not a commercial site, we are happy to have you here because you enjoy the place and come to share experience and knowledge, ask for support or give support. If not, then they are many other resources you can use, including into the Ubuntu ecosystem.

---

### Post by varunendra on 2014-10-21
Wow, what a coincidence this thread was bumped again. Maybe not really surprising?

More than a week ago, I broke my 3G modem by smashing it on the floor because of the frustration caused by the need to log in a dozen times in less than an hour. My ISP was acting up (seems like a monthly routine for them) and I was getting disconnected every few minutes, requiring to log in again as the IP was changing every time. Mind you, I'm sitting at the heart of the capital of India and was using one of the most reputed mobile broadband services here. Yeah, this is how the bests here are, don't even want to talk about days I spend in smaller towns/my village.

My last 8-line [post]("http://ubuntuforums.org/showpost.php?p=13141014") here on the forums took me about an hour, a dozen+ re-logins and a partially broken modem to complete it. Obviously my mood and the contents of the post (thanks to the server glitches, forcing me to re-type it a couple of times) were completely changed by then, thankfully, just from descriptive to dry, not something bad. But in that mood, I could have posted something nasty enough somewhere to get a bitter reply or maybe even a warning from one of the mods/admins.

**Sudodus** PM'd me to correct a mistake in my post, but given my mood and the frequency of disconnects/IP change, I asked him back to post it himself knowing my connection and the modem may not survive long enough to complete the edit. Turned out to be a good call as the 2nd and final smash came only about 10 minutes later that turned my one nice-looking modem into four nice-looking pieces. A couple of hours with a soldering iron and some elfy (the adhesive, not the admin) next day brought it back though, and I am posting here from the same modem, a different ISP (just different, already tried and discarded more than once for the same reasons).


Now I don't want to bug the admins for something they don't have control over, but I couldn't decipher a clear answer from Elfy's previous post ([#93]("http://ubuntuforums.org/showpost.php?p=12834060")) about this (I think he talked about 'Timeout', not IP/network change issue), and hloeung's reply to it (post #96) further confused me. So just for sake of clarity, could you admins please explain what these posts from **hloeung** were referring to again? -
> **hloeung said:**
> Last I checked, it was configured to keep across a /24 network. Our awesome Forum Admins have access to increase this to something larger (**_or even disable_**, which isn't something I recommend :-)).

> **hloeung said:**
> I was actually talking about vBulletin's "Session IP Octet Length Check" option meant for making it harder to hi-jack existing sessions. So that's:

AdminCP -> Settings -> Options -> Server Settings and Optimizations

**It's currently set to [COLOR="#FF0000"]255.255.255.0[/COLOR]**.

Did it mean that the forum admins have access to a setting that can remove the IP change issue? Is it anywhere close to be true? If yes, what is the problem in implementing that change?

> **Elfy said:**
> Edit - seriously - go talk to them - if you can manage to get them to do it - we'll be as happy as you.
Can we get contact links here please? Thank you for whatever you can provide us. Any recommendation on what might be more effective, if at all, would also be very appreciated.


**@lisati, bapoumba, BlinkinCat, Cavsfan** and all those who are 'Thankful' for what we have got from the big-hearted canonical team,

First of all, I shouldn't need to proclaim here how much I respect all of you. Nor am I questioning or disputing what you say about 'thankfulness'. But for me, it is more than a question of comfort now. At least to me, one tiny insignificant creature of this huge ecosystem, it has become a question of 'how much they value or respect us'. We are not asking anything extraordinary, means we're not asking for 'special' attention. But seeing how ALL other sites related to Ubuntu SSO are unaffected by this 'bug', it seems as if UF is being deliberately ignored. Maybe some (or most) of the members like you don't mind, but with a '**Closed Ticket**' on the current unusual and clearly buggy way of logging in, combined with recent server performance issues, it seems to me as if UF is not just down, but in fact completely OUT of their list of priorities.

A general rule of leadership and management is - If you can't handle something, let it be handled by those who can. I would be thankful if Canonical just keeps sponsoring the server and let them be administered by our Forum Admins here, if it has become too much of a trouble for them.

Now I don't know what the Canonical leaders and the IS team are upto, but I do know that the number of forum users (hence the workload on the servers) has certainly NOT grown exponentially over the years, while hardware/software and infrastructure capabilities have. So from whatever little is in my knowledge, nothing else but an utter disregard and ignorance of this particular spot (the forums) explains all the lags and bugs we are seeing here.

I was about to post a question (in a new thread) about whether we are going to see some improvement in the login procedure and server performance anytime soon. But somehow already knowing the answer, decided to just cool it off. After 8-9 days now, apparently it is instead my enthusiasm about helping people here that is cooling off.

[INDENT][I]Am I offering my volunteer help in the right place?
Do we even exist for the company that we are directly or indirectly supporting here?[/I][/INDENT]

Unless we get a clear answer to why the login problem specific to UF can't be solved, the answer to above two questions seems to me a big, bold, bitter NO.

Since my last post here, something very strange has happened to me - I no longer feel the crave to hunt for questions and try to answer them. Very surprising to myself, I've not even answered the PM's requesting help, whereas I used to reply them immediately putting all my important tasks in the backseat earlier. Maybe it is because my mind is currently clouded with doubts due to ignorant behaviour and unclear answers from Canonical? Or could it be a natural "***Strike X***" type reaction?

Couldn't help looking back at what I considered "[**Strike 1**]("https://bugs.launchpad.net/bugs/1172422")" sometimes ago, and can't help quoting this part (from ***comment #50*** there) I posted then -
> I still love Ubuntu and am proud to be a part of the community. But I am also proud of what I have to offer to the community. I'm just confused at the moment if I'm offering it at the right place, for right people.
From *"right people"*, of course I mean canonical.

Now that I have logged in again anyway, think it's time to reply those PM's (with an apology for not responding in time) and thread posts.

Sorry for this long post, possibly off-topic in the later part, but _in case I failed to really "cool-off" this time, I hope this would explain my absence from here_ (or anything Ubuntu).

---

### Post by bapoumba on 2014-10-22
When I am traveling and on the phone I sometimes get the same symptoms, ie constant UF disconnections. Not always, not everywhere. So, to me, not related to my provider, rather to the local network setups (several companies may share the same hardware and the balance and priorities are not homogeneous, they depend on who actually owns the physical tubes).

---

### Post by varunendra on 2014-10-22
Disconnecting while travelling (1+1 hour daily, between office/apartment) is a daily routine for me, and I have trained myself to be mentally prepared for that. Usually it disconnects 2-3 times along the way at certain places, but sometimes I remain logged in even after a new connection is established. Perhaps due to the IP or network remaining the same.

It is usually this time (1 hour per side) in the bus that I get for posting on the forums for last few months. So the problem is affecting me regularly. Pages not refreshing in time after hitting the "submit" button (or ending up in double-posts if I wait too long) seems to have become the "norm" these days, but that is a different issue, shouldn't be discussed here.

What I can't train myself to digest is - I can't even remember which month I logged into launchpad, and I'm still logged in there. Perhaps too much of a convenience. But why is UF alone being treated so [s]differently[/s] badly?

--

---

### Post by wildmanne39 on 2014-10-22
I am traveling all the time now and everytime I change IP's I get disconnected but I click one button and it logs me in and redirects me back to ubuntu forums so while I understand the frustration I just do not see it as a big ordeal to sign back in especially if it is keeping the forum safer from hackers.

---

### Post by apollothethird on 2014-10-22
> **Wild Man said:**
> I am traveling all the time now and everytime I change IP's I get disconnected but I click one button and it logs me in and redirects me back to ubuntu forums so while I understand the frustration I just do not see it as a big ordeal to sign back in especially if it is keeping the forum safer from hackers.

How is it going, Wild Man.

Please understand that logging in isn't the issue.  I don't know how much experience you have with participating in forums and following up on threads from your notification message.  But it wouldn't be possible for you to catch up with this thread and and be logged in with only one click.  Even the administrators have admitted that takes them 3 clicks.

I wish I didn't have to be logged out.  I wish I could actually stay logged in to the forum just like was are able to stay logged into SSO.

I'm an IT speciallist with lots of experience in security and forums.  Some one use the words and say the forums are safer.  But that is just words.  I guess if someone say you'd live longer by not saying connected.  You could also say, I don't mine having to keep logging in as long as it allows me to live longer.

Again, those are just words.

Again, SSO isn't the problem.  The administrators/providers/IT (or the powers that be) could allow us to say logged on if they wanted to.  At first it was just one session.  Enough users "complained" until they were actually hear and was giving this consideration to extent it.  If the users hadn't expressed themselves we would be further back.  If enough people like you who can't see the problem was heard loud enough over the experience users who does see the problem, it'll make it less likely that the powers that be would actually be able to recognize there is a problem.

I could go into more details about all the work it takes to get to a specific thread, like what happens when you perform a Google search and get a Ubuntuforums hit.  You won't be automatically logged in if the system had logged you out (as it does me an many other users).  When you click on the option to reply, you'd be brought to the SSO site.  Then you click to allow SSO to log you in, you won't be at your desired thread, you'd be at the UF home screen.  Now you'll have to navigate to find the thread you wanted to reply to.  That takes me a lot of clicks and trying to remember the exact thread.  I can imagine that some novice might give up because some of the work would be over their head.

Can you tell me what I could possible do different to have less clicks and navigation to read an updated message to this thread when I get a notification?

Please look at the work it takes me.  I'd b e happy and a very strong supporter of whatever you present to me that could get this down to one click.

[https://www.youtube.com/watch?v=SPvlL5L85Vk](https://www.youtube.com/watch?v=SPvlL5L85Vk)

A picture is worth a thousand words.  No matter how much many of the experienced users have explained this.  Please look at the video and see for yourself what we are going through.

As the video shows, one click is the norm for all forums except UF... this forum.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by QIII on 2014-10-22
Again:  This is an issue for Canonical IT/IS.

None of us -- neither the Moderators nor the Admins -- are Canonical employees.  We all post on a site provided to us as-is by Canonical. To get to it, we have to follow a process dictated by Canonical.  The employees of Canonical are not within earshot of you here.

While the need to vent is quite understandable, it isn't of much use to beat a dead horse here only because the light is better.  Your videos are nice and all, but your concern needs to be directed at those who can do something about it rather than continuing to rail against and make demands of those who cannot.

---

### Post by Elfy on 2014-10-22
> **apollothethird said:**
> [snip] The [s]administrators[/s]/providers/IT (or the powers that be) could allow us to say logged on if they wanted to. [snip]

Snipped a bit - and fixed something ;)

Please see my PM.

---

### Post by apollothethird on 2014-10-28
> **bapoumba said:**
> This is where you have to consider our login method is not standard.

Not standard and defective is two different things.

> Like it or not, it is not.

Actually I don't like it.  Hopefully I can provide enough evidence of this defective format as to have the issue resolved.  The issue would never be viewed or resolved if some diligent person with technical savvy didn't put definition to it.  You wouldn't be so animate to brush it off if you at least understood it.  Instead of bashing me and telling me to like it or leave, you'd have a more appreciated frame of mind for the input.

> 
 The current login method was set up after a forums breach, to prevent it from happening again. Is it the best ? I do not know. This is the one canonical-sysadmins who run and administrate the servers came up with and are supporting. They do all the infrastructure work. If this is what they are comfortable with regarding security, I'm not going to discuss it. There are many points we would like to have access to, including application functionalities, we do not. If the price is too high for you, then I'm sorry you cannot afford it. We cannot make it cheaper.

I understand that you don't have the power to change things.  However you do have the power to understand the problem.  You can't understand the problem without someone pointing it out.

As far as "current login method", that isn't the problem.  You think I'm criticizing the SSO login system.  I'm not.  As far as I'm concerned, I believe it's a great system.  It's just as good of a method as any.  As long as you don't actually know what I'm talking about, I understand that you will try to discourage the discussion and sum it up to lack it or leave.

What you don't know is that it's this discussion what has brought the system up to the current status of working for some users.  Before the thread started it didn't work for anyone.  You don't realize that you are benefiting from this discussion and can benefit even more if you didn't try so hard to stifle it.

> 
Many sites have reinforced their access regarding security (random number based on timestamps, sms confirmation) that require another device to confirm your identity. If you prefer comfort over security, we do not have anything to offer. If the login method drives you away from the forums, then it drives you away from the forums. We are not a commercial site, we are happy to have you here because you enjoy the place and come to share experience and knowledge, ask for support or give support. If not, then they are many other resources you can use, including into the Ubuntu ecosystem.

I'm very sorry for your misinterpretations for my post in such as to have such a rude response.  On one had you are suggesting that I'm welcome to come and share.  That is what I'm doing.  I have just as much concern for security at you.  Any definition of the problem that I have tried to help present doesn't take away any iota of security.

Again, you're able to login with a remember me component and have a comfort zone because of this thread.  The people who listened and understand the problem up to that point made adjustments.  I have seen a lot of fine tuning since the new login system came in place.  This fine tuning only comes because there are users like me who understand what is happening and are offering definition so that the people who has the control can make adjustments.

If you had to change your password hourly for some "so-called" security, I would consider that very much problematic and offer suggestions of how to have security and not have to change the password hourly.  What is very apparent from your discussion is that you don't realize that this is happening to some of the users.  This is not because of the login method.  It has to do with flaws in the setup.

I'm compiling information to present to the powers that be so that they can address the flaws.  At present I appreciate input from this thread to help in that definition.

I'm offering this contribution because I like the OS Ubuntu and I wish to participate in promoting it.  I don't use this form a lot for support.  I mainly use this forum for giving support.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by apollothethird on 2014-10-28
> **bapoumba said:**
> When I am traveling and on the phone I sometimes get the same symptoms, ie constant UF disconnections. Not always, not everywhere. So, to me, not related to my provider, rather to the local network setups (several companies may share the same hardware and the balance and priorities are not homogeneous, they depend on who actually owns the physical tubes).

This could be resolved by fixing the remember me option.  I'll gladly work between whoever is interested as well as the vBulletin team to get the problem resolved.

Of course this happens to you only some times like when you are traveling.  However, it happens to some people all the time and only on UF.  That's because it's a bug in the way vBulletin is setup.  The bug isn't SSO... I would like to strongly emphasize, SSO isn't the problem.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by apollothethird on 2014-10-28
> **varunendra said:**
> Disconnecting while travelling (1+1 hour daily, between office/apartment) is a daily routine for me, and I have trained myself to be mentally prepared for that. Usually it disconnects 2-3 times along the way at certain places, but sometimes I remain logged in even after a new connection is established. Perhaps due to the IP or network remaining the same.

It is usually this time (1 hour per side) in the bus that I get for posting on the forums for last few months. So the problem is affecting me regularly. Pages not refreshing in time after hitting the "submit" button (or ending up in double-posts if I wait too long) seems to have become the "norm" these days, but that is a different issue, shouldn't be discussed here.

What I can't train myself to digest is - I can't even remember which month I logged into launchpad, and I'm still logged in there. Perhaps too much of a convenience. But why is UF alone being treated so [s]differently[/s] badly?

--

I have been given an email as info to someone who may have the authority to start addressing this issue.  I'll keep this thread informed with the development.  I appreciate the feedback that is happening.  Without this feedback, it might appear that I'm exaggerating on something that isn't experienced by the general users.

I'm going to use links from this thread to help represent my presentation.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by bapoumba on 2014-10-29
While you are at it, if the AdminCP timeout could be a bit longer, I'd very much appreciate it.

---

### Post by Mike_Walsh on 2015-02-07
To be honest, I've never found the login process a problem.

I joined after this 'compromise' of the forum security, so didn't know anything about it. I use Chromium most of the time, and occasionally Firefox. I use LastPass password manager in both browsers, which I sign into before doing anything else; I have this set to 'auto-login'. With this, all I have to do is two clicks; one on the forum's bookmark, and one on the 'authenticate to' page.....and I'm in.

Doesn't seem such a big deal.


Regards,

Mike. :)

---

### Post by apollothethird on 2015-02-07
> **Mike_Walsh said:**
> To be honest, I've never found the login process a problem.

I joined after this 'compromise' of the forum security, so didn't know anything about it. I use Chromium most of the time, and occasionally Firefox. I use LastPass password manager in both browsers, which I sign into before doing anything else; I have this set to 'auto-login'. With this, all I have to do is two clicks; one on the forum's bookmark, and one on the 'authenticate to' page.....and I'm in.

Doesn't seem such a big deal.


Regards,

Mike. :)

What you described works for all users on all the forums I visit all the time, except for this one.  It work that way for some of the users of this forum on this some times, but not all the time.  It even works for me on this forum some of the time.  Usually if I log in multiple times in a day.  But if I go a week or so without logging in it doesn't work.  It also stops working that way if I reboot my computer.  But again, what you described will work for all the other forums I visit if I only log in once every few months and boot my computer every day.

It's very unfortunate that it doesn't work on this computer for everyone.  Since it's working that way for you (for now) of course you won't have any complaints.  Also if you don't use a lot of forums and have become accustom to the convenience that all other forums provide, you still won't miss something you are not familiar with.  But if you join a lot of forums and find the convenience (of what you described) works with those forums all the time, you'd start missing it when you have to go though hoops to continue where you loft off here.

By the way, you mentioned that you have to sign in to some type of password manager before doing anything else.  To me (an many people who frequent many forums and don't have a lot of time), we hope that we don't have to sign in before doing anything else.  I didn't sit down to plan to notice a message update in this thread.  I happened to saw a message.  Then I had to take the time to sign in before doing anything else.  If the forum had a "remember me" that actually works properly, as with all other bona fided froms, a single click from the email and I would have been in.

In this case it took me about 7 clicks to actually get in.  The single click too me to the forum.  Then I had to browse around to find the last message (where I left off).  After I found that message I had to use the SSO facility to log in (by the way the SSO remembers me, I with the forum could do it, I would consider the SSO login being compromised more of a security concern than a forum being compromised).

If you can't see the many clicks of [https://www.youtube.com/watch?v=SPvlL5L85Vk](https://www.youtube.com/watch?v=SPvlL5L85Vk) as a problem for many computer users who are not extremely computer literate, I believe you might be lacking in some sense of empathy our fellows.  You described a workaround that you have discovered.  It would be a lot of work to try to get everyone to learn and install your workaround.  I consider this a responsibility of the host to provide ease of use to their clients.

And again, your workaround doesn't work for everyone.  It doesn't work for me.  My password manager remembers my password.  Loosing and not remembering the password isn't the problem.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by coffeecat on 2015-02-08
For the record for the other forum admins, I've just bumped RT ticket #22858 - again.

Until Canonical IS respond to the ticket we bumped 2½ months ago, there is nothing more that the forum admins can do.

> **apollothethird said:**
> 
In this case it took me about 7 clicks to actually get in.

Then you are doing something wrong. It takes me two clicks to log into the forum via Ubuntu One SSO. Every day. Every time. Without fail. 

I always log out when I have finished what I wish to do on the forum. I do not find having to log in again a burdensome thing, since - to repeat - it takes me two clicks, every time, every day, without fail.

---

### Post by apollothethird on 2015-02-08
> **coffeecat said:**
> For the record for the other forum admins, I've just bumped RT ticket #22858 - again.

Until Canonical IS respond to the ticket we bumped 2½ months ago, there is nothing more that the forum admins can do.



Then you are doing something wrong. It takes me two clicks to log into the forum via Ubuntu One SSO. Every day. Every time. Without fail. 

I always log out when I have finished what I wish to do on the forum. I do not find having to log in again a burdensome thing, since - to repeat - it takes me two clicks, every time, every day, without fail.

Hi, coffeecat.  Please look at [https://www.youtube.com/watch?v=SPvlL5L85Vk](https://www.youtube.com/watch?v=SPvlL5L85Vk) and tell me what I'm doing wrong.  If you can turn the many clicks into one click without I'll be glad to propagate how to do it and resolve the problem that many users are having.  I posted that video because a number of people had accused some of the users of lying.

The many clicks in the video was the minimum I could get down to while practicing and doing the best I could do, to avoid being accused of lying and embellishing.  The seven clicks of yesterday was the results of just going in, reading the message, then performing clicks so that I could pickup where I had left off and post and update to the forum.

I can log in with just a couple of clicks.  But for most of us logging in isn't the final objective.  We want to log in, then pickup where we left off.  When I login with the minimum of two clicks I'm logged in to the forum.  Then I have to spend clicks to go to where I want to participate.

Today I was in without any clicks.  I click on my email and was in where I left off.  It worked just like it works with all forums (this particular time).  It doesn't do that every day.  There are circumstances for some users where they are lucky.  I believe you have the luck of logging in every day which might minimize some of your clicks.  Some of us can't log in everyday.  You also might have the luck of having an IP that doesn't frequently change.  Some of us don't have that luck.  So you are among the lucky ones who may have a form of "remember me" that some of us can't enjoy.

I really hope that you with your position would have some compassion for the users who don't have that and allow the computer to automate this for us, just like all the other forums do.

I understand that you can say, you don't care, we should just be happy with what is doled out to us.  But I really hope you appreciate the feed back that you are getting from your good users who understand this  very real technical problem.

When you brush it off as if it isn't happening you minimize the likelihood of the powers that be from taking serious interest.  I would expect for them to look at your post and your position as ambassadors for a hint to as if a real problem exist or not.

By your post, I understand that you are not seeing it.  I'm just trying to help to clarify the problem to you so that you can see it.  I appreciate your dedication that you can't wait a few days or a week, then log on and see if you can still enjoy the only two clicks to pickup where you left off... or if you can afford of invest in an IP change (like many people have) and see if the "remember me" still works for you.  I have actually invested money to test the problems that the users has described in this thread.  The problems are real.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by Cavsfan on 2015-02-08
Beating a dead horse here...  :p

But having proper cookie management and bookmarking the forum solves this problem. 
I start out navigating to the forum by typing "ub" in the address bar and since it is a bookmark it fills the rest in.
Just the 2 clicks when it's been over so many hours since last login. 
Also same 2 clicks to get in when I switch operating systems...

Then once you're back in and want to find where you were headed in the first place, all you have to do is click on settings at the top right. 
You'll see a list of what threads you are subscribed to.
Just click on each one and then click "view first unread post" at the top near Thread tools. 
Then you will miss nothing.

Or if it's a thread that you are not subscribed to open another tab, login and then go back to the first tab and click refresh.

To me this is a non-issue. Although I get that it'd be nice to be remembered in this forum permanently... But, it does not slow me in the least.

I believe admins have a harder problem than we do but I don't know.

---

### Post by apollothethird on 2015-02-08
> **Cavsfan said:**
> Beating a dead horse here...  :p

The horse doesn't have to be dead.  The issue is real.  The issue is current.  It could actually be resolved.

Because of the feedback in this forum, the problem isn't as bad as it was when it first started.  Also, because of the feedback, some of the forum administrators has acknowledged that they are starting to understand the problem.

Also, there are many who are starting to realize the problem, and are trying to describe it.  They are benefiting by the ones who has the knowledge and can help them to clarify it.

Also, many people such as you are giving advise and workarounds that are helping some people to minimize the problem in their environments.  While the workarounds, including the ones you are giving, won't work very everyone, it's something that will benefit some.

> 
But having proper cookie management and bookmarking the forum solves this problem. 
I start out navigating to the forum by typing "ub" in the address bar and since it is a bookmark it fills the rest in.
Just the 2 clicks when it's been over so many hours since last login. 
Also same 2 clicks to get in when I switch operating systems...

It only takes me a couple of clicks as well as anyone a couple of clicks to get into the forum.  Logging in and getting in to the forums isn't the problem.  Being able to easily get to a specific point by having a common "remember me" without actually logging in, just picking up where you left off is the problem.

When I do the bookmark, cookies and all the other things you describe... the actually "SSO" login takes me to the top of the forums.  It doesn't take me to the specific place the I'm trying to go to.  It also doesn't take me to the new messages.  When I go to the top of the forums, now I have to perform "clicks" navigation to find where I left off so that I can read my new messages and post or reply to them.

I'm sure many of our novice users who gets an update to one of their questions a few weeks later, click on the email and read the update.  However, by the time they try to reply to the email, it takes them more time and trouble to find the actual thread.  If they respond they usually start a new thread to reply to the users.  

> 
Then once you're back in and want to find where you were headed in the first place, all you have to do is click on settings at the top right. 
You'll see a list of what threads you are subscribed to.
Just click on each one and then click "view first unread post" at the top near Thread tools. 
Then you will miss nothing.

Or if it's a thread that you are not subscribed to open another tab, login and then go back to the first tab and click refresh.

To me this is a non-issue. Although I get that it'd be nice to be remembered in this forum permanently... But, it does not slow me in the least.

I believe admins have a harder problem than we do but I don't know.

You describe a workaround that is significantly different from the one the previous users described who are saying it only takes two clicks.  You described opening up new browser tabs, looking around for links to click on.  All those are clicks and inconveniences that are complicated and labor extensive to many casual users who are doctors, lawyers, and other professionals who don't have the time to become a guru to use a forum.

Even the powers that bring us the forum might no realize this is a real problem if a user not understanding the problem describes it as a non-issue.  I can figure out the clicks and navigate with all the necessary distractions to find out where I left off and pickup where I left off.  I type over a hundred words a minute.  But again, with all my speed and skill, I realize the distraction of the flaw and hope to share it.

The user yesterday ([Mike_Walsh]("http://ubuntuforums.org/showthread.php?t=2165623&p=13223914#post13223914")) who said when he gets ready to use this forum, he first performs a ritual of loading his "LastPass password manager" before doing anything else.  He said he only has to do two clicks, but he doesn't take in to account that loading whatever he loads as a workaround to prepare to use this forum actually takes time and it takes clicks.

If it really wasn't a problem, then these people, including you, wouldn't have a need to describe their rituals for trying to get around the problem.  Clicking on the notification link in the email would work.  It would take us to the thread in one click every time... no special tricks or workarounds.  It would just work.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by Elfy on 2015-02-08
> **Cavsfan said:**
> Beating a dead horse here...  :p...

Not at all.

It's unfortunately the case that *we* can't do anything about it though, if we could we would have long before anyone else was allowed back on the site.

All we can do is what we have done.

---

### Post by Cavsfan on 2015-02-08
> **apollothethird said:**
> You describe a workaround that is significantly different from the one the previous users described who are saying it only takes two clicks.  You described opening up new browser tabs, looking around for links to click on.  All those are clicks and inconveniences that are complicated and labor extensive to many casual users who are doctors, lawyers, and other professionals who don't have the time to become a guru to use a forum.

....

If it really wasn't a problem, then these people, including you, wouldn't have a need to describe their rituals for trying to get around the problem.  Clicking on the notification link in the email would work.  It would take us to the thread in one click every time... no special tricks or workarounds.  It would just work.


Again, I have no problem and do not feel like I go through any "workaround" or "ritual" to login to the forum and get to what I want.
I do not receive emails when someone replies to a thread I'm subscribed to anyway. I simply login and click settings to find any replies as I described in my previous post.

 I described this method in a previous post in this thread. One method involving Firefox and another using Chromium. Obviously this login process looks at cookies and no one wants to have every cookie from every site they have ever visited stay on their computer forever.

I use this method to clear my cache, etc when I close Firefox [https://support.mozilla.org/en-US/kb/how-clear-firefox-cache#w_automatically-clear-the-cache](https://support.mozilla.org/en-US/kb/how-clear-firefox-cache#w_automatically-clear-the-cache)
But this does not clear my cookies.
I have this addon that allows me to "opt-in" to save only the cookies I want [https://addons.mozilla.org/en-US/firefox/addon/biscuit-220876/](https://addons.mozilla.org/en-US/firefox/addon/biscuit-220876/)
So, when my browser closes the protected ones are saved and the rest are deleted.

Sure, it takes a little bit to setup but you only need to do it once and done. However, you seem fairly proficient by being able to mention others by name [apollothethird]("http://ubuntuforums.org/member.php?u=1176033").
Because doing that took me about 100 times longer than it does for me to login even if it has been days since my last login. 
I have 4 Linux systems on this box and when I logout of one and into another I have to click on "login in with SSO"; like I say 2 clicks and done. 

I would think that doctors and lawyers, etc. are not computer illiterate or novices at all as they most probably used computers to get to where they are.

Again, you may find this an insurmountable issue. I hope that they do fix this for you and others that think it is difficult to login to this forum. 
But, for me and many others this is simply a non-issue.

> **Elfy said:**
> All we can do is what we have done.

I know you admins have done all you can and it's much better now with the timeout being a lot longer than it initially was.
I simply do not have a problem with it.

---

### Post by apollothethird on 2015-02-08
> **Cavsfan said:**
> Again, I have no problem and do not feel like I go through any "workaround" or "ritual" to login to the forum and get to what I want.
I do not receive emails when someone replies to a thread I'm subscribed to anyway. I simply login and click settings to find any replies as I described in my previous post.

 I described this method in a previous post in this thread. One method involving Firefox and another using Chromium. Obviously this login process looks at cookies and no one wants to have every cookie from every site they have ever visited stay on their computer forever.

I use this method to clear my cache, etc when I close Firefox [https://support.mozilla.org/en-US/kb/how-clear-firefox-cache#w_automatically-clear-the-cache](https://support.mozilla.org/en-US/kb/how-clear-firefox-cache#w_automatically-clear-the-cache)
But this does not clear my cookies.
I have this addon that allows me to "opt-in" to save only the cookies I want [https://addons.mozilla.org/en-US/firefox/addon/biscuit-220876/](https://addons.mozilla.org/en-US/firefox/addon/biscuit-220876/)
So, when my browser closes the protected ones are saved and the rest are deleted.

Sure, it takes a little bit to setup but you only need to do it once and done. However, you seem fairly proficient by being able to mention others by name [apollothethird]("http://ubuntuforums.org/member.php?u=1176033").
Because doing that took me about 100 times longer than it does for me to login even if it has been days since my last login. 
I have 4 Linux systems on this box and when I logout of one and into another I have to click on "login in with SSO"; like I say 2 clicks and done. 

I would think that doctors and lawyers, etc. are not computer illiterate or novices at all as they most probably used computers to get to where they are.

Again, you may find this an insurmountable issue. I hope that they do fix this for you and others that think it is difficult to login to this forum. 
But, for me and many others this is simply a non-issue.



I know you admins have done all you can and it's much better now with the timeout being a lot longer than it initially was.
I simply do not have a problem with it.

You keep making a reference to logging in and how it's not a problem.  This thread isn't about logging in being a problem.  No one has a problem logging in.  Anyone can log in without going thought the complicated description you mentioned for how you log in.  All anyone has to do is click on the site, click on the SSO and they are logged in.

You are missing a very important component of using forums.  All forums including this one has a feature to provide notifications when one of your subscribed threads are updated.  In all forums (except for this one) a single click on the email and you're remembered (remember me) and immediately in the updated thread, exactly where you left off.  You don't have to spend clicks looking for the thread and looking for where you left off.  It's all automatic... and again, this is common for all forums that I have used in the past twenty years.  The forum uses it, but this is the only forum where it doesn't work (the notification email).

Of course you don't miss it, nor notice it.  You have just mentioned that you don't use email notifications.  You also mentioned that you don't appear to appreciate the convenience of cookies.  However, I appreciate them.  I prefer the cookies that provides these facilities of the forums I visit to be available forever.  If I go six months without logging in to a forum where I participate, I hope to pickup where I left off if I get a notice of one of my subscribed forums being updated.  It works with a single click on all forums except for this one.

I read the detailed description of what you do to keep up with what you do on the forum.  It sounds like a lot of work.  I don't think a user should have to go though all that work just to participate on the forums.

If someone thinks this thread is about logging in and having problems logging in, I would expect for the quest for relief to be ignored.  But if it's clear enough that logging in isn't a problem or issue, the issue is the many clicks to pickup where you leave off (which would be resolved by a simple properly configured "remember me") this might be more likely to be looked at.

I'm not having any problems today.  I'm not doing any of the work that you described that you do to use the forum.  I just click on the notification link (a single click) and I'm in exactly where I left off.  The problem is that I don't know how long this will last.  I don't know if it last in a matter of hours or days.  But the problem is that the system will soon forget me and I'll have to logging in again.  I can log in with two clicks, just like you.  Then I spend a number of other clicks to search where I left off.  I gave you a youtube link showing what a user has to go through when the system logs them out.  Being logged out is the problem.

Some of the people's in this thread login doesn't survive a full day.  Many of the forum administrators understand how to activate the "remember me" (whatever is happening to log out the users).  If the problem can be understood clear enough so that the powers that be will give them permission (and controls) to provide the "remember me" then the issue would be resolved.

You prefer to perform your couple of clicks and log in each time.  I don't prefer to log in.  I'm enjoying the single click of having the system "remember me" for this immediate day.  When the system chooses to log me out, it's the many clicks I have to perform to browse around to figure out where I left off that I have a problem with.

By the way the quote of the user's name that I used in my message was a link to his message of which I was making a reference to.  You missed my point.  I hope you will review my message and see my intentions.  I wasn't trying to link to his profile which is already automatically linked by the system with their immediate post.

Take another look at what [apollothethird]("http://ubuntuforums.org/showthread.php?t=2165623&p=13224569#post13224569") is saying.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by Elfy on 2015-02-09
Just so that people know what it is that we're having to fight against.

We were told this in October 2013 - 

> After further investigation, it seems that the "Remember Me" option
cannot be made available in the new SSO/OpenID world.

Since that time we have been carrying on trying to get them to help you. 

Please don't think that we're ignoring this issue - we know it affects some of you.

---

### Post by apollothethird on 2015-02-09
> **Elfy said:**
> Just so that people know what it is that we're having to fight against.

We were told this in October 2013 - 



Since that time we have been carrying on trying to get them to help you. 

Please don't think that we're ignoring this issue - we know it affects some of you.

Hi, Elfy.  We know that the moderators are doing all they can and we have a lot of appreciation for your concern and the hard work that you are doing.  For the others who are posting workarounds, I think your input is also great.  My updates are to help the ones suggesting workarounds (such as cookies) are not the issue, nor the problem.  I hope the ones who are confused with the subject of the thread don't mind my effort for clarification.  This way if they fully understand it, their suggestions might become more on target.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

### Post by JKyleOKC on 2015-02-09
I'll add my own workaround just in case it helps someone. It's simply that I never log out of the web site, and make it a point to visit at least once every 24 hours, from the same IP. This results in going directly to the referenced message when I click on the link in a notification Email, still logged in and able to reply.

In addition, I have a Firefox shortcut to my list of subscribed threads. When I'm away for more than 24 hours, or some other situation makes the over-sensitive security system log me out, I can go immediately to my subscribed list rather than to the top of the forum. It's not down to just two clicks, but the automatic redirection feature TPTB saw fit to include does make it relatively easy.

---

