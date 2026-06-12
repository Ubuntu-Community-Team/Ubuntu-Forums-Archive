---
title: "SSO login general chat thread"
date: 2013-07-29
forum: Forum Feedback &amp; Help
---

### Post by coffeecat on 2013-07-29
I've moved all the chat and other stuff from the[ SSO login sticky]("http://ubuntuforums.org/showthread.php?t=2164051") to here. This thread is for general discussion about SSO login. Please confine any posts to the sticky to suggestions for amendments/additions to the first post there.

If you have inadvertently created a duplicate account, or need an admin to deal with a problem with your account related to SSO login, please post in the [Resolution Centre]("http://ubuntuforums.org/forumdisplay.php?f=123"), giving the username of your old account.

---

### Post by BLFLpb3 on 2013-07-30
Okay, I'm not trying to be too critical here, but this seems like a step in the wrong direction security wise.  Your forum software got hacked.  It happens, and as someone that runs a forum as well, I've had it happen to me before, though on a much smaller scale.  The immediate reaction is to try to increase security through any means necessary, and that's the right step; however, tying together our forum logins with our Ubuntu One accounts seems like it has the potential to link together potentially insecure forum software with an account that for many people contains a lot more sensitive information than they would ever have with just a standard forums account.

Ubuntu One, unless I'm mistaken, potentially has credit card info, private cloud storage files, and a record of purchases that people have made as well.  I've personally not used it for any of these things, but I'm sure there are quite a few people who have.  If I did have that kind of info stored in there, I'd be gravely concerned about it being linked with a forum that was just compromised, no matter what level of new security was just added to it.  That's just me though...

---

### Post by BLFLpb3 on 2013-07-30
Hmm.  Just one extra note here: 'BLFLpb3' is very definitely not a nickname I chose anywhere for my account.  I'm not sure if that's some kind of randomly generated name that it gave me to protect my identity, or if it's a bug with your login system.  In either case, I apparently can't edit it at all because my account is too new.

The migration process you have setup for people seems very un-intuitive here.  Hopefully this doesn't come across at me having too much of an ego here, but I'm pretty certain that if I'm struggling to wade through all this, there's quite a number of other users who are too.

---

### Post by MadmanRB on 2013-07-30
Actually the move to Ubuntu sso is actually a good move, unlike vbullitin the culprit of the issues that made the foums go down ubuntu one and its sso services are their own thing seperate from most other components.
Sure its extra steps now but its not that big of a deal.

---

### Post by Cheesemill on 2013-07-30
> **MadmanRB said:**
> Actually the move to Ubuntu sso is actually a good move, unlike vbullitin the culprit of the issues that made the foums go down ubuntu one and its sso services are their own thing seperate from most other components.
Sure its extra steps now but its not that big of a deal.

+1

By switching to using SSO with Ubuntu One the potential for damage is decreased.

If the forums are ever hacked again then there is now no password information stored on the forums server ***at all***, not even in hashed form.

---

### Post by j2bv16 on 2013-07-30
> **MadmanRB said:**
> Actually the move to Ubuntu sso is actually a good move, unlike vbullitin the culprit of the issues that made the foums go down ubuntu one and its sso services are their own thing seperate from most other components.
Sure its extra steps now but its not that big of a deal.

Very good move. SSO is more secure. And the accounts will be linked.

---

### Post by BLFLpb3 on 2013-07-30
> **MadmanRB said:**
> Actually the move to Ubuntu sso is actually a good move, unlike vbullitin the culprit of the issues that made the foums go down ubuntu one and its sso services are their own thing seperate from most other components.
Sure its extra steps now but its not that big of a deal.

The problem is that by using it at all here, there's some kind of cross authentication being used between the forums and an Ubuntu One account.  I'm sure that they kept security in mind when designing the system that allows the two to talk to each other, but there's always that remote possibility that an insecurity on the forums could result in tokens being grabbed that let attackers backpedal into the Ubuntu One account of a user through something like a cross site scripting attack.

Even if the new system is designed 100% correctly to prevent this though, it still just doesn't give me a warm fuzzy feeling having the two linked together.

Maybe I'm just paranoid though.

---

### Post by PaulW2U on 2013-07-30
> **j2bv16 said:**
> Very good move. SSO is more secure. And the accounts will be linked.

Agreed. 

And despite the problems that some users seem to be having, what we have been told to do when logging in for the first time **does** work. I've reset my Ubuntu One email address back to what it was previously, logged out of the forums and logged back in again and all is well.:)

---

### Post by coffeecat on 2013-07-30
@BLFLpb3, it's possible that the reason the system chose an apparently random string for your username is that you did not fill in the username field in the Ubuntu One SSO account - only the real name field. I've taken this up with Canonical sysadmins to find a workaround. In the meantime, pm me with 3 alternative choices for your forum username and I can change your account details accordingly.

Please also confirm whether or not this assumption is correct - that your SSO username is a blank field. We need this to be sure we're on the right track.

---

### Post by hLtbPDh on 2013-07-30
After years of interaction with other members on this forum, we get to know each other by our usernames. Now that we don't have access to them, we have no idea who we are talking to, or who is replying to us. We can't find each other on these forums any more. We may still recognize the moderators, but how will they know us? There were relationships built here on this forum that have now been erased by some arbitrary policy somebody came up with in a state of panic. That policy may have been a good idea, but maybe the implementation process could have been thought through and checked out a little more thoroughly.

Creating an Ubuntu One account with the same email address was no guarantee that the accounts would be associated. Someone should have looked into that more carefully. Also, the usernames didn't come out as expected either. The username hLtbPDh is in no way a variation of Luxx, Luxx1, Luxx2. I'm seeing more of these wierd names on the forums and wonder how many people are feeling as lost as I do in a place that was once a kind "home" where we felt like part of a family. This is really a mess.

Considering the urgency of the fixing the breach, I hope someone is also working on a way to remedy the damage caused by the fix. It is no less severe than the original breach, and may actually be worse.

---

### Post by PhobosK on 2013-07-30
[SOLVED]
To the @Admins...

I guess this is not of top importance to be fixed, but the settings page of the forum profile is blocked by permissions... i.e. one cannot Edit his profile etc...
Shall we hope we will have access to those at some point in time?

[SOLVED] Upps sorry ... my fault... it seems like I am below 25 posts now.... so it is a standard access permission "problem"

---

### Post by thefluffyone2 on 2013-07-30
My previous account was "TheFluffyOne". I don't have a huge post count, but I like to keep the same username on various forums.

So I have set my Ubuntu One preferred email to the same as my old forum email address and it doesn't seem to have linked to the old account. I am now "thefluffyone2"... something isn't working right here :(

---

### Post by mniess on 2013-07-30
Wow. There could have been a bigger warning. I went to the forums, logged in with SSO and now I have for ever lost my account? This really sucks. There really should be a warning when you do the first login.

---

### Post by Lightning Dragon on 2013-07-30
I don't mind the change, I guess, only that there was no way to re-get your forum email to associate it to the Ubuntu One email. I could not remember mine and by freak chance entered one that it accepted. I would suggest that you allow an option to get people to find their emails properly. Because the "reset password" does not work; it sends mail to the email you entered regardless if it is in use or not, so it is basically useless in finding out your real email used on the forums.

---

### Post by Buntu Bunny on 2013-07-30
All I can say is, it's good to be back.

---

### Post by sandyd on 2013-07-30
> **mniess said:**
> Wow. There could have been a bigger warning. I went to the forums, logged in with SSO and now I have for ever lost my account? This really sucks. There really should be a warning when you do the first login.

Is your prefered email (see below) set to the same one used in your forum account?
[IMG]http://s18.postimg.org/amfwdxlqx/ubuntulogin.png[/IMG]

---

### Post by hamiljf on 2013-07-30
Not here to argue with the rights and wrongs of security... just really confused.  I've (obviously) been able to sign on after the hackevent and at some point in the process found a place to set a new password.  But can someone draw a simple picture showing how OpenID, SSO, UbuntuOne (which I don't use) these Forums (Fora ?) and Launchpad are all connected.
And if somehow I've acquired an OpenID, can there be only one for me, and how can I check ?

---

### Post by sandyd on 2013-07-30
> **hamiljf said:**
> Not here to argue with the rights and wrongs of security... just really confused.  I've (obviously) been able to sign on after the hackevent and at some point in the process found a place to set a new password.  But can someone draw a simple picture showing how OpenID, SSO, UbuntuOne (which I don't use) these Forums (Fora ?) and Launchpad are all connected.
And if somehow I've acquired an OpenID, can there be only one for me, and how can I check ?

fyi, Ubuntu did some merging - Ubuntu One does not only include the backup service now - Ubuntu One _is_ the SSO system used. Ubuntu One is the SSO used to login to launchpad, askubuntu, the forums ,etc ,etc ,etc

---

### Post by mabynke2 on 2013-07-30
> **sandyd said:**
> Is your prefered email (see below) set to the same one used in your forum account?

As can be deducted from my current username, I did the exact same thing as mniess and am now unable to access my original account.
When I noticed my mistake, I tried changing the Ubuntu One email to match what I am sure is the email of my original Ubuntuforums account, and then log in again. However, I am still logged in to mabynke2. I guess that the two accounts are now "properly" linked up, and that the forum therefore makes no attempt to change anything. Is there any hope for regaining access to my zombie account?

---

### Post by brumfield-glenn on 2013-07-30
+1
Same username since 2006, same email account for several years and now I'm zeroed out to newbie status with no way to recover. I hope we come up with a way to get back to the way it was; I can't even remember my own username anymore ;)

---

### Post by Iowan on 2013-07-30
Although I hate to suggest flooding the Resolution Centre, a thread there will let us work on fixing your account(s).  There is a procedure (I haven't tried yet) to disassociate your current account/OpenID, which should let you relink with your old one - which still exists.

---

### Post by coffeecat on 2013-07-30
I won't answer people individually who have found themselves with new user accounts for whatever reason, in case I miss anyone. In any case, individual problems get lost in a long thread like this.

If you need admin help rescuing your old account, please post (politely!) in the [Resolution Centre]("http://ubuntuforums.org/forumdisplay.php?f=123"), giving as much information as you can, including the name of your old forum account. An admin will help you in due course, but please be patient. There are only a handful of us and we are all part-time volunteers. Please do not post your email addresses - these can be harvested by spam bots and this will result in more spam to your email account. If we need to confirm email addresses we will find a confidential way of doing that.

---

### Post by ventrical on 2013-07-30
> **BLFLpb3 said:**
> Okay, I'm not trying to be too critical here, but this seems like a step in the wrong direction security wise.  Your forum software got hacked.  It happens, and as someone that runs a forum as well, I've had it happen to me before, though on a much smaller scale.  The immediate reaction is to try to increase security through any means necessary, and that's the right step; however, tying together our forum logins with our Ubuntu One accounts seems like it has the potential to link together potentially insecure forum software with an account that for many people contains a lot more sensitive information than they would ever have with just a standard forums account.

Ubuntu One, unless I'm mistaken, potentially has credit card info, private cloud storage files, and a record of purchases that people have made as well.  I've personally not used it for any of these things, but I'm sure there are quite a few people who have.  If I did have that kind of info stored in there, I'd be gravely concerned about it being linked with a forum that was just compromised, no matter what level of new security was just added to it.  That's just me though...


That's an excellent theory , especially if there is a man-in-the middle and, of course, presumming it was an inside job. There are things that IS knows, believes and does not know. Whether or not the hacker or hacker group is lying in wait remains to be seen. However, on a lighter note, the effort that went into vetting the database and subsequent copy was done by personel who were offsite from actual forum admins and moderators. Therefore we have to once again trust the meritocracy philology that current ubuntu forum council members are synchronized and on the same page. It was a wise move to  incorporate a secondary tier of security which is SSO. So if there is a hand-off somewhere within the works it will be easily detected.

---

### Post by kansasnoob on 2013-07-30
Thanks for all the hard work, I'm sure this had to be a nightmare.

In case it's at all helpful, after updating my SSO profile which I use for the iso-tracker and Launchpad I had to wait a while before I could log into my existing forum acct. I had some other tasks to attend to away from the desk so I ended up waiting about two hours.

I'm not sure what the appropriate time is for the SSO database to update???? But patience is truly a virtue ;)

---

### Post by Newbunto on 2013-07-30
I realise that you guys have had a difficult time dealing with "the hack" but this process doesn't seem to work very well. (However I got there in the end.)

Scenario: Existing Ubuntu Forums user without Ubuntu One account trying to create Ubuntu One account in such a way as not to lose access to existing forum profile etc.

I tried to follow the instructions but when I tried to create a Ubuntu One account I just got an error message like "This email address cannot be used" with **no further explanation**. After some flailing around I think that what this is telling me is that I already had a Ubuntu One account even though I didn't know it. So I did a password reset on my Ubuntu One account and that got me over that hump.

The next problem was with the login to the forum itself. It kept on saying that it didn't have my email address and so it prompted me for it, which is OK, but then when I entered the email address (with correct retyping of the email address for confirmation) it would reject the email address. (Sorry, don't remember error message.) After some more flailing around I think that the problem here is that in the interface between the "OpenID" and the Ubuntu Forums I didn't tick the checkbox to pass the email address - and then whatever Ubuntu Forums is doing to solicit the missing email address doesn't work ! (I think here that I misunderstood what those three checkboxes are asking me. If it won't work unless a checkbox is checked then best to grey it out or remove it altogther.)

So to summarise some of the issues.

* People who signed up some time ago to Ubuntu Forums may not remember what email address they used. (For example, I don't have email notification enabled so don't routinely get emails from the forum.)

* People may be unsure of whether they do or don't have a Ubuntu One account already. (Where did the existing unknown account come from?)

* Obscure error messages that don't give the user a hint about what to investigate.

and of course the most fundamental issue, the chicken and egg,

* Can't post for help until problems are resolved.

But thanks for everything that *is* working.

---

### Post by Newbunto on 2013-07-30
> **BLFLpb3 said:**
> however, tying together our forum logins with our Ubuntu One accounts seems like it has the potential to link together potentially insecure forum software with an account that for many people contains a lot more sensitive information than they would ever have with just a standard forums account.

Yes, that was my thought.

"Single sign-on" is convenient for users but it violates the very solid security advice not to use security credentials in multiple contexts.

(Yes, keeping track of literally hundreds of usernames and passwords is a hassle but it does act to limit the damage if one place is compromised. It is my choice to accept that hassle and get higher security.)

The idea of removing all authentication responsibility from the server on which the forum is hosted is good. That in no way implies that you have to reuse security credentials from another context.

*Let's assume though that the new arrangements are permanent ... how would a user go about fixing this?*

I assume that they would need to create a second Ubuntu One account to replace their existing Ubuntu One account and then move everything over to the second account, keeping the first account only for Ubuntu Forums. Or alternatively, use the second account only for Ubuntu Forums i.e. ditch their Ubuntu Forums profile and become a newb again. LOL.

---

### Post by bcschmerker on 2013-07-30
I may have been a little slow to figure it out, but Ubuntu® One™ SSO supports my existing Launchpad™ account, so one Login should gain me access to both Launchpad™ and these Forums.  This is a secure enough solution for my requirements - and adaptable enough to compensate, should I find need to close down my Yahoo*!*® account and go with another E-mail service.

---

### Post by 8E7M67w on 2013-07-30
OK wait, my emails were different on the U1 and forum.  To log into the U1 I had to use the associated U1 email, so now I can't access my old forum account/profile and so of course I can't change that email to match the U1 account.  :confused:  WHAT? I hope that by logging in via U1 SSO I haven't lost EVERYTHING???????  What do I do now and why aren't there obvious instructions for us somewhere?????

---

### Post by Newbunto on 2013-07-31
> **bcschmerker said:**
> I may have been a little slow to figure it out, but Ubuntu One SSO supports my existing Launchpad account

Ditto. With the benefit of hindsight this, I think, is what caused my first problem.

---

### Post by FWIW on 2013-07-31
Hmm.  I find this conclusion to the wait for the forums to return to be a bit of a disappointment.  I created my account here in 2006, probably to ask a question.  Whatever the case, I haven't used it since.  Then last week I get the e-mail advising of the hack.  But here's the thing.  I don't know what password I was using on here back then.  There is some chance that it is the same as some of my current passwords for various online accounts and such.  I had kind of naively hoped that when the forums came back I could try to log in using my e-mail address and most likely password (and failing that one of several other possible passwords), which would have told me whether I needed to go changing any of my passwords elsewhere.  Now I have little option but to spend a lot of time going around the whole lot and changing all of them.  That's not going to be fun.  I wish there was an alternative.

---

### Post by cariboo on 2013-07-31
> **8E7M67w said:**
> OK wait, my emails were different on the U1 and forum.  To log into the U1 I had to use the associated U1 email, so now I can't access my old forum account/profile and so of course I can't change that email to match the U1 account.  :confused:  WHAT? I hope that by logging in via U1 SSO I haven't lost EVERYTHING???????  What do I do now and why aren't there obvious instructions for us somewhere?????

Change your Ubuntu One email address to the same as the one you used for your forum account, then once you've logged into the forum, you can change your Ubuntu One email address to whatever you want, as SSO login doesn't depend on email addresses, after the first login.

---

### Post by Aide9aic on 2013-07-31
> **BLFLpb3 said:**
> Your forum software got hacked... tying together our forum logins with our Ubuntu One accounts seems like it has the potential to link together potentially insecure forum software with an account that for many people contains a lot more sensitive information than they would ever have with just a standard forums account.
> **MadmanRB said:**
> unlike vbullitin the culprit of the issues that made the foums go down
This report, from a Ubuntu forum admin, would disagree with assertions that the forum software was "hacked" or that vBulletin was somehow to blame.

[http://ubuntu-discourse.org/t/looks-like-ubu-forums-was-just-defaced/603/65](http://ubuntu-discourse.org/t/looks-like-ubu-forums-was-just-defaced/603/65)
> We now know what happened, it wasn't anything to do with a security hole in VB, **all this came about via social engineering and legacy problems left over from when the previous owner was still running the forum**. For some reason, some of the loco mods had admin privileges, and it was one of those accounts that was compromised, along with quite a few hooks in pnp that allowed the attacker tp deface the site. Canonical IS is in the process of rectifying the problems.

---

### Post by Fh7p6mG on 2013-07-31
I'm pretty sure that "Fh7p6mG" is neither my previous forum username, nor is my login.ubuntu.com username. I have no idea where this was picked up from. Suffice to say I've now lost all my subscriptions and post counts. Whilst I fully understand the reasons behind this, it doesn't appear to be working for a significant portion of the users.And yes, I did make sure my main email account in login.ubuntu.com is the same as my old ubuntuforums.org email address.

---

### Post by blenderfox on 2013-07-31
Okay, I managed to fix it. I had to create a NEW login.ubuntu.account (even though I have one already), with the same email address as my ubuntuforums one, even though I had set my previous ubuntu.com account to have the same preferred email as my forums account. So now I'm using two SSO accounts. Not ideal, but I guess I'll have to live with that.

---

### Post by loukingjr on 2013-07-31
Trying to create an SSO account was extremely unintuitive to say the least. But there is an issue I find much more annoying. When I receive an email notification of a thread I'm following and I click on the link, it does take me to the page. However, if I don't log in I will not receive further notifications. If I do log in, instead of taking me back to the page I was on, it takes me to the home page of the forums. The other problem is, apparently you can't stay logged in as you could before. So every time I get a new email notification I have to relog in. This all seems more trouble than it's worth.

---

### Post by Newbunto on 2013-07-31
> **FWIW said:**
>  I don't know what password I was using on here back then.

If you ask nicely perhaps someone will make the salt and the hash of your old password available to you. Then you can test the various passwords that you think it might be.

  > There is some chance that it is the same as some of my current passwords for various online accounts and such.

It goes without saying that you should just **never ever** do this.

> Now I have little option but to ...

If you think that any of your passwords is strong enough to survive MD5 brute forcing then you can take a punt and not change that password.

---

### Post by deadflowr on 2013-07-31
> **Newbunto said:**
> If you ask nicely perhaps someone will make the salt and the hash of your old password available to you. Then you can test the various passwords that you think it might be.


The only person who can get you your old password is the hacker, as Canonical IS overwrote all passwords and randomised them.


If you feel that you might have used the same password on any other site, or system, then change them.
In fact, for good measure, change all your passwords.

---

### Post by TLD98541 on 2013-07-31
> **Newbunto said:**
> 
I tried to follow the instructions but when I tried to create a Ubuntu One account I just got an error message like "This email address cannot be used" with **no further explanation**. After some flailing around I think that what this is telling me is that I already had a Ubuntu One account even though I didn't know it. So I did a password reset on my Ubuntu One account and that got me over that hump.


I had this exact same problem, happily i read this post before i screwed up my account here.

---

### Post by von Stalhein on 2013-07-31
Just happy it's back. Very happy.

Severe withdrawal symptoms exacerbated by a broken machine and only being able to operate in Windows until I build another one were made even worse by not being able to experience Ubuntu vicariously.

First world problems eh?

---

### Post by ofnuts on 2013-07-31
OK, so I was on of the lucky ones who got the same account after registering on SSO :)

IMHO the whole thing is a bit overboard. As long as I am not moderator or admin, there is no need for a really secure forum access. Using a trivial password exposes yourself to what? Someone who masquerades as you to troll people? Big deal... When I received the mail from UF about hacked accounts, I didn't raise an eyebrow... even the mail userid isn't the main one so it cannot be used to log in on my mail box.

Now the very down-to-earth and practical question: in the former life of Ubuntu forum, I could have a bookmark on [http://ubuntuforums.org/usercp.php](http://ubuntuforums.org/usercp.php) and the userid and password kept by Firefox so checking out new stuff on UF was a one click operation. Now it takes me through several pages and leaves me in UF home. So what can I do to get back to the original? What id should I use to login? the UF one? My name on U1? My mail for U1?

---

### Post by Seb71 on 2013-07-31
I managed to regain access to my old forum account.

But I want to point out some problems with this process:

- My **forum account** is associated with **email1**.
- I have an **Ubuntu One account** associated with **email2**.
- I also have a Launchpad account associated with email1 (same email as the forum account).

I followed the instructions and logged into my Ubuntu One account (email2). I tried to add email1 to that account, but got an error message saying that the email1 is already associated with an account. I discovered that email1 is associated by default with a Ubuntu One account that I never created.

I logged with that Ubuntu One account (email1) and at first step I was asked what info I want to be passed to Ubuntu Forums (or something like that). There were 3 items with check boxes:
- the name given as real name
- "user name" (with check box marked and **greyed out**)
- e-mail address (email1 in this case)

The problem is that "user name" was the name from email1 (characters before "@" from email1), not the user name from this forum (Seb71). So it would appear that after completing the login process I would have another forum user name. Fortunately it was not the case, otherwise you would have yet another topic in the "Resolution Centre".

I would preferred to keep the old way to login and just get a password reset at first login after the forums breach. Then, if really necessary, transition to SSO login at a later date, after warning forum users about the implications.

---

### Post by 7R6Kh6w on 2013-07-31
...hi, don't know where to post my request...my former sign-in name is byStanderone and it's gone..lol. tried to open new mail acct with tht name yet it won;t appear in the forums....is there any chance tht i may secure my former name? i don't mind the bean count, should it be lost. thanks.

---

### Post by Seb71 on 2013-07-31
> **7R6Kh6w said:**
> ...hi, don't know where to post my request...my former sign-in name is byStanderone and it's gone..lol. tried to open new mail acct with tht name yet it won;t appear in the forums....is there any chance tht i may secure my former name? i don't mind the bean count, should it be lost. thanks.

Make a new thread [here]("http://ubuntuforums.org/forumdisplay.php?f=123").

---

### Post by volkswagner on 2013-07-31
Yay,  

I'm back.

One thing I did wrong.  I had an UbuntuOne account but my email was not the same as the email
I used to sign up on the forums.  I mistakenly logged into UbuntuOne then added the email address
associated with my forum ID.  Even after setting this email as primary, the accounts still did not sync.

I logged out of forums, changed UbuntuOne primary email back, and deleted the email that was tied
to my forum ID.

Then I created a new UbuntuOne account using my email address that was tied to my forum ID.

All is good!

---

### Post by Newbunto on 2013-07-31
> **deadflowr said:**
> The only person who can get you your old password is the hacker

That might be worth a shot too. :)

> , as Canonical IS overwrote all passwords and randomised them.

Maybe they did a backup first. I would.

---

### Post by Newbunto on 2013-07-31
> **Seb71 said:**
> just get a password reset at first login after the forums breach.

That isn't completely adequate by itself because if the hacker has managed to get the password from the MD5 hash then the first login after the breach could be the hacker. So at the very least it would have to be a mandatory password change i.e. no login until changed and it would have to involve confirmation via the email address.

Even that would be broken if someone is silly enough to use the same password as is used to access the mailbox associated with the email address associated with login. Noone would be that silly, would they?

---

### Post by Seb71 on 2013-07-31
> **Newbunto said:**
> So at the very least it would have to be a mandatory password change i.e. no login until changed and it would have to involve confirmation via the email address.

That is what I had in mind: a mandatory password change, with confirmation by e-mail (so when you first try to login, you would automatically get a one-time password via e-mail and only be able to login with that one-time password; after that, change the password as you wish).

If e-mail is also compromised, the SSO would not solve anything.

---

### Post by 7R6Kh6w on 2013-07-31
...as the heat about this login issue progress...am coming to a conclusion tht this whole thing is a 'BIG'...hoax...just to give way for the process of merging ubuntuone and whatever else they are merging....come on peiople, we were not born yesterday. being an ubuntu user since 2007, this is unbelievable!

---

### Post by mohan-ram on 2013-07-31
Mine didn't link. :(

---

### Post by sandyd on 2013-07-31
> **mohan-ram said:**
> Mine didn't link. :(

Please post [here]("http://ubuntuforums.org/forumdisplay.php?f=123") with your original username

---

### Post by stebbins2 on 2013-07-31
My $0.02 about this change.

Users make mistakes, like signing on from an unknown insecure machine.  So no matter how secure the password database is, some percentage of users are going to be hacked.  Encouraging users to use credentials to an account that has sensitive personal information in order to perform everyday non-sensitive business is going to magnify the severity of the consequences when they are hacked.

So my recommendation for most folks that already has a Ubuntu One account would be to *not* use it for forum access.  **Create a new account that has as little personal information as possible!**

Personally, I came very close to turning my back and walking away from Ubuntu.  I'm still wavering a bit.  I'm only here to support users of my OSS project.  You are on the verge of chasing me away.

---

### Post by CitadelUniversal on 2013-07-31
Why is my account name different on Ubuntu One, it is registering a different username - I did email Ubuntu One support and this was their response: 

"In the case of ubuntuforums, what you should do is to set your preferred email address on Ubuntu SSO to the same email address you used to register there. If you already signed in with the wrong email address, now you need to contact the forum admins to clear your OpenId association. They explain the use of Ubuntu SSO here: [http://ubuntuforums.org/showthread.php?t=2164051](http://ubuntuforums.org/showthread.php?t=2164051) There you will find some other people with your same problem, and there you can ask the forum admins to help you."

The Ubuntu One account should only display "CitadelUniversal" and not someone elses - I even don't know why the other account has my email address on it please explain this problem......

---

### Post by malspa on 2013-07-31
I didn't realize I had a Ubuntu One account. I think it was from back when I was using ShipIt or something.

---

### Post by kansasnoob on 2013-07-31
> **7R6Kh6w said:**
> ...as the heat about this login issue progress...am coming to a conclusion tht this whole thing is a 'BIG'...hoax...just to give way for the process of merging ubuntuone and whatever else they are merging....come on peiople, we were not born yesterday. being an ubuntu user since 2007, this is unbelievable!

I'm quite comfortable saying there is no conspiracy here :)

I've used Ubuntu's SSO (single sign on) for quite some time and it was NOT breached during this hacking episode. I've also not yet synced with Ubuntu One, not because I don't trust it but I just don't need it.

I've used SSO with the QA Tracker and Launchpad for quite some time w/o a problem so I think this is a wise move.

I truly believe that a great deal of the problems people are encountering are related to simply not being patient when presented with SSO's warning about waiting for 15 minutes when they initially edit their profile :)

I wish I'd taken a screenshot when I did mine, but it clearly said to wait at least 15 minutes when it first failed. I was busy anyway so I waited about 2 hours, then there it was :guitar:

---

### Post by kansasnoob on 2013-07-31
> **malspa said:**
> I didn't realize I had a Ubuntu One account. I think it was from back when I was using ShipIt or something.

I've never used Ubuntu One but I was prompted to create an SSO (single sign on) acct to manage my QA Tracker and Launchpad accts a long time ago.

I sort of wonder if many of these ongoing problems couldn't be resolved by changing the wording about creating or editing a SSO acct/password.

Maybe link the full meal deal:

[https://help.ubuntu.com/community/SingleSignOn](https://help.ubuntu.com/community/SingleSignOn)

Sometimes abbreviations can be confusing or lead to incorrect assumptions :(

Maybe warn that it will take at least 15 minutes for the updated info to sync? Darn I wish I'd taken a screenshot of that :(

---

### Post by malspa on 2013-07-31
I'm actually quite shocked that I managed to get through it and get to my original forum account with everything intact, and not as "malspa2" or anything weird like that. I was trying to follow the instructions but I didn't feel like I knew what I was doing. Clear as mud, seemed to me. Oh, well, glad to be back.

---

### Post by kansasnoob on 2013-07-31
> **stebbins2 said:**
> My $0.02 about this change.

Users make mistakes, like signing on from an unknown insecure machine.  So no matter how secure the password database is, some percentage of users are going to be hacked.  Encouraging users to use credentials to an account that has sensitive personal information in order to perform everyday non-sensitive business is going to magnify the severity of the consequences when they are hacked.

So my recommendation for most folks that already has a Ubuntu One account would be to *not* use it for forum access.  **Create a new account that has as little personal information as possible!**

Personally, I came very close to turning my back and walking away from Ubuntu.  I'm still wavering a bit.  I'm only here to support users of my OSS project.  You are on the verge of chasing me away.

I understand your concern, but I've sometimes had to use public computers in hotels or libraries to access my bank account :shock:

How scary is that compared to this?

---

### Post by stebbins2 on 2013-07-31
> **kansasnoob said:**
> I understand your concern, but I've sometimes had to use public computers in hotels or libraries to access my bank account :shock:

How scary is that compared to this?

Both are risky behavior not to be engaged in lightly.  The difference is that I'll bet you gave it some thought and weighed the risks as compared to your immediate needs when you accessed your bank account from a public computer.  I'm hoping you don't make a habit of this and only do so in dire need.  In the case of forum access, you should not have to make such judgement calls that have such serious consequences.  The forum should be more easily accessible with very little risk to yourself if a breach occurs. The worst that should happen is someone uses your forum credentials to impersonate you on the forum.  But if you used an Ubutnu One account that is linked to a credit card and other personal data, they could do much worse.

---

### Post by kansasnoob on 2013-07-31
> **stebbins2 said:**
> Both are risky behavior not to be engaged in lightly.  The difference is that I'll bet you gave it some thought and weighed the risks as compared to your immediate needs when you accessed your bank account from a public computer.  I'm hoping you don't make a habit of this and only do so in dire need.  In the case of forum access, you should not have to make such judgement calls that have such serious consequences.  The forum should be more easily accessible with very little risk to yourself if a breach occurs. The worst that should happen is someone uses your forum credentials to impersonate you on the forum.  But if you used an Ubutnu One account that is linked to a credit card and other personal data, they could do much worse.

Of course I'm always as cautious as possible. Are you aware of anyones SSO account being hacked?

---

### Post by Andrew_P on 2013-07-31
It's strange that a number of users have random-character user names.  Other than the forum appearance having changed since the last time logged in, my username and avatar appear as before, as well as my posting history.  I just followed the instructions and logged in via Ubuntu One SSO and it appears to have worked as designed.

---

### Post by stebbins2 on 2013-07-31
> **kansasnoob said:**
> Of course I'm always as cautious as possible. Are you aware of anyones SSO account being hacked?
There would be no way for me to know of such an event unless it were publicly announced or I had some personal contact with the unfortunate individual.

---

### Post by d0p3y2k4 on 2013-07-31
[B]All users, please note:


[LIST]
[*]When you login the first time using Ubuntu One, your forum account is associated with your Ubuntu OpenID account. Subsequent changes to details in your Ubuntu One account will have no effect on your forum account - they will remain associated.
[/LIST]



well that must be a bug. because it now says i am new user when i joined long time ago & my name was -jay- when i used the same email to log into

[/B]

---

### Post by coffeecat on 2013-07-31
> **d0p3y2k4 said:**
> 
well that must be a bug. because it now says i am new user when i joined long time ago & my name was -jay- when i used the same email to log into


It is not a bug and the part you quoted is correct. The -jay- account has a different registered email address from the preferred email you had set in your Ubuntu One account. That is why the system made a new account for you.

Please post in the [Resolution Centre]("http://ubuntuforums.org/forumdisplay.php?f=123") and an admin will deal with this and sort you out. It is quite impossible to give individual attention in a long thread like this.

@everyone, if you need your account sorting out, please post in the Resolution Centre. If you want to chatter please find somewhere else. This thread was intended for people to pose general questions so that we could refine the OP. There is too much background noise in this thread for it be useful as it stands. Tomorrow I shall prune out all the off-topic chatter and individual requests.

---

### Post by imnichol on 2013-07-31
So do I need to change my password now that my forums account is linked with SSO?

---

### Post by rattskjelke on 2013-07-31
I never had a Ubuntu One account until I had to create one the other day to get back on the forums.
The way I understand it, your Ubuntu One account is used to log into the forums.
If you go to your forum profile settings there is still a place where you can change your email and password.
Does that do anything now since you log in with Ubuntu One? What happens if you try to change your email or password there?

---

### Post by FWIW on 2013-07-31
> **Newbunto said:**
> 

It goes without saying that you should just **never ever** do this.

If you think that any of your passwords is strong enough to survive MD5 brute forcing then you can take a punt and not change that password.

But you see, there's the rub.  A different password for each and every on-line service is quite unmanageable.  I know there are password handling tools available and so on, but that means you are tied to that password handler and cannot use some other computer to access anything unless you also know the passwords that are managed.  So I use a selection of different passwords across my on-line services.  The key thing here is my previous and only use of this forum was so long ago that I may well have used a different password (that I commonly used for other similar forums etc at that time) or I may not.  I simply have no memory.

The big issue is that across all my current on-line stuff, I have to change all my passwords regardless of what they currently are, because I have no way of knowing which may be the same as my old ubuntuforums password.  OK, there are a few that I won't have to change because they are definitely different, but you get the idea.

---

### Post by Yellow Pasque on 2013-08-01
> **ofnuts said:**
> Now the very down-to-earth and practical question: in the former life of Ubuntu forum, I could have a bookmark on [http://ubuntuforums.org/usercp.php](http://ubuntuforums.org/usercp.php) and the userid and password kept by Firefox so checking out new stuff on UF was a one click operation. Now it takes me through several pages and leaves me in UF home. So what can I do to get back to the original?

Yeah, that's my biggest complaint. I have to go through multiple pages to log in every time, when I used to be able to go directly to my subscriptions. I kind of doubt we'll get back to the fast login...

---

### Post by cariboo on 2013-08-01
Your browser still saves your SSO details, so it's just a matter of clicking the log in button, waiting for it to continue to the SSO login page, and your done, if I remember correctly, probably 3 clicks.

The reason we went to SSO login, is that the vBulletin way of storing passwords was totally inadequate, Canonical IS is actually working with the vBulletin team to hopefully fix the problem, so what happened to us, doesn't happen on other vBulletin forums

---

### Post by Quepali on 2013-08-01
Ehm... What was the password I was using on the old login, then? I have several passwords that I am reusing on different sites, and I am not 100% sure which one i used here. If I change all my passwords I am risking changing it to the one that I had here... Suggestions on how to handle this situation?

---

### Post by coffeecat on 2013-08-01
> **imnichol said:**
> So do I need to change my password now that my forums account is linked with SSO?

> **rattskjelke said:**
> I never had a Ubuntu One account until I had to create one the other day to get back on the forums.
The way I understand it, your Ubuntu One account is used to log into the forums.
If you go to your forum profile settings there is still a place where you can change your email and password.
Does that do anything now since you log in with Ubuntu One? What happens if you try to change your email or password there?

I'll add things to the OP to answer this when I prune this thread in a few hours, but in the meantime...

The forum (vbulletin) password is now an irrelevance. The only password you need to be concerned about as far as the forum is concerned is your Ubuntu One login password. All forum passwords were replaced by random ones shortly after the forum was taken down after the attack as a preliminary measure. The only reason the password fields are still visible in the change email option in the forum is that admins and moderators still need the ability to change their forum password for a legacy operation. This is being worked on by Canonical sysadmins and soon this too will become an irrelevance and hopefully then the reference to password can be removed from the change email page. In the meantime, sorry about the confusion the presence of password fields there creates.

As far as changing emails is concerned, I'll edit/amend the OP in due course to make this clearer:

Association between an Ubuntu One account and a forum account occurs as a one-time operation on first login when the openID login code finds a match for the Ubuntu One preferred email in the forum database. Or, if it does not find a match, then a new forum account is created. Once the association has been made, the two accounts are locked together and can only be disassociated by a forum admin. This means that once the two accounts are associated, you can change the email in either or both accounts and the association will stick. You can also change usernames in either and the association will still stick, although changing the username in the forum account can only be done by an admin and we place restrictions on this to prevent frivolous and repeated changes.

---

### Post by ofnuts on 2013-08-01
> **cariboo907 said:**
> Your browser still saves your SSO details, so it's just a matter of clicking the log in button, waiting for it to continue to the SSO login page, and your done, if I remember correctly, probably 3 clicks.

Actually four clicks instead of one:

**Before:**

[LIST=1]
[*]Click on a UbuntuForums bookmark that takes me to my settings page
[/LIST]
[B]
Now:[/B]

[LIST=1]
[*]Click on a UbuntuForums bookmark that would have taken me to my settings page
[*]Reach a page saying "Login has changed. Please read BEFORE logging in!". Hunt for "Login with SSO" and click
[*]Reach a page saying "Personal Data Request". Click "Yes log me in"
[*]Reach UbuntuForums home page. Hunt for "Settings" and click
[/LIST]

So that's 3 more clicks; including two hunting for things that are in the corners... 


[LIST]
[*]Page 2) is totally unecessary for people with cookies from login.unbuntu.org. They already know.
[*]Page 3) why? Any use case where someone connect to login.ubuntu.com with cookies and doesn't want to login?
[*]Page 4) The original target URL could be forwarded so that login redirects to it.
[/LIST]

---

### Post by dag-ringdal on 2013-08-01
I try to choose the preffered e-mail adress, but when I type in (under manage e-mail adresses) I get a message saying the adress I'm trying to attach to the account, allready is associated with the account. But I cannot chose this adress as preferred. What do I do wrong?

---

### Post by vasa1 on 2013-08-01
The login procedure has to be done once per browser session. More clicks than before but not at all a big deal. I can live with it.

---

### Post by G@Tenerife on 2013-08-01
Hello, I just discovered after having logged out of the forum, my SSO account still is logged in. After having logged out from the forum I also should be logged out from my SSO account.

---

### Post by watgrad2 on 2013-08-01
Hi - instead of Ubuntu One linking to my original Forums account I have been given a new account. (I'm now watgrad2, used to be watgrad)
Ubuntu One uses a different email address that what I used to use here...is there a way to link my old account?

---

### Post by turftech on 2013-08-01
Oh well. I lost everything, including my username. I have never really used Ubuntu One as I have always found the idea of "the cloud" anathema to security, but am now forced to sign in to a service I do not use nor ever will. Looks to me like fixing a problem by adding more of the same. A classic bureaucratic response to an attack.

---

### Post by versvs2 on 2013-08-01
You're totally right, and not to mention the inhability to merge your account if you happen to not remember which one of the 2 e-mails you have with Ubuntu SSO where the one you used in the forum, which is my case.

So I have an account registered back in 2005 ( [http://ubuntuforums.org/member.php?u=33450](http://ubuntuforums.org/member.php?u=33450) ) and i cannot access it, instead I'm here as a newly registered user, with 0 posts and a few minutes old.


Really, this is a mess: not only the forums got hacked and taken offline for a long time, but the solution they provide now is a real headache.


Edit: i was trying to reply to [http://ubuntuforums.org/showthread.php?t=2164051&p=12738961#post12738961](http://ubuntuforums.org/showthread.php?t=2164051&p=12738961#post12738961)



BTW, The forum software now believes at any time that i'm editing a reply, though I havnt touched the form. I found this misbehaviour of the forum disturbing.

---

### Post by QIII on 2013-08-01
For those of you who believe you have lost your original accounts, you have not.  Please note that I have not.  I simply matched my Ubuntu One preferred email with my UF account's email when first logging in.

Please start a new thread in the Resolution Centre and provide the Admins with your original account name and they will help you properly associate your original account with your Ubuntu One login.

If you do not remember your original UF email, the Admins will help you with that.

---

### Post by Ronald_P._Ouellette on 2013-08-01
Same mistake others made. Added my old email account to UbuntuOne, but setting it as the "preferred" email failed. After logging into the forums, I now have a new account. And I am locked out of settings changes due to the 25 post rule. One problem with this is that this new account uses my full name (not good) rather than my old forum screen name.

I put in a request in the resolution center to link to my old forums account, but realized that though I might get my profile back (user since 2008 and bean count etc.), I will still have my full name as a screen name.

Can I resolve this by closing my UbuntuOne account completely then creating a new account with my old email address? At this point, I am afraid to do anything.

---

### Post by coffeecat on 2013-08-01
@Ronald_P._Ouellette, I have addressed your concerns in your Resolution Centre thread. I can sort this all out for you so there is no need to ask the same again in this thread.

And a reminder to everyone - something that has been said before.

[SIZE=3]**Please do not post questions about individual accounts in this thread - they will be lost in the background noise. The place to get an admin to help you deal with issues for individual forum accounts is in the Resolution Centre.** [/SIZE]

---

### Post by Hexxus on 2013-08-01
While I do not know the intimates of their setup, our organization has had experience with SSO's and they do/can work very well when properly thought out. I think that it is a nice move to see and hope for the best. 

Nice job developers and admins that got this thing changed over with the sso, retained user data and help patch (im guessing) a zero-day bug in the forums.

---

### Post by G@Tenerife on 2013-08-01
> **dag-ringdal said:**
> I try to choose the preffered e-mail adress, but when I type in (under manage e-mail adresses) I get a message saying the adress I'm trying to attach to the account, allready is associated with the account. But I cannot chose this adress as preferred. What do I do wrong?

It Looks Like you use this email address already. Check your SSO  account. Maybe you will have to change your password temporary  according to the password used to log into the forum. Once you have logged in once you can go back to your old SSO password.

---

### Post by Gavin77 on 2013-08-01
Sorry if this has been asked already as I haven't gone through all 9 pages but how can I stay logged into the forums now?  I've got cookies enabled for both ubuntuforums.org and ubuntu.com but when I close my browser and come back I need to log in again.  I never had any problems staying signed in before.

Using latest Firefox 23 beta if that's relevent.

---

### Post by Yellow Pasque on 2013-08-01
> **Gavin77 said:**
> Sorry if this has been asked already as I haven't gone through all 9 pages but how can I stay logged into the forums now?  I've got cookies enabled for both ubuntuforums.org and ubuntu.com but when I close my browser and come back I need to log in again.

You can't stay logged in :\ (though some have said they can work around it by editing the expiration date on the cookies).

---

### Post by ventrical on 2013-08-01
> **Temüjin said:**
> You can't stay logged in :\ (though some have said they can work around it by editing the expiration date on the cookies).

This appears to be somewhat fixed. You can close a tab, reopen it and go to ubuntuforums without SSO log on. Also , it does not bump you anymore after a few minutes of inactivity.

---

### Post by Elfy on 2013-08-01
> **turftech said:**
> Oh well. I lost everything, including my username. I have never really used Ubuntu One as I have always found the idea of "the cloud" anathema to security, but am now forced to sign in to a service I do not use nor ever will. Looks to me like fixing a problem by adding more of the same. A classic bureaucratic response to an attack.

guess what - I don't use the cloud either

Ubuntu One is now the name for the SSO thingy - not the cloud thing

[http://fridge.ubuntu.com/2013/06/21/improving-web-services-for-ubuntu/](http://fridge.ubuntu.com/2013/06/21/improving-web-services-for-ubuntu/)

---

### Post by Newbunto on 2013-08-01
> **FWIW said:**
> I know there are password handling tools available and so on, but that means you cannot use some other computer to access anything unless you also know the passwords that are managed.

Some such tools allow remote (e.g. client-server) access. You have to balance convenience v. security with that option though. An alternative would be to remote in to where you can run the tool. Again, convenience v. security.

My choice is never to duplicate passwords across multiple contexts. So I am 100% sure that my likely compromised password here is not being used by me anywhere else. My choice then is to manage a *lot* of passwords.

> I have to change all my passwords regardless of what they currently are

With the choices that you have made, yes. So how are you going with changing almost all of your online passwords? :-(

---

### Post by Ron O on 2013-08-02
The resolution center untangled my duplicate accounts and restored my original forum profile pretty quickly by going to this url  [http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)  and just politely asking for help. Pretty impressive considering the number of people having problems with this!

Just tell them your email address, your old email address, and the screen name you had in the forums before this problem began with the security breach.

---

### Post by deadflowr on 2013-08-02
> **Elfy said:**
> guess what - I don't use the cloud either

Ubuntu One is now the name for the SSO thingy - not the cloud thing

[http://fridge.ubuntu.com/2013/06/21/improving-web-services-for-ubuntu/](http://fridge.ubuntu.com/2013/06/21/improving-web-services-for-ubuntu/)

So what's the cloud thingy called now?

---

### Post by bluemeda on 2013-08-02
okey, my account has been recovered, thanks

---

### Post by spider623 on 2013-08-02
Thanks you are life savers, i hate calculating now passwords, @[[COLOR=#000000]hLtbPDh[/COLOR]]("http://ubuntuforums.org/member.php?u=1841215")[COLOR=#000000] what [/COLOR]@[COLOR=#990303]**_coffeecat_**[/COLOR]&#8203; said[COLOR=#990303]**__**[/COLOR][COLOR=#990303]**__**[/COLOR]

---

### Post by rankokohime on 2013-08-02
> **thefluffyone2 said:**
> My previous account was "TheFluffyOne". I don't have a huge post count, but I like to keep the same username on various forums.

So I have set my Ubuntu One preferred email to the same as my old forum email address and it doesn't seem to have linked to the old account. I am now "thefluffyone2"... something isn't working right here :(
Having the same problem here.  My previous UF account was "Ranko Kohime", with the space, and I used the same e-mail for both SSO and UF, though they were not linked before the hack.

ETA: just read the rest of the thread, heading to the Resolution Center now.  :)

---

### Post by Invincible23 on 2013-08-02
Mine works perfectly after i registered for a SSO account with the same username i had earlier, got a new email for verification purpose and here i'm back to postin :)

---

### Post by cariboo on 2013-08-02
> **FWIW said:**
> Hmm.  I find this conclusion to the wait for the forums to return to be a bit of a disappointment.  I created my account here in 2006, probably to ask a question.  Whatever the case, I haven't used it since.  Then last week I get the e-mail advising of the hack.  But here's the thing.  I don't know what password I was using on here back then.  There is some chance that it is the same as some of my current passwords for various online accounts and such.  I had kind of naively hoped that when the forums came back I could try to log in using my e-mail address and most likely password (and failing that one of several other possible passwords), which would have told me whether I needed to go changing any of my passwords elsewhere.  Now I have little option but to spend a lot of time going around the whole lot and changing all of them.  That's not going to be fun.  I wish there was an alternative.

Even before the hack, there was no way to check your password other that logging. The password never showed up anywhere on the forum.

---

### Post by HousieMousie2 on 2013-08-02
For the record...
Ubuntu One's descriptions, explanations of what they want and what you are giving them (where it will be used and how) are very lacking.
Not a good impression especially since I already held a bit of a grudge against it for its intrusive nature after upgrading to the LTS.

Anyway, all's well that ends well... I just don't envy those who have yet to deal with Ubuntu One.

Just happy the forums are back!  :D

---

### Post by Elfy on 2013-08-02
> **deadflowr said:**
> So what's the cloud thingy called now?

I don't use it. Have absolutely no interest in it - I've no idea I'm afraid.

---

### Post by quequotion2 on 2013-08-02
Is there a way to find out what e-mail address my original account is using?

Actually I think it was the same as my SSO, and as you can see here:

[IMG]http://i.imgur.com/704MRPN.png[/IMG]

1. correct name
2. correct username
3. correct e-mail

why am I quequotion2 ?

If it's the only way, I wouldn't mind quequotion being deleted so long as I don't have to use a number with my username. I like quequotion. Bugmenot gave me this name before it died.

*update*

Ubuntu SSO tells me my username is quequotion at every login. I've tried all of the other addresses I might have registered under and none synced with the original quequotion.

Something is wrong here.

---

### Post by vasa1 on 2013-08-02
> **coffeecat said:**
> .... I can sort this all out for you so there is no need to ask the same again in this thread.

And a reminder to everyone - something that has been said before.

[SIZE=3]**Please do not post questions about individual accounts in this thread - they will be lost in the background noise. The place to get an admin to help you deal with issues for individual forum accounts is in the Resolution Centre.** [/SIZE]

Looks like this needs to be repeated :)

---

### Post by cariboo on 2013-08-02
@quequotion2, we block bugmenot accounts :-P. You should have received an email about the attack, check your spam folder to see if it was there, and use the email address that message was sent to.

---

### Post by Babin_Lonston on 2013-08-03
Wow my account was still live , Thanks .........

---

### Post by Soul-Sing on 2013-08-03
I found the information from this forum how to restore things cristall clear. SSO is better indeed.

---

### Post by PaulW2U on 2013-08-03
> **Soul-Sing said:**
> I found the information from this forum how to restore things cristall clear. SSO is better indeed.

I had no problems at all but after reading some of the requests for help in the Resolution Center I think it's very obvious that many of us don't keep a record of what email address we have registered at the various websites that we use. This has led to many "new" accounts being created. 

After one of my email addresses, which was only used to register at forums, was stolen from another forum database a couple of years ago I decided to keep a record of every email address, username and password that I have set-up. After nearly 20 years on the internet I have over 150 on-line accounts although most are no longer used. There's probably a few that I've forgotten about as well. :(

If one of those 'forgotten' sites were to email me and tell me that their database had been hacked then I too would be unable to regain access to my account without a certain amount of guessing what my email address or user-name was. And some of the email addresses that I used all those years ago haven't been  accessible for many years now. ](*,)

So yes, Ubuntu SSO does help manage those important details that I need to remember for some of the Ubuntu related sites that I regularly visit.

---

### Post by wildman424 on 2013-08-03
test test .....

This is the first time I've logged into Ubuntu Forum since the breach. Is my account now considered secured since I had to create an Ubuntu One account with a completely different password to log into the forum. Are there any other steps I need to take to secure my account?

---

### Post by critin on 2013-08-03
**Before:**

1. Before:  click on forum bookmark that takes me to forum.
2. Type name or click. (My name was saved to auto enter, 
3. Enter password by typing it. 

**Now:**

1. Click on bookmark.
2. Click on login button.
3. click on Yes, Log Me In (without entering name or password)

Pretty handy!  No more forgotten passwords or typos.

---

### Post by Irihapeti on 2013-08-03
> **wildman424 said:**
> test test .....

This is the first time I've logged into Ubuntu Forum since the breach. Is my account now considered secured since I had to create an Ubuntu One account with a completely different password to log into the forum. Are there any other steps I need to take to secure my account?

Welcome back!

You should be fine as you are, as long as you have a reasonable password on your SSO login and your preferred email account, of course.

---

### Post by wildman424 on 2013-08-03
> **Irihapeti said:**
> Welcome back!

You should be fine as you are, as long as you have a reasonable password on your SSO login and your preferred email account, of course.

Thanks Irihapeti, Glad to be back  :)

---

### Post by mattcen2 on 2013-08-04
Um. Oops. So apparently I picked the wrong "Primary Email Address" when signing in, so now have 2 accounts, the old one 'mattcen' now being inaccessible I think, even having tried setting the *correct* primary email address. Is there any way to clean this up so that, at the very least, I can get my old username back? I don't particularly care about the posts etc. associated with the old account if that makes it any easier.

---

### Post by deadflowr on 2013-08-04
> **mattcen2 said:**
> Um. Oops. So apparently I picked the wrong "Primary Email Address" when signing in, so now have 2 accounts, the old one 'mattcen' now being inaccessible I think, even having tried setting the *correct* primary email address. Is there any way to clean this up so that, at the very least, I can get my old username back? I don't particularly care about the posts etc. associated with the old account if that makes it any easier.

Read post number one in this thread.

---

### Post by Elfy on 2013-08-04
> **mattcen2 said:**
> Um. Oops. So apparently I picked the wrong "Primary Email Address" when signing in, so now have 2 accounts, the old one 'mattcen' now being inaccessible I think, even having tried setting the *correct* primary email address. Is there any way to clean this up so that, at the very least, I can get my old username back? I don't particularly care about the posts etc. associated with the old account if that makes it any easier.

As deadflowr says ... read the first post.

Your issue WILL be ignored in this thread.

Thanks :)

---

### Post by martinr on 2013-08-04
Some remarks about degraded usability:

**Thread location Lost**
When I'm not logged in whilst reading a thread and I click on reply in the thread, then I'm sent to an explanation page that says I should log into UbuntuOne. So I click on log in and jump through all the hoops, but then I arrive at a [general Ubuntu Forums page]("http://ubuntuforums.org/") and am never taken back to my reply on the thread. Not only the location in the tread is lost but the whole thread entirely. This is very inconvenient. Could this be fixed so that one returns to the reply field on the thread one was reading?

**Implement Client Certificate login**
At the UbuntuOne account I was not able to select the same username as I have on Ubuntu Forums. So I needed to select a crummy one. Also the security demands at Ubuntu One are higher and you have to log in with a complete email address. Entering a long crummy email address and high security password is a hassle and interrupts my train of thought thoroughly. I actually have to look it up (and am about to write them down on a post-it). A solution for this would be to make certificate login possible for UbuntuOne. Could x509 client certificate login be added as a login method for UbuntuOne SSO to prevent the hassle with high security passwords and full email addresses?

**Single Sign Out**
If I log out at the forums I'm still logged in at UbuntuOne, although I have no window open any more at UbuntuOne. Anybody that high-jacks that session can do real harm, for it allows them to log into Ubuntu Forums again, Launchpad and UbuntuOne and all other systems it gives access to. This seems as a vector of attach to me. Please implement single sing-out as well.

---

### Post by ibjsb4 on 2013-08-04
I really liked staying logged in 24/7.  Seems with the new login there is now a timeout.

---

### Post by quequotion2 on 2013-08-04
> **cariboo907 said:**
> @quequotion2, we block bugmenot accounts :-P. You should have received an email about the attack, check your spam folder to see if it was there, and use the email address that message was sent to.
It's possible I registered my account before the block was in place. I was using the bugmenot account for everything at the time. I have recieved no message to any address I know of; the news was a surpise to me when I came to review the boards one day.

Is it possible to remove quequotion and rename me quequotion? I'd rather not lose the content of my threads but I don't really mind if it means having my original screenname.

---

### Post by quequotion2 on 2013-08-04
Would it be possible to put up a cached version of the old forum, read only of course, that we could log into to solve these mysteries for ourselves?

---

### Post by Elfy on 2013-08-04
> **quequotion2 said:**
> It's possible I registered my account before the block was in place. I was using the bugmenot account for everything at the time. I have recieved no message to any address I know of; the news was a surpise to me when I came to review the boards one day.

Is it possible to remove quequotion and rename me quequotion? I'd rather not lose the content of my threads but I don't really mind if it means having my original screenname.

Can you post in RC please - we'll deal with it then as soon as we can.

There are parts of your profile hidden that you will know and that we can see :)

---

### Post by spellbinder2 on 2013-08-05
I've been on this forum since 2006, I believe. But now my username is spellbinder2 (I was Uncle Spellbinder). I can't modify my profile, change avatars, until hit 25 posts???  I hit 25 posts YEARS AGO! 

How do I retrieve my original username? I want my Ubuntu Forums identity back. Is it gone forever????????

---

### Post by Elfy on 2013-08-05
> **spellbinder2 said:**
> I've been on this forum since 2006, I believe. But now my username is spellbinder2 (I was Uncle Spellbinder). I can't modify my profile, change avatars, until hit 25 posts???  I hit 25 posts YEARS AGO! 

How do I retrieve my original username? I want my Ubuntu Forums identity back. Is it gone forever????????

calm down - post in RC and please read the RC sticky re this issue - thanks

---

### Post by spellbinder2 on 2013-08-05
> **Elfy said:**
> calm down - post in RC and please read the RC sticky re this issue - thanks

OK. Sorry 'bout that. And at the risk of sounding stupid here, What is RC?

Also, I just responded to you PM. Thanks.

---

### Post by Elfy on 2013-08-05
resolution centre - [http://ubuntuforums.org/forumdisplay.php?f=123](http://ubuntuforums.org/forumdisplay.php?f=123)

I replied ;)

don't worry about the sticky - we've got past that :)

---

### Post by spellbinder2 on 2013-08-05
Thanks, Elfy!

---

### Post by Uncle Spellbinder on 2013-08-05
YES! Thank you Elfy!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Valene_Reynolds on 2013-08-05
hi everyone, I am a 15 year old female from over in cyanogenmod nook color. What happened with the forums here? Its changed in the log in screen and uses that ubuntu one now.

---

### Post by deadflowr on 2013-08-05
Look over these two threads
[http://ubuntuforums.org/showthread.php?t=2164064](http://ubuntuforums.org/showthread.php?t=2164064)
and
[http://ubuntuforums.org/showthread.php?t=2164051](http://ubuntuforums.org/showthread.php?t=2164051)

also, look in the [forums feedback & help]("http://ubuntuforums.org/forumdisplay.php?f=48") sub-section for extra info regarding site problems found and other known issues.

---

### Post by oldos2er on 2013-08-05
> **Valene_Reynolds said:**
> hi everyone, I am a 15 year old female from over in cyanogenmod nook color. What happened with the forums here? Its changed in the log in screen and uses that ubuntu one now.

Merged with SSO login megathread.

---

### Post by FWIW on 2013-08-06
> **cariboo907 said:**
> Even before the hack, there was no way to check your password other that logging. The password never showed up anywhere on the forum.

Yeah there was.  Attempt to log in with any and all passwords that it could have been.  The password that lets you log in is the right one!  And if I couldn't get in....then no problem.  If I can't use one that I'm currently using, then it's gone for good.

---

### Post by FWIW on 2013-08-06
> **Newbunto said:**
> 
With the choices that you have made, yes. So how are you going with changing almost all of your online passwords? :-(

Not well.  Hard to find the time to sit down and work through the list (generate the list first!) and document.

---

### Post by santosh83 on 2013-08-27
Hi everyone,

First post after the Ubuntu forums hack. Reading all the posts I feel lucky that the first login and association with Ubuntu One apparently went smoothly for me. I'd registered for a Ubuntu One account a year back to try out the cloud service, and luckily I use the same email address across all sites and logins, so the OpenID association process seems to have gone as promised in the instructions. Since I don't use Ubuntu One for any important file storage, nor have financial details associated with it, I don't have to fear my Ubuntu One credentials somehow getting compromised because of having to login from Ubuntu forums, but understand the worry of those that do have sensitive information in their Ubuntu One account.

Sadly though I never got any mail from the forums warning me about the breach, but stumbled on the news (since I don't login to forums regularly) through a slashdot article, so that part (immediately warning all users) could've been handled better. Rather stupidly I'd used the same password for a bunch of other sites, so it was lucky I stumbled on that slashdot article. Immediately changed all my passwords to be unique.

---

### Post by cariboo on 2013-08-27
> **santosh83 said:**
> Hi everyone,

First post after the Ubuntu forums hack. Reading all the posts I feel lucky that the first login and association with Ubuntu One apparently went smoothly for me. I'd registered for a Ubuntu One account a year back to try out the cloud service, and luckily I use the same email address across all sites and logins, so the OpenID association process seems to have gone as promised in the instructions. Since I don't use Ubuntu One for any important file storage, nor have financial details associated with it, I don't have to fear my Ubuntu One credentials somehow getting compromised because of having to login from Ubuntu forums, but understand the worry of those that do have sensitive information in their Ubuntu One account.

Sadly though I never got any mail from the forums warning me about the breach, but stumbled on the news (since I don't login to forums regularly) through a slashdot article, so that part (immediately warning all users) could've been handled better. Rather stupidly I'd used the same password for a bunch of other sites, so it was lucky I stumbled on that slashdot article. Immediately changed all my passwords to be unique.

We found that quite a few members found the message in their spam folder, that may have happened to you.

---

### Post by santosh83 on 2013-08-27
> **cariboo907 said:**
> We found that quite a few members found the message in their spam folder, that may have happened to you.

That's certainly possible, although I do scan the spam folder for genuine mails before emptying it! Well, hope this bumpy period is soon behind us. :-)

---

### Post by DRatJr on 2013-09-09
What is with viewing a specific forum or topic, then going to log in, and it redirecting me to the "Ubuntu Forum Community" where all subforums are listed. Is there not a way to be redirected back to the topic of subforum I was already in? It isn't a huge deal, just really annoying when I'm automatically logged out, viewing a forum, want to log back in, and don't remember where the subforum/topic was. And having to hit the back button several times is annoying as well.


ALSO:
I apologize if this has been posted somewhere in this thread as of recent. I HAVE read the thread with all the information in it as well. But what is the current status of being able to be logged in indefinitely? Or is there even one other than the Ubuntu forums team looking into it? I am by NO MEANS trying to sound like a ****, just wanting to know if there is an update on it.

---

### Post by TheVakman on 2013-10-01
I like this move but I still wish it let me set a user name, I remade an account multiple times because I did not want my username to be my real name, not sure if there is a way.

---

### Post by oh_my on 2013-10-09
I've tried to register my old mail to your SSO thingie, but it just wouldn't accept it and kept saying it's an invalid email. great. Now I had to register a new account and that means I can no longer subscribe to topics, configure other settings or find my old posts because this is a "new account".
I get that you want to make things safer, but it would've been nice to keep my old account as well. "Delete all user accounts and have them make new ones" isn't really a solution. :(

Is there any way to join this account with my old account "oh my"?

---

### Post by coffeecat on 2013-10-09
> **oh_my said:**
> I've tried to register my old mail to your SSO thingie, but it just wouldn't accept it and kept saying it's an invalid email.

As the prelogin notice tells you, Ubuntu One and old forum accounts are matched on email. It sounds as though the email account used for the old forum account has been allowed to lapse. There was a reasonable expectation that people would maintain an active email account at ubuntuforums, or change the email if it became necessary.

> **oh_my said:**
> Is there any way to join this account with my old account "oh my"?

Yes. Rather than me moving your post to the appropriate place and risk you losing track of it, please post in the [Resolution Centre]("http://ubuntuforums.org/forumdisplay.php?f=123"). Please read these two stickies:

[http://ubuntuforums.org/showthread.php?t=2164369](http://ubuntuforums.org/showthread.php?t=2164369)

[http://ubuntuforums.org/showthread.php?t=2164051](http://ubuntuforums.org/showthread.php?t=2164051)

---

### Post by oh my on 2013-10-09
Ok, it turns out I was just being stupid.. Apparently I already have a  login at login.ubuntu.com from my launchpad account. I found a warning  mail about the unsuccessful login when I tried to login the first time.
I  still don't quite understand why it was saying my email was invalid  when I tried to register it. It is obviously a valid mail, since I  received an email on it. 

In any case, could you please delete  this thread: [http://ubuntuforums.org/showthread.php?t=2179633](http://ubuntuforums.org/showthread.php?t=2179633) I will  repost it from this account.

---

### Post by SeijiSensei on 2013-10-09
I would like to restate my request, made in some earlier thread about the revised login procedures, that the session cookie have a much longer expiration.  Those of us who visit the forums multiple times per day would benefit from a cookie duration of 8-10 hours.  I don't know the current duration, but I'm guessing it's only an hour or two.

---

### Post by cariboo on 2013-10-09
> **SeijiSensei said:**
> I would like to restate my request, made in some earlier thread about the revised login procedures, that the session cookie have a much longer expiration.  Those of us who visit the forums multiple times per day would benefit from a cookie duration of 8-10 hours.  I don't know the current duration, but I'm guessing it's only an hour or two.

This has been covered in several other threads,We have a ticket in with Canonical IS, as we can't do anything about it. For regular members the time out is 120 minutes.For the moderation team it is 120 minutes for the regular sub-forums, and 30 minutes for the Admin and Mod control panels.

If you think 120 minutes is to short, you should try the 30 minute time limits we have to deal with. :-(

---

### Post by stuff3 on 2013-12-08
OK guys, I haven´t been very active in the last months (or even years), but I´ve been a member of these forum since at least 2008, if not earlier. The Ubuntu One account had/has the same email adress as my forum account, still my account is not linked, I´m getting a random nick (used to be funkster & funkster1 before) and my post count is 0.
What can I do now?

---

### Post by PaulW2U on 2013-12-08
> **stuff3 said:**
> OK guys, I haven´t been very active in the last months (or even years), but I´ve been a member of these forum since at least 2008, if not earlier. The Ubuntu One account had/has the same email adress as my forum account, still my account is not linked, I´m getting a random nick (used to be funkster & funkster1 before) and my post count is 0.
What can I do now?

See - [http://ubuntuforums.org/showthread.php?t=2164369](http://ubuntuforums.org/showthread.php?t=2164369)

---

### Post by stuff3 on 2013-12-08
> **PaulW2U said:**
> See - [http://ubuntuforums.org/showthread.php?t=2164369](http://ubuntuforums.org/showthread.php?t=2164369)
Thank you, I read a lot of threads already concerning the new login method, even though I can understand security concerns, I don't like this new way of logging in.
Anyway, again, thank you for the link.

Raphael ;)

---

### Post by Elfy on 2013-12-08
> **stuff3 said:**
> Thank you, I read a lot of threads already concerning the new login method, even though I can understand security concerns, I don't like this new way of logging in.
Anyway, again, thank you for the link.

Raphael ;)

Few of us do like it - I don't like it anymore than you - that's what we've got and that's what we'll have unfortunately.

However, I'd assume that PaulW2U's thought behind posting that sticky was to point you in the right direction to get help - and I believe other threads point to the same thing - you posting a thread in the Resolution Centre.

---

### Post by stuff3 on 2013-12-08
Sorry if I posted in the wrong thread/forum section, and I mean that sincerely.

---

### Post by tfrue on 2013-12-18
I'm having troubles logging into this forum using Firefox version 26.0. I click Login With SSO, and LastPas log me in, I get the Hello messege, then it doesn't show the profile options at the top of the screen rather, the Login With SSO option. I have to use Chrome to log in to this page.

---

### Post by GraysonPeddie on 2013-12-18
Still had my old account back (and man how I was a member of Ubuntu Forums since 2008...I feel like a stranger! LOL!) and I've started to use KeePass2 as I'm unable to keep track of 100 different passwords (even variations) for 100 different accounts. This is all happened due to Ubuntu and Adobe hack.

I cannot use LastPass or any third party servers for managing my passwords as I cannot place my trust in them that my passwords are all encrypted by a master password.

Anyway, I'm happy to be back.

---

### Post by cariboo on 2013-12-19
> **chris_johnson2 said:**
> I'm having troubles logging into this forum using Firefox version 26.0. I click Login With SSO, and LastPas log me in, I get the Hello messege, then it doesn't show the profile options at the top of the screen rather, the Login With SSO option. I have to use Chrome to log in to this page.

I just tried FF 25.0. and no problem logging in. Your problem may have something to do with your profile, as before doing a fresh Trusty install, I was running into the same problem, although it was with chromium, instead of Firefox. Try creating a new Firefox profile using the following command in a terminal:

```
firefox -P
```

to see if that make a difference.

---

### Post by tfrue on 2013-12-19
> **cariboo907 said:**
> I just tried FF 25.0. and no problem logging in. Your problem may have something to do with your profile, as before doing a fresh Trusty install, I was running into the same problem, although it was with chromium, instead of Firefox. Try creating a new Firefox profile using the following command in a terminal:

```
firefox -P
```

to see if that make a difference.

Unfortunately, I'm using Window's 7. I haven't quite made the transition since I still need Win 7, but I should be getting a new desktop soon and I'm gonna wipe this baby clean, and rid this world of one more Window's evil! So, do you think I should just downgrade to 25.0?

---

### Post by coffeecat on 2013-12-19
> **chris_johnson2 said:**
> So, do you think I should just downgrade to 25.0?

I'm using FF version 26.0 in Ubuntu 13.10 and I'm not having any trouble logging in via SSO in Firefox. It might be worth trying cariboo907's suggestion to create a new FF profile.

---

### Post by tfrue on 2013-12-19
> **coffeecat said:**
> I'm using FF version 26.0 in Ubuntu 13.10 and I'm not having any trouble logging in via SSO in Firefox. It might be worth trying cariboo907's suggestion to create a new FF profile.

I would, but I'm using Window's. I don't have access to a terminal.

---

### Post by coffeecat on 2013-12-19
I've never done this myself, but this should help:

[http://kb.mozillazine.org/Creating_a_new_Firefox_profile_on_Windows](http://kb.mozillazine.org/Creating_a_new_Firefox_profile_on_Windows)

---

### Post by tfrue on 2013-12-19
> **coffeecat said:**
> I've never done this myself, but this should help:

[http://kb.mozillazine.org/Creating_a_new_Firefox_profile_on_Windows](http://kb.mozillazine.org/Creating_a_new_Firefox_profile_on_Windows)

Well...It worked, but I'm not sure why. I think I'm going to disable LastPass for that site and maybe even remove it to see if that helps. Maybe AdBlock Plus too...Thanks a lot though!

---

### Post by tfrue on 2013-12-19
So, I re-installed ABP and LastPass and now I don't have any problem logging in and out with the new profile. Strange...But again, thanks!

---

### Post by matt-fastz on 2014-04-07
Just received an email from Ubuntu saying the Ubuntu One service will be discontinued as of 1 June 2014. How's this going to affect our SSO service to this forum?

---

### Post by Elfy on 2014-04-07
The shutdown will not affect the Ubuntu One single sign on service, the Ubuntu One payment service, or the backend U1DB database service.

[http://blog.canonical.com/2014/04/02/shutting-down-ubuntu-one-file-services/](http://blog.canonical.com/2014/04/02/shutting-down-ubuntu-one-file-services/)

---

### Post by BBQdave on 2014-04-07
> **matt-fastz said:**
> Just received an email from Ubuntu saying the Ubuntu One service will be discontinued as of 1 June 2014. How's this going to affect our SSO service to this forum?

"The shutdown will not affect the Ubuntu One single sign on service, the  Ubuntu One payment service, or the backend U1DB database service." - [**Ubuntu One Blog**]("http://voices.canonical.com/ubuntuone/2014/04/02/shutting-down-ubuntu-one-file-services/")

Oops, Elfy's post was not there when I started post :D

---

### Post by PaulW2U on 2014-04-07
> **matt-fastz said:**
> Just received an email from Ubuntu saying the Ubuntu One service will be discontinued as of 1 June 2014. How's this going to affect our SSO service to this forum?

It won't.

From - [http://blog.canonical.com/2014/04/02/shutting-down-ubuntu-one-file-services/](http://blog.canonical.com/2014/04/02/shutting-down-ubuntu-one-file-services/)
[COLOR=#333333][FONT=Ubuntu]> The shutdown will not affect the Ubuntu One single sign on service, the Ubuntu One payment service, or the backend U1DB database service.

Strange - I didn't see Elfy's post either. [/FONT][/COLOR]:confused:

---

### Post by cecilieaux on 2014-06-27
Will we still be able to do SSO login UbuntuOne is finally gone?

---

### Post by s.fox on 2014-06-27
> **cecilieaux said:**
> Will we still be able to do SSO login UbuntuOne is finally gone?

Yes.

> **The shutdown will not affect the Ubuntu One single sign on service**, the Ubuntu One payment service, or the backend U1DB database service.

From - [http://blog.canonical.com/2014/04/02/shutting-down-ubuntu-one-file-services/](http://blog.canonical.com/2014/04/02/shutting-down-ubuntu-one-file-services/)

---

