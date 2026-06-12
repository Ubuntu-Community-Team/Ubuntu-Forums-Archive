---
title: "OpenID"
date: 2007-06-05
forum: Forum Feedback &amp; Help
---

### Post by DPic on 2007-06-05
Would it be a good idea to use [OpenID]("http://openid.net/")? 

From the website:
"[OpenID]("http://openid.net/") is an open, decentralized, free framework for user-centric digital identity.

OpenID starts with the concept that anyone can identify themselves on the Internet the same way websites do-with a URI (also called a URL or web address). Since URIs are at the very core of Web architecture, they provide a solid foundation for user-centric identity.

The first piece of the OpenID framework is authentication -- how you prove ownership of a URI. Today, websites require usernames and passwords to login, which means that many people use the same password everywhere. With OpenID Authentication, your username is your URI, and your password (or other credentials) stays safely stored on your OpenID Provider (which you can run yourself, or use a third-party identity provider).

To login to an OpenID-enabled website (even one you've never been to before), just type your OpenID URI. The website will then redirect you to your OpenID Provider to login using whatever credentials it requires. Once authenticated, your OpenID provider will send you back to the website with the necessary credentials to log you in. By using Strong Authentication where needed, the OpenID Framework can be used for all types of transactions, both extending the use of pure single-sign-on as well as the sensitivity of data shared.

Beyond Authentication, the OpenID framework provides the means for users to share other components of their digital identity. By utilizing the emerging OpenID Attribute Exchange specification, users are able to clearly control what pieces of information can be shared by their Identity Provider, such as their name, address, or phone number.

Today, OpenID has emerged as the de-facto user-centric identity framework allowing millions of people to interact online. With programs such as the [I Want My OpenID Bounty]("http://iwantmyopenid.org/bounty"), developers of Open Source projects are rapidly adding support for OpenID in order to enable their communities."

---

### Post by ubuntu-geek on 2007-06-06
At this time we do not plan to integrate openid into the forums.

---

### Post by flabdablet on 2007-06-08
Might be kind of nice to make it easy for anybody with an Ubuntu box to be their own OpenID provider, if they wanted.  Has anybody made [[COLOR="Blue"]_gracie_[/COLOR]]("http://trac.whitetree.org/gracie/") available as an Ubuntu package?

---

### Post by atoponce on 2007-06-09
> **ubuntu-geek said:**
> At this time we do not plan to integrate openid into the forums.  How come?  Are there technical limitations that keep it from happening, or just not a priority?  I too would like to see OpenID implemented in the forums.

---

### Post by Saoshyant on 2007-07-10
> **atoponce said:**
> How come?   Are there technical limitations that keep it from happening, or is it just not a priority?   I too would like to see OpenID implemented in the forums.

The feeling is mutual.

---

### Post by wubrgamer on 2009-04-10
> **saoshyant said:**
> the feeling is mutual.

+1 ;)

---

### Post by ubuntu27 on 2009-04-10
Canonical's [LaunchPad]("https://launchpad.net/") is also an OpenID provider

[https://help.launchpad.net/YourAccount/OpenID]("https://help.launchpad.net/YourAccount/OpenID")

It will be nice to be able to use OpenID in this forum also.
But, of course, I can see that it is not top pritotity. 

But, I wonder if there is some technical limitation that prevents ubuntuforums from using OpenID? Perhaps it is because they use [vBulletin]("http://www.vbulletin.com/"), which is proprietary?

---

### Post by jpeddicord on 2009-04-11
> **ubuntu27 said:**
> Perhaps it is because they use [vBulletin]("http://www.vbulletin.com/"), which is proprietary?

That would have nothing to do with it, really. Sure, the software is under a non-free license, but when you purchase it you get the entire vBulletin PHP source, which allows you to develop plugins for it. Example: [http://www.vbulletin.org/forum/showthread.php?t=120923](http://www.vbulletin.org/forum/showthread.php?t=120923)

---

### Post by jdong on 2009-04-11
We were testing an OpenID authentication bridge on a test config of the forums; it's still not ready yet to roll out.

---

### Post by ubuntu27 on 2009-04-11
Thank you Jdong and jacobmp92 for the input and update.

---

### Post by ubuntu27 on 2009-06-28
So, looks like it is now possible to use OpenID in Ubuntuforums. 
Is it complete?

---

### Post by cariboo on 2009-06-28
It just went live this morning UTC+8, seems to be working great.

---

### Post by idris83 on 2009-07-26
I can't see any options to log in using openID (only launchpad.net).

How does this work then?

---

### Post by zekopeko on 2009-07-26
> **idris83 said:**
> I can't see any options to log in using openID (only launchpad.net).

How does this work then?

launchpad is an OpenID provider.

---

### Post by DPic on 2009-07-26
> **zekopeko said:**
> launchpad is an OpenID provider.

so you can't log in using any other provider?

---

### Post by ubuntu27 on 2009-07-26
> **DPic said:**
> so you can't log in using any other provider?

Yes. We can only use [LaunchPad]("https://launchpad.net/")'s [OpenID]("https://help.launchpad.net/YourAccount/OpenID").

I don't know if it is going to change. Might we consider this as a bug?

---

### Post by zekopeko on 2009-07-26
> **ubuntu27 said:**
> Yes. We can only use [LaunchPad]("https://launchpad.net/")'s [OpenID]("https://help.launchpad.net/YourAccount/OpenID").

I don't know if it is going to change. Might we consider this as a bug?

I doubt it's a bug since it clearly states that you can only login with LP's OpenID. So I conclude it's by design.

---

### Post by idris83 on 2009-07-26
Urm. Doesn't locking it to a single provider sort of **totally** defeat the purpose of using openID? Or is that only a temporary measure?

---

### Post by jpeddicord on 2009-07-27
> **idris83 said:**
> Urm. Doesn't locking it to a single provider sort of **totally** defeat the purpose of using openID? Or is that only a temporary measure?

It's not advertised as an OpenID sign on. It's used, like [many]("http://wiki.ubuntu.com") [other]("http://revu.ubuntuwire.com") [ubuntu]("http://help.ubuntu.com/community") [sites]("http://shipit.ubuntu.com"), to let you sign in with your Launchpad account to have one less thing to keep track of. Though, at the moment you have to have a forum account to link your Launchpad account to.

It's not uncommon to see sites using an OpenID backend just for the purpose of single sign-on.

---

### Post by LepeKaname on 2009-07-27
How can we use our OpenID in this forum?

Update: I see it now! in the CP... there are 2 fields: OpenID and LaunchPad ID... neat!

---

### Post by idris83 on 2009-07-27
> **jacobmp92 said:**
> It's not advertised as an OpenID sign on.

It is in this thread ;)

---

### Post by idris83 on 2009-07-27
> **LepeKaname said:**
> How can we use our OpenID in this forum?

Update: I see it now! in the CP... there are 2 fields: OpenID and LaunchPad ID... neat!

Oh yes, I see it now. But what does it do? I filled in my openID url and all it *seems* to have done is to put an extra field in my profile.

---

### Post by jpeddicord on 2009-07-27
> **idris83 said:**
> Oh yes, I see it now. But what does it do? I filled in my openID url and all it *seems* to have done is to put an extra field in my profile.

As far as I know it's only used internally by the plugin. When you link your Launchpad account, your Launchpad OpenID URL is stored there.

---

### Post by jenkinbr on 2009-07-27
> **jacobmp92 said:**
> as far as i know it's only used internally by the plugin. When you link your launchpad account, your launchpad openid url is stored there.
+1

---

### Post by idris83 on 2009-07-27
Okay, so the forums *don't* support openID then.

Are there any plans to add this functionality?

---

### Post by bodhi.zazen on 2009-07-27
> **idris83 said:**
> Okay, so the forums *don't* support openID then.

Are there any plans to add this functionality?

You can log into the forums using Openid.

I do not think the forums will support openid outside of that as it would be duplication a function currently served by LP.

---

### Post by yquemener on 2009-07-28
Hi, new member here. I just wanted to give some feedback on this.

I just registered in order to be able to post in the forums. Apparently it is now impossible to do without having a launchpad ID. So I registered launchpad, went through the email routine, then registered with launchpad ID into the forum, got through another email routine...
This integration probably made life easier for existing members but made registration longer for new members. Just my 2 cents.

1 hour earlier I just registered to bitbucket to test some functionality. It accepts outside openIDs, it took less than 2 minutes to get an account. I wish that Ubuntu forums and launchpad did not advertise openID as a way to log in into them, it made me lose some time searching for a way to use my regular openID provider.

Anyway, whatever the registration procedure, it is great these forums exist and are opened ! Please just don't tell that one call log using openID, it is misleading.

---

### Post by jenkinbr on 2009-07-28
> **yquemener said:**
> Hi, new member here. I just wanted to give some feedback on this.

I just registered in order to be able to post in the forums. Apparently it is now impossible to do without having a launchpad ID. So I registered launchpad, went through the email routine, then registered with launchpad ID into the forum, got through another email routine...
This integration probably made life easier for existing members but made registration longer for new members. Just my 2 cents.

1 hour earlier I just registered to bitbucket to test some functionality. It accepts outside openIDs, it took less than 2 minutes to get an account. I wish that Ubuntu forums and launchpad did not advertise openID as a way to log in into them, it made me lose some time searching for a way to use my regular openID provider.

Anyway, whatever the registration procedure, it is great these forums exist and are opened ! Please just don't tell that one call log using openID, it is misleading.
It has been stated in the past that you still have to have a regular user account at the forums in order to link your launchpad account.  Once this is done, it is a simple matter to log in using Launchpad OpenID

And you still can create forum accounts without having launchpad credentials - not sure why you think otherwise....?

---

### Post by idris83 on 2009-07-28
> **bodhi.zazen said:**
> You can log into the forums using Openid.

Oh, I didn't know that. 

Would you mind linking to the page that allows you to login using openID, because I can't find it.

Thanks :D

---

### Post by jenkinbr on 2009-07-28
> **idris83 said:**
> Oh, I didn't know that. 

Would you mind linking to the page that allows you to login using openID, because I can't find it.

Thanks :D
[http://ubuntuforums.org/launchpad_login.php](http://ubuntuforums.org/launchpad_login.php)

It's linked right over the regular login fields on the home page.

---

### Post by bodhi.zazen on 2009-07-28
Thank you [jenkinbr]("http://ubuntuforums.org/member.php?u=446630")

---

### Post by idris83 on 2009-07-28
> **jenkinbr said:**
> [http://ubuntuforums.org/launchpad_login.php](http://ubuntuforums.org/launchpad_login.php)

It's linked right over the regular login fields on the home page.

That's a launchpad login. 

:-k I think some people in this thread are missing the point of openID slightly. 

Saying ubuntu forums supports openID because lauchpad uses openID is like saying "Welcome to our shop. We now accept MONEY" when what you mean is "We now accept Mongolian tögrögs". There's a whole world of other currencies you don't accept, and everyone else in the world is going to have to visit a beureau de change before they can use your shop.

Imagine if every website you went to said "We accept openID" - but on closer inspection, it transpired that they only accepted openID from *one single provider*, and this provider was different for every website you visited.

Now, instead of having to remember a different login and password for every website you visit, you now have to remember a different login and password for every different openID provider for all the different website you visit.

Seems a bit pointless. Am I missing something?

---

### Post by ktechkio on 2009-07-28
> **ubuntu-geek said:**
> At this time we do not plan to integrate openid into the forums.

Wonder if they can! Forum runs vbulletin.

---

### Post by jenkinbr on 2009-07-28
> **ktechkio said:**
> Wonder if they can! Forum runs vbulletin.
They have - look at the date of the post you quoted.

---

### Post by bodhi.zazen on 2009-07-28
> **idris83 said:**
> Seems a bit pointless. Am I missing something?

Yes. You are missing that the code to allow logging in with OpenID is under development.

Second, Openid is almost like GPG keys, there needs to be a network of trust. One can not simply log in becasue they use OpenID, we need to determine what, if any, additional OpenID servers we wish to allow on the forums.

If you are interested in OpenID on the forums, come to the FC meeting, OpenID is on the agenda.

---

### Post by SciFi-Bob on 2009-07-28
> **bodhi.zazen said:**
> Yes. You are missing that the code to allow logging in with OpenID is under development.

Second, Openid is almost like GPG keys, there needs to be a network of trust. One can not simply log in becasue they use OpenID, we need to determine what, if any, additional OpenID servers we wish to allow on the forums.

If you are interested in OpenID on the forums, come to the FC meeting, OpenID is on the agenda.

I thought the whole point with OpenID was, that the user could choose whatever provider he wanted, even his own server..

OpenID just makes it easier to have a common password for multiple sites.

Actually, I cannot see the problem here. Clearly you need an account on the board to login, and it is a requirement to link that account to an actual provider if you want to use an OpenID for login.

That's fine, but limiting providers really defeats the whole point of using an OpenID.

---

### Post by lisati on 2009-07-28
> **SciFi-Bob said:**
> I thought the whole point with OpenID was, that the user could choose whatever provider he wanted, even his own server..

OpenID just makes it easier to have a common password for multiple sites.

Actually, I cannot see the problem here. Clearly you need an account on the board to login, and it is a requirement to link that account to an actual provider if you want to use an OpenID for login.

That's fine, but limiting providers really defeats the whole point of using an OpenID.

There needs to be some degree of trust and security precautions - we don't want just any rogue having access to information that could let said rogue log into the forums, launchpad, or wherever and get up to mischief.

---

### Post by idris83 on 2009-07-28
> **lisati said:**
> There needs to be some degree of trust and security precautions - we don't want just any rogue having access to information that could let said rogue log into the forums, launchpad, or wherever and get up to mischief.

OpenID endpoints are capable of sharing a user's name, email, country, website, etc. 

Ideally, on their first visit, the user should simply have to enter their openID and authenticate themselves, and an account and profile will be automatically filled out for them using the meta-data provided by their endpoint.

Then, if the website in question is paranoid, an email can be automatically sent to the email address provided by their endpoint for verification.

First visit to website:

[LIST=1]
[*]Enter openID and authenticate yourself
[*]Click a validation link in your email
[/LIST]
Subsequent visits:

[LIST=1]
[*]Enter openID and authenticate yourself
[/LIST]
From a "trust" point of view, this is no different to a normal sign-up. You already let in anyone with an email address, so what's the difference?

---

### Post by bodhi.zazen on 2009-07-28
> **idris83 said:**
> That's a launchpad login. 

:-k I think some people in this thread are missing the point of openID slightly. 

Saying ubuntu forums supports openID because lauchpad uses openID is like saying "Welcome to our shop. We now accept MONEY" when what you mean is "We now accept Mongolian tögrögs". There's a whole world of other currencies you don't accept, and everyone else in the world is going to have to visit a beureau de change before they can use your shop.

Imagine if every website you went to said "We accept openID" - but on closer inspection, it transpired that they only accepted openID from *one single provider*, and this provider was different for every website you visited.

Now, instead of having to remember a different login and password for every website you visit, you now have to remember a different login and password for every different openID provider for all the different website you visit.

Seems a bit pointless. Am I missing something?

I am going to close this thread now as it is  starting to attract some uninformed off topic posts, like the one above. This thread is quite old and was in fact started in June of 2007. Since the thread was started we now allow one to log into the forums using a Launchpad Openid.

On the front page, when you log in, you will see a link :

    [Sign in using your Launchpad ID]("http://ubuntuforums.org/launchpad_login.php")

The link clearly states that a launchpad ID is required. This is a relatively new feature on these forums and we hope you enjoy it. If you find bugs please report them so they can be fixed.

The above analogy to money is simply not appropriate. We do not hold ourselves out as accepting any ID outside of Launchpad for one. So we are really not saying we accept "money", we are saying we allow "launchpad money".

The money analogy is quite poor and, no offense intended,  shows you really do not understand how openid works or what service is provided on these forums.

Furthermore the statement that we do not support openid because we the forums are not an openid provider is just as misinformed and misleading as the money anology.

If you want to know about OpenID please see :

[http://en.wikipedia.org/wiki/OpenID](http://en.wikipedia.org/wiki/OpenID)

The forums allows login using openid and currently accepts launchpad as the only provider. There are no plans to make the fourms an openid provider.

---

