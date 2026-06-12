---
title: "Ubuntuforums.org SSL Security"
date: 2008-06-16
forum: Forum Feedback &amp; Help
---

### Post by gmendoza on 2008-06-16
Greets, folks.  I would really like to see Ubuntuforums.org protect user login, session tracking, and search data with SSL, just as many of the related sites do.  e.g. launchpad.net, wiki.ubuntu.com.

Even help.ubuntu.com is redirected to use SSL, and it's not even used for passing sensitive data.

I would assume others share my concern over the matter, but it really is important to me, and figured it's as good a time as any to bring it up.

Thanks for listening.

Gilbert

---

### Post by PriceChild on 2008-06-16
I hardly know anything about this, and am not being a voice of staff in this post...

I'm not sure if ssl is really worth it on a forum like this, and even then, whether the current infrastructure could handle the load increase?

The reason the wikis use ssl is because they use launchpad to authenticate, which needs to be more secure because of the things on the site.

---

### Post by LaRoza on 2008-06-16
> **gmendoza said:**
> Greets, folks.  I would really like to see Ubuntuforums.org protect user login, session tracking, and search data with SSL, just as many of the related sites do.  e.g. launchpad.net, wiki.ubuntu.com.

The only "personal" information that is sent is the user name and password. 

Sessions end with the browser closing (unless you check otherwise).

---

### Post by gmendoza on 2008-06-17
> I'm not sure if ssl is really worth it on a forum like this, and even then, whether the current infrastructure could handle the load increase?

I'd be very surprised if the Canonical team is not making use of hardware assisted SSL accelerators.  And you don't have to encrypt all forum traffic, just the username/password exchange.


> The only "personal" information that is sent is the user name and password.

Sessions end with the browser closing (unless you check otherwise).

That's exactly what we should be protecting.  Theft of cookies and unencrypted password exchange is trivial.

Yes... I know it's ultimately up to people to obey best practices when logging into sites... but it's also courteous for those that know better to help a situation when it's within their means.  People may often find themselves on untrusted hotspot networks, and it would be a shame for them not to feel comfortable participating in forum discussions when they don't want to log in for fear of exposing their passwords.

This really isn't meant to cast responsibility or debate security implications, just a friendly suggestion that I'm sure Canonical and fellow Ubunteros would appreciate.

Thanks.

---

### Post by LaRoza on 2008-06-17
> **gmendoza said:**
> That's exactly what we should be protecting.  Theft of cookies and unencrypted password exchange is trivial.

Yes... I know it's ultimately up to people to obey best practices when logging into sites... but it's also courteous for those that know better to help a situation when it's within their means.  People may often find themselves on untrusted hotspot networks, and it would be a shame for them not to feel comfortable participating in forum discussions when they don't want to log in for fear of exposing their passwords.


You do realise you contradicted yourself? Only encrypt login credentials, but not the rest of the site but the theft of cookies is trivial. If SSL were to be used, it would have to be used for the entire site. Better yet, force re-authentication every time an action is made (not sarcastic, some moderator actions require that)

You can always use a portable browser, like [Opera]("http://www.kejut.com/operaportable") and [Firefox]("http://portableapps.com/apps/internet/firefox_portable"). You can use them on a flash drive and use whatever password managers they have (Opera has wand, a very good manager)

---

### Post by gmendoza on 2008-06-17
> **LaRoza said:**
> You do realise you contradicted yourself? Only encrypt login credentials, but not the rest of the site but the theft of cookies is trivial. If SSL were to be used, it would have to be used for the entire site. Better yet, force re-authentication every time an action is made (not sarcastic, some moderator actions require that)

No offense taken or anything, as I see where perhaps I didn't make myself clear enough.  I was responding to the notion of increased load and what one strategy would be to remedy that particular situation; encrypt only authentication data.  I didn't expand on this next point.

Being that your cookie is part of your ongoing authenticated access and just as important as your password, and should be protected using SSL.  You do not have to encrypt an entire page just to protect cookie transmission.

> **LaRoza said:**
> You can always use a portable browser, like [Opera]("http://www.kejut.com/operaportable") and [Firefox]("http://portableapps.com/apps/internet/firefox_portable"). You can use them on a flash drive and use whatever password managers they have (Opera has wand, a very good manager)

SSL is to protect network based MITM attacks.  You are referring to theft of stored cookies, which is not the attack vector I'm concerned with.  If you are using an untrusted computer, then your password is at risk of being stolen anyway.

---

### Post by LaRoza on 2008-06-17
> **gmendoza said:**
> SSL is to protect network based MITM attacks.  You are referring to theft of stored cookies, which is not the attack vector I'm concerned with.  If you are using an untrusted computer, then your password is at risk of being stolen anyway.

True. However, I do feel that using untrusted computers is by itself a fail. The average (I think) poster is using a home computer, a friend/family computer or a work/school computer. 

If one feels that the computer being used isn't secure enough to use the forum, then I question using that computer.

---

### Post by gmendoza on 2008-06-17
> **LaRoza said:**
> True. However, I do feel that using untrusted computers is by itself a fail. The average (I think) poster is using a home computer, a friend/family computer or a work/school computer. 

If one feels that the computer being used isn't secure enough to use the forum, then I question using that computer.

Agreed 100%.  My concern and reference was for someone using their own computer on an untrusted *network*.  But since that pretty much equates to *any* Internet connection, that's the reason behind SSL to begin with.

Anyway, thanks for your concern in the matter.  I really hope this conversation isn't taken as an argument, but simply clarification.  Tone can easily be lost in translation.

---

### Post by LaRoza on 2008-06-17
> **gmendoza said:**
> Agreed 100%.  My concern and reference was for someone using their own computer on an untrusted *network*.  But since that pretty much equates to *any* Internet connection, that's the reason behind SSL to begin with.

Anyway, thanks for your concern in the matter.

I really have no control or say in this matter. It would, I think, be ultimately Canonical's decision and action.

Having a trusted ISP, and a good router should be enough. Of course, anyone that truly wants to spy and has the knowledge could do it, but there is a fundamental rule in security. The best way to secure something is to make compromising it more expensive that it is worth. So for a bank with a million dollars in it, make it cost one million and one dollars to compromise it. 

I don't think Ubuntuforums is a worthy enough target or anyone but the admins accounts.

---

### Post by gmendoza on 2008-06-17
I hope you read the last sentence of my last post.  I edited it right before/after you submitted yours.  Again, thanks for the attention you've given to the thread.

> **LaRoza said:**
> I don't think Ubuntuforums is a worthy enough target or anyone but the admins accounts.

Here's an excerpt of a point I made in an email I just sent to the Canonical and Ubuntu web team, which I thought it was applicable to this post.

--
Let's be honest, even though I created unique passwords for each site
that doesn't use password hashing or SSL, many other people use the same
password for everything which puts them at risk.  This is not about just
protecting their forum access, but anything else users may give up as a
result of this habit.  Sure if it's not access to the Ubuntu forums that
 divulge their credentials, it will be another site.  But at least it
*wont* be the Ubuntu forums.
--

---

### Post by FuturePilot on 2008-06-17
> **LaRoza said:**
> True. However, I do feel that using untrusted computers is by itself a fail. The average (I think) poster is using a home computer, a friend/family computer or a work/school computer. 

If one feels that the computer being used isn't secure enough to use the forum, then I question using that computer.
I will never log onto this site or any other site that doesn't use encryption from school because I can almost guarantee there's many packet sniffers running for various assignments and such. That is why I have thought of this same idea and I would think just encrypting the exchange of username and password would be enough.
> **LaRoza said:**
> 

I don't think Ubuntuforums is a worthy enough target or anyone but the admins accounts.
I know there are people out there that would steal a password just for the sake of stealing a password. :|

---

### Post by rune0077 on 2008-06-17
I'm not sure I'm getting this? This is not Internet banking or anything, so why the extra need for protection? I have no personal data at these forums that anyone could possible want. Even if they did steal my password, they could not really use it for very much, other than to make me look like a fool (and I do a fine enough job at that myself already, thank you very much).

---

### Post by LaRoza on 2008-06-17
> **rune0077 said:**
> I'm not sure I'm getting this? This is not Internet banking or anything, so why the extra need for protection? I have no personal data at these forums that anyone could possible want. Even if they did steal my password, they could not really use it for very much, other than to make me look like a fool (and I do a fine enough job at that myself already, thank you very much).

And it would be trivial to change your password, and to undo whatever was done.

To date, I think there was one possible case of this happening.

---

### Post by gmendoza on 2008-06-17
> **rune0077 said:**
> ...I have no personal data at these forums that anyone could possible want. Even if they did steal my password, they could not really use it for very much...

Again... this is not just about a forum account, fellas.

If you follow best practice, then I'm sure you have unique passwords for every online account you own, and that your forum password is nothing at all related to any of your other accounts.  Fantastic... no problem.

But the truth is, many of our community members will reuse their passwords for many of the other sites and computers they access.  Their forum profile is likely not a target, but one's banking or email account might be.

Is this Canonicals fault?  Heck no.  But, if it's within someone's power to make a simple difference without much of a cost, then why not?  It's one less thing people have to worry about, and it makes you feel fuzzy.

The suggestion is meant to simply help the community, even if they don't know they need it.  :-)

---

### Post by LaRoza on 2008-06-17
> **gmendoza said:**
> 
If you follow best practice, then I'm sure you have unique passwords for every online account you own, and that your forum password is nothing at all related to any of your other accounts.  Fantastic... no problem.

But the truth is, many of our community members will reuse their passwords for many of the other sites and computers they access.  Their forum profile is likely not a target, but one's banking or email account might be.


I admit it, I do not have unique passwords for everything, however, my forum account password is actually very weak. The reason it is weak is because the risk analysis came out that this password wouldn't be important. (When I became a mod, I made the password stronger, but it is still weaker than my typical passwords)

---

### Post by rune0077 on 2008-06-17
> **gmendoza said:**
> Again... this is not just about a forum account, fellas.

If you follow best practice, then I'm sure you have unique passwords for every online account you own, and that your forum password is nothing at all related to any of your other accounts.  Fantastic... no problem.

But the truth is, many of our community members will reuse their passwords for many of the other sites and computers they access.  Their forum profile is likely not a target, but one's banking or email account might be.

Is this Canonicals fault?  Heck no.  But, if it's within someone's power to make a simple difference without much of a cost, then why not?  It's one less thing people have to worry about, and it makes you feel fuzzy.

The suggestion is meant to simply help the community, even if they don't know they need it.  :-)

I keep the exact same password for various social/productive/fun accounts, sure, but I have seperate unique passwords for anything that involves money or private data (like gmail).

The best way for people to remember to lock their doors, is for them to have a break-in :) Some people have to learn the hard way, as the saying go.

But okay, added security is never a bad thing if it can be implemented, so I won't complain of course. If it can't, it won't keep me awake at night, though.

---

### Post by p_quarles on 2008-06-17
It's certainly true that the connection is not secure, and anyone with their wits about them would be able to sniff login data for these forums pretty easily. But, there's really nothing all that valuable to be gained from those, and the people who steal passwords "just because" aren't the same as the people who set up personal data mining operations. 

For those who'd prefer not to have to worry about untrusted networks at all, there's always ssh tunneling.

---

### Post by hyper_ch on 2008-06-18
Well, if you use the same passwords on social sites as for your online banking then you ask for problems right away.

Instead of protecting users from all the hazards in the world, the users should start protecting themselves... why do we have a brain to think? Definitively not for being spoon-fed all the time.

---

### Post by kevdog on 2008-06-21
Crap

I just found out another user has been masquerading as KevDog for months.  I hope this doesn't mean black beans for me!  Gotta stop using the public wifi connection!

---

### Post by LaRoza on 2008-06-21
> **kevdog said:**
> Crap

I just found out another user has been masquerading as KevDog for months.  I hope this doesn't mean black beans for me!  Gotta stop using the public wifi connection!

Really? Change your password if that is the case.

---

### Post by kevdog on 2008-06-22
> **LaRoza said:**
> Really? Change your password if that is the case.

No -- I guess I lied.  However I would be really angry if my password were lifted and someone masqueraded as me.  There seems like there should be a better security mechanism in place above transferring passwords in clear text?!  I know UG only runs these forums off 2 computers, however you think MS would throw him a few bucks so he run the site using SSL certs.

---

### Post by LaRoza on 2008-06-22
> **kevdog said:**
> No -- I guess I lied.  However I would be really angry if my password were lifted and someone masqueraded as me.  There seems like there should be a better security mechanism in place above transferring passwords in clear text?!  I know UG only runs these forums off 2 computers, however you think MS would throw him a few bucks so he run the site using SSL certs.

I thought you were (and my first response was also a joke) but I didn't want to take chances.

(My first response was an offer to ban you and your IP)

Is this security needed? I don't think so. To get an account, you just need an email address. Technically, stealing a password from someone is easy, but not rewarding. The worst you could do is mess up an account. To get the credentials of an admin would be the goal, and there are only five of them.

---

### Post by kevdog on 2008-06-22
I kind of like my credentials as an ordinary user also.  I wouldn't want someone stealing my identify on the Ubuntu forums.  I've invested too much time and energy.

---

### Post by LaRoza on 2008-06-22
> **kevdog said:**
> I kind of like my credentials as an ordinary user also.  I wouldn't want someone stealing my identify on the Ubuntu forums.  I've invested too much time and energy.

It would be easy to undo, and the chances of it happening are low. It would be more likely to have someone to have access to your computer and use it when you are logged on (that has happened a few times here).

---

### Post by kevdog on 2008-06-22
That wouldn't happen -- my attack dog would rip that person's head off!

---

### Post by LaRoza on 2008-06-22
> **kevdog said:**
> That wouldn't happen -- my attack dog would rip that person's head off!

Your attack dog could do it, 

[img]http://weblogs.mozillazine.org/gerv/archives/2007/images/internet_dog.jpg[/img]

---

### Post by kevdog on 2008-06-22
Hmmm never thought about that possibility :confused:

---

### Post by virx on 2008-07-08
Currently logged into this forum from tech university campus LAN with few hundred future IT specialists living in it. How likely it is that somebody is just testing "Cain & Abel" just to see what it can sniff.

Should I change my password from another connection now?

Is ubuntuforums.org doing everything for protecting their members enough? Specially if using SSL only for password exchange wouldn't need much financial resources?

---

### Post by LaRoza on 2008-07-08
> **virx said:**
> Currently logged into this forum from tech university campus LAN with few hundred future IT specialists living in it. How likely it is that somebody is just testing "Cain & Abel" just to see what it can sniff.
How likely? Not likely. The traffic is probably very high on the campus.

Is it possible? Yes.
> 
Should I change my password from another connection now?

If you feel the people on the campus are untrustworthy scammers, yes.

> 
Is ubuntuforums.org doing everything for protecting their members enough? Specially if using SSL only for password exchange wouldn't need much financial resources?
It does everything but encrypt, and encrypting in this case would be too much of a strain.

---

### Post by adamclinch on 2008-08-18
It's an interesting topic and I think that theft of any part of a persons identity is troublesome, be it a forum account or a credit history.

It would be nice to at least have an option to use encrypted authentication at times when you 'know' that your traffic could be monitored. Plenty of cafe wireless access points are unencrypted and there's often lots of people connected with laptops possibly reading your data. 

Besides, no one wants their name to be on the 'wall of sheep'

---

### Post by Technoviking on 2008-08-18
Does anyone have an example of an internet forum using SSL? I never recall ever seeing one that does.

---

### Post by Dr Small on 2008-08-18
> **Mike said:**
> Does anyone have an example of an internet forum using SSL? I never recall ever seeing one that does.
No. But we could be a first! It really wouldn't be that hard to setup, so I don't see why it is some cumbersome. But anyhow, whether or not UbuntuForums has an SSL certificate, one can always use a web (HTTP) proxy that uses SSL, start the encrypted connection at that point, and then login to the forums. This would eliminate sending the password over raw TCP for it to be sniffed / used for Universities, Cafe's, etc.

---

### Post by LaRoza on 2008-08-19
> **Dr Small said:**
> No. But we could be a first! It really wouldn't be that hard to setup, so I don't see why it is some cumbersome. But anyhow, whether or not UbuntuForums has an SSL certificate, one can always use a web (HTTP) proxy that uses SSL, start the encrypted connection at that point, and then login to the forums. This would eliminate sending the password over raw TCP for it to be sniffed / used for Universities, Cafe's, etc.

You want to set it up? You want to pay for the proxy? 

Also, there is no evidence this is an issue.

---

### Post by Joeb454 on 2008-08-19
I just have the browser remember my passwords :)

---

### Post by Dr Small on 2008-08-19
> **LaRoza said:**
> You want to set it up?
Yes, and I would definitely use it. 

> **LaRoza said:**
> 
You want to pay for the proxy?
I wouldn't have to. I can setup bblocked on a remote host that supports SSL. My connection is then encrypted to that host.

> **LaRoza said:**
> 
Also, there is no evidence this is an issue.
Then I challenge you to login to your UbuntuForums account and packetsniff with Wireshark. You will very plainly see the issue, when you observe your password being broadcasted in plaintext across your network (and not to mention, every other network your connection passes through, to the destination)

---

### Post by LaRoza on 2008-08-19
> **Dr Small said:**
> I wouldn't have to. I can setup bblocked on a remote host that supports SSL. My connection is then encrypted to that host.

You deal realise performance of this forum is a result of heavy duty tweaking? Without the special care to keep performance up, this forum crashes in an instant.


> 
Then I challenge you to login to your UbuntuForums account and packetsniff with Wireshark. You will very plainly see the issue, when you observe your password being broadcasted in plaintext across your network (and not to mention, every other network your connection passes through, to the destination)

I am very well aware of the "issue". However, it isn't an issue in practice.

---

### Post by Technoviking on 2008-08-21
Dr. Small, you are welcome to add this as a topic at an upcoming Forums Council meeting ([https://wiki.ubuntu.com/ForumCouncilAgenda](https://wiki.ubuntu.com/ForumCouncilAgenda)), but at this time the benefit is probably not worth the extra strain put on the forums server and software.

I'm all for security, but not at the cost of the forums not being able to handle the large number of people who use it.

---

### Post by gmendoza on 2008-08-25
> **Mike said:**
> I'm all for security, but not at the cost of the forums not being able to handle the large number of people who use it.

With all due respect, no one is suggesting that you implement something haphazardly or at the cost of usability.  Forgoing the implementation of SSL due to some type of server strain based on pure conjecture is silly.

Just offload SSL acceleration to dedicated systems or appliances like all other enterprises in the world.  These forums are nothing special in comparison to many other larger sites out there.

Anyway... thanks for everyone's input.  I guess it all was just a "lame idea".  Now I'm just tired of trying to convince people of something that should have been a very simple concept to understand.

---

### Post by cyberdork33 on 2008-08-25
> **gmendoza said:**
> Just offload SSL acceleration to dedicated systems or appliances like all other enterprises in the world.  These forums are nothing special in comparison to many other larger sites out there.
So I guess you are volunteering the money and resources?

---

### Post by Joeb454 on 2008-08-25
> **gmendoza said:**
> Just offload SSL acceleration to dedicated systems or appliances like all other enterprises in the world.  These forums are nothing special in comparison to many other larger sites out there.

If you can convince Canonical to buy another server (there's only 2) then I'm sure this could be implemented

---

### Post by LaRoza on 2008-08-25
> **gmendoza said:**
> With all due respect, no one is suggesting that you implement something haphazardly or at the cost of usability.  Forgoing the implementation of SSL due to some type of server strain based on pure conjecture is silly.

Is it? None of us have physical access to the servers.

> 
Just offload SSL acceleration to dedicated systems or appliances like all other enterprises in the world.  These forums are nothing special in comparison to many other larger sites out there.
Nothing special? Yes they are. This forum runs on hardware that larger sites (and equally sized sites) wouldn't use.

> 
Anyway... thanks for everyone's input.  I guess it all was just a "lame idea".  Now I'm just tired of trying to convince people of something that should have been a very simple concept to understand.
Simple concept? In theory yes, but remember, no one here owns the forums or owns the servers. What you are suggesting is basically the same as asking us to upgrade Yahoo!'s servers.

---

### Post by Canis familiaris on 2008-08-26
> **LaRoza said:**
> Is it? None of us have physical access to the servers.

Except you of course. (Aren't you the server itself?)

---

### Post by LaRoza on 2008-08-26
> **Anurag_panda said:**
> Except you of course. (Aren't you the server itself?)

Well, do you have direct access to your own kidneys?

---

### Post by Canis familiaris on 2008-08-27
> **LaRoza said:**
> Well, do you have direct access to your own kidneys?

I didnt think about abstraction.

---

