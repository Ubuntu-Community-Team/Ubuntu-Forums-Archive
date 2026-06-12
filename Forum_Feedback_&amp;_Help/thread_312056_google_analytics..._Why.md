---
title: "google analytics... Why?"
date: 2006-12-03
forum: Forum Feedback &amp; Help
---

### Post by JLB on 2006-12-03
Why do the forums use google analytics? Is it a "MUST" ? It really slows stuff down. I find that oftentimes page load is just hanging, waiting on google analytics to respond. It's quite annoying.

---

### Post by aysiu on 2006-12-03
I disabled it using NoScript, so I don't know if it slows things down.

By the way, I've moved your thread to the appropriate place.

---

### Post by mikerduffy on 2006-12-03
> **aysiu said:**
> I disabled it using NoScript, so I don't know if it slows things down.

Ditto that. Google Analytics, DoubleClick, SiteMeter, etc.  I block anything that isn't necessary.

---

### Post by ubuntu-geek on 2006-12-03
I'll have to find a way around it :)

---

### Post by aretei on 2006-12-03
I also disable JavaScripts with NoScript. Do any of you guys mind sharing me what Google Analytics does? I always see sites using it but never figured out the exact purpose.

---

### Post by aysiu on 2006-12-03
From [Google's website](http://www.google.com/analytics/): > Google Analytics tells you everything you want to know about how your visitors found you and how they interact with your site. You'll be able to focus your marketing resources on campaigns and initiatives that deliver ROI, and improve your site to convert more visitors.

---

### Post by Bezmotivnik on 2006-12-04
> **aretei said:**
> I always see sites using it but never figured out the exact purpose.
It's data mining and spyware.

What did you *think* it was? :rolleyes: 

Y'know:  "Let's be evil."

---

### Post by KiwiNZ on 2006-12-04
> **Bezmotivnik said:**
> It's data mining and spyware.
 
What did you *think* it was? :rolleyes: 
 
Y'know: "Let's be evil."
 
No its not

---

### Post by ubuntu-geek on 2006-12-05
Using google analytics is no different then using webalizer or analog. We choose analytics because 1. its free, 2. because it takes the load of processing off our servers and 3. because the data is helpful to us when making site changes and seo positioning. Besides we've been using it for almost 9 months now and it has never been an issue before. I've even talked to the ubuntu.com webmaster Matthew in the past and they might use it as well.

---

### Post by PriceChild on 2006-12-05
I've just been browsing the forums and noticed that my NoScript isn't even complaining about it... it's not there...

Its not exactly giving you a performance hit as you describe.

---

### Post by Mimsy on 2006-12-05
My NoScript has blocked it, but Im okay with that. I'm paranoid about all scripts and block them by default.

It's not spyware, it's not datamining. Both those terms imply that somthing is being installed to your computer, and gaters information from your system, and google-analytics does not do that.

I've never managed to convince anyone of this, usually because they have heard from someone who knows someone who saw a special about this on CNN 2:30 am three months ago, that scripts can shut down your computer, use your credit card, and sell your children on the black market... you get the idea. And why would that be on CNN if it wasn't a serious threat? :rolleyes: 

Spyware ought to be illegal, and datamining is a nasty thing, and none of those terms should be thrown around lightly. Especially if you're not sure what the script you're applying them to actually does.

/Mimsy

---

### Post by Josh1 on 2006-12-05
Dialup?

---

### Post by ashwinjm on 2007-09-21
Dear Ryan and KiwiNZ, I know this is an old thread, but having been on the verge of posting something similar, I have to agree with Bezmotivnik. Google Analytics is, in a manner of speaking, spyware used for data mining. I do understand the reasons a webmaster would find it invaluable - I used it myself for quite a while. 

But when I thought about it, I was helping Google find patterns in user behaviour across potentially hundreds of thousands of websites, without informing visitors to my site that I was giving their navigation trail away to Google. Even if I were to put up a privacy notice, I could not be sure that every user would read it. Personally, I think that websites should manage their own analytics programs, or use a trusted 3rd party who will never aggregate analytics data. In the meantime, all cookies from google.com and other such behaviour tracking sites are blocked on my browser - though not on the browsers of LOTS of other users who may just not know any better.

---

### Post by kerry_s on 2007-09-21
just block it and move on to more important things. i recommend the ABP tracking filter for adblock+->

[http://adblockplus.org/en/subscriptions](http://adblockplus.org/en/subscriptions)

---

### Post by ashwinjm on 2007-09-21
As I noted in my post, I have blocked it. To restate my opinion - I do not think that it is in the spirit of FOSS to give user data away, however innocuously, and for whatever good reasons, without the informed consent of each and every such user. If a website popped up a question when you visited, asking if you would consent to giving your navigation data to Google while you were browsing that site, what would you do? I would imagine that most users would say "No". What's happening with Google Analytics as it stands today is that users are being made to say "Yes" without knowing, unless they are aware that GA is being used on a site.

---

### Post by ubuntu-geek on 2007-09-21
ubuntu.com uses it as well as a matter of fact the same code used on the ubuntu.com site is used here for the GA. wow people really need to get out more and stop crying.

---

### Post by ashwinjm on 2007-09-21
There are laws being put in place against the kind of data retention that Google and others are doing. I raised what to me, and to many others I know working on this stuff, is a hugely important concern.

I'm not saying anything more - I didn't come here to be abused.

---

### Post by fred the wise on 2008-01-09
mmm.. I think this Google Analytics isn't only for statistics, but it's used to monitor and register most kind of net activities... I've heard Google sells information even from its mail servers... is it a case?

---

### Post by nikoPSK on 2008-01-09
If you wanted to, you can always *block *google analytics. DO as follows:

this will open up etc/hosts
```
gksudo gedit /etc/hosts
```

now at the bottom line add all this then save all your work and restart your session.
```
# BLOCK GOOGLE ANALYTICS
127.0.0.1 www.google-analytics.com
127.0.0.1 ssl.google-analytics.com
127.0.0.1 google-analytics.com
```

I don't really think it's required as it sends alot of user unwwanted (sometimes) information to google. If that solves your problem, I am glad I have helped.

Best to you,
nikoPSK

---

### Post by Nano Geek on 2008-01-10
> **fred the wise said:**
> mmm.. I think this Google Analytics isn't only for statistics, but it's used to monitor and register most kind of net activities... I've heard Google sells information even from its mail servers... is it a case?I am almost certain that that is false. Wouldn't everyone know about it by know if it was true?

---

### Post by Perfect Storm on 2008-01-10
Where's my tinfoil hat.

---

### Post by PriceChild on 2008-01-10
[http://www.google.com/analytics/tos.html](http://www.google.com/analytics/tos.html)
[http://www.google.com/intl/en_ALL/privacy.html](http://www.google.com/intl/en_ALL/privacy.html)

Yes... information collected by google analytics goes further than just google and ubuntu-geek, but it is statistics and trends rather than personally identifiable information.

---

### Post by fred the wise on 2008-01-10
> **asjdfwejqrfjcvm msz34rq33 said:**
> I am almost certain that that is false. Wouldn't everyone know about it by know if it was true?
I don't have personal experience...but I'm not the only

[http://davidcancel.com/2007/12/17/facebook-hearts-google/](http://davidcancel.com/2007/12/17/facebook-hearts-google/)

---

### Post by MarkX on 2008-02-26
> **ubuntu-geek said:**
> Using google analytics is no different then using webalizer or analog. We choose analytics because 1. its free, 2. because it takes the load of processing off our servers and 3. because the data is helpful to us when making site changes and seo positioning. Besides we've been using it for almost 9 months now and it has never been an issue before. I've even talked to the ubuntu.com webmaster Matthew in the past and they might use it as well.

Well [COLOR="Red"]**I OBJECT**[/COLOR]
 I don't want data collected about me in this subversive way and I doubt   that Linux users in particular  want to be spied upon, thats why we use Linux. Aside from that, I don't trust google at all to handle information in a way that respects privacy.
I find the name "Google analytics" very apt. It's just another way to gather information without permission by the  back entrance. UBUNTU shouldn't be employing tactics that M$ is famous for. It's bad for Ubuntu's image.

---

### Post by matthew on 2008-02-26
MarkX, you obviously have very strong feelings about this. I understand. Just as you are free to use whatever operating system you want to use, proprietary or foss, I would expect you to allow others the same sorts of freedom.

We have made a decision to use something that is best for the administration of these forums. We chose to continue to use Google Analytics because it gives us the information we want in a very easy and complete package that we find useful. We're just pragmatic that way.

Consider your objection noted. Please understand that until we find something that better suits our needs, we will continue using Google Analytics.

For more on our perspective, you might appreciate the "are you imposing?" link in my signature.

---

### Post by Forrest Gumpp on 2008-02-26
If Matthew will permit me this indulgence, I should like to observe that it is indeed a red letter day for you, MarkX.

You should consider yourself wholly mis-rolled.  With this heretofore unseen side of your Linux persona now revealed, try and see this issue from another point of view:  without such analytics it would be difficult to implement such things as fund-raising for free software development.

For example, schemes such as proposed in this link:  [http://ubuntuforums.org/showthread.php?t=705814](http://ubuntuforums.org/showthread.php?t=705814)  post # 11.

Mark, you have just won the Award of the German Belt Buckle!  Matt 1:23.  Honest, its gospel.

---

### Post by MarkX on 2008-02-26
> **matthew said:**
> MarkX, you obviously have very strong feelings about this. I understand. Just as you are free to use whatever operating system you want to use, proprietary or foss, I would expect you to allow others the same sorts of freedom.

We have made a decision to use something that is best for the administration of these forums. We chose to continue to use Google Analytics because it gives us the information we want in a very easy and complete package that we find useful. We're just pragmatic that way.

Consider your objection noted. Please understand that until we find something that better suits our needs, we will continue using Google Analytics.

For more on our perspective, you might appreciate the "are you imposing?" link in my signature.

Just a sec there! I'm sure the vast majority of computer users  utterly object to being analised by google! We have no idea what information it gathers and who it gives it to (and I doubt even you know all they do with the data you allow them access to).

 **I dare you to put up a poll right now !!!:**
A) I object to google analytics collecting data about me.
B) I don't mind being analised by google analytics.

Go on post that poll and see what the community thinks! That poll data is more valuable to your company than what google analytics can feed you.

Business sense tells me that it's far more important for a company to preserve it's ethical image than to let some perceived multinational big brother gather data on your "customers", the Ubuntu community. 
I doubt the information google analytics supplies you with is so utterly indispensable that you would tarnish your company image for it.

---

### Post by aysiu on 2008-02-26
> **MarkX said:**
> 
 **I dare you to put up a poll right now !!!:**
A) I object to google analytics collecting data about me.
B) I don't mind being analised by google analytics.

Go on post that poll and see what the community thinks! Your dare is meaningless. If all you tell people is that they're "being analyzed," then of course they'll vote against that, since they (like you, apparently) have no idea what benefits analysis can have for the community or the forums.

You'd get similar results if you posted a poll in America saying, "What should the government do about taxes?" with the two answers A) Tax people more and B) Tax people less. People only think about the immediate ramifications of "Well, of course I don't want the government taking more money out of my paycheck," instead of thinking about how those taxes will affect the country, the economy, and even the culture of the country. That's why politicians lie during their campaigns and say things like "Read my lips: no new taxes" and then add new taxes once elected.

Likewise, if you asked a bunch of middle school students "What do you think teachers should do about homework?" with the two answers A) Give homework and B) Get rid of homework, I can assure you the gut reaction will be to vote for no homework. Of course, when it takes them the whole year to read one book, because they couldn't read at home, then maybe (just maybe) they'll realize they could have learned more by preparing for class. Because they're only middle schoolers, it may take ten years for them to realize it, though.

Instead of having a knee-jerk reaction against Google Analytics, why don't you ask what the forum uses it for and how it benefits the forums' operations?

---

### Post by popch on 2008-02-26
> **MarkX said:**
> (...) I'm sure the vast majority of computer users  utterly object to being analised by google! We have no idea what information it gathers and who it gives it to (...)
 I dare you to put up a poll right now !!!:.

I offer just a few thoughts on your concern, then I will be off to some other places.

What do you base your certainty on that many people will object to having some statistics collected?  

Why do you say 'we have no idea what information it gathers'? The protocols IP, TCP, HTTP and HTML are fairly well documented. From these, you can derive exactly and precisely what data Google can harvest. While it might be true that you yourself do not know what information is gathered, ***we***  certainly ***can*** know.

I do not know how you access the internet. However, unless you do so from an internet cafe or by anonymously stealing bandwidth from a neighbour, you certainly pass more data and more personally attributable information to your ISP and to a number of other nodes than you pass to Google.

Besides, if you really object so strongly to sites making use of Google analytics, you can easily avoid those sites. Also, it's not rocket science to disable Google analytics for your own PC.

Lastly, there's no need to dare anyone to do a poll. If you want a poll, make it yourself.

---

### Post by matthew on 2008-02-26
> **MarkX said:**
> Just a sec there! I'm sure the vast majority of computer users  utterly object to being analised by google! Frankly, it depends on how you phrase the question, just as with all polls. I honestly don't think "the vast majority of computer users" have given this a nanosecond's thought. Furthermore, your constant substitution of "analised" for "analyzed" makes you look immature and silly.

> **MarkX said:**
> We have no idea what information it gathers and who it gives it to (and I doubt even you know all they do with the data you allow them access to).Unless you are going to call Google liars, they tell us in the TOS what they will and will not do with the data. Feel free to read up on that and on the service as a whole.

[http://www.google.com/analytics/tos.html](http://www.google.com/analytics/tos.html)
[http://www.google.com/analytics/index.html](http://www.google.com/analytics/index.html)

 > **MarkX said:**
> **I dare you to put up a poll right now !!!:**I double dog dare you to learn to ask politely and also not make demands on others to do things you are perfectly capable of doing yourself. Sigh.

I really think aysiu covered the point quite well about a weakness in putting this to a poll. Depending on how the question was framed you could get people to tend to vote one way or another. I'm completely certain a poll phrased as you chose would lend the results you are looking for. One phrased like this would yield the opposite:

Would you support the forum administration choosing to track, record, and use data on forum usage for the purposes of making the forums run more smoothly, give better and more consistent results in online searches, and be more readily accessible to the average user?

> **MarkX said:**
> Business sense tells me that it's far more important for a company to preserve it's ethical image than to let some perceived multinational big brother gather data on your "customers", the Ubuntu community. 
I doubt the information google analytics supplies you with is so utterly indispensable that you would tarnish your company image for it.You doubt...you actually don't know. You heard someone somewhere say something about Google, you didn't like what you heard, and you decided to go on a crusade over it. Good grief. Surely you have better things to do with your time.

Again, read the "are you imposing?" link in my sig.

If you are concerned for yourself, you can block google analytics with a browser plugin like noscript. You can do it by adding a few lines to /etc/hosts. This is ultimately a trivial issue. 

We have been using this for nearly two years. It is helpful to track trends, to decide when the best times are to do forum and server maintenance, to help us determine where most of our traffic comes from and seek new ways to enhance forum visibility. Most other alternatives are not as complete in the information they provide, and/or they put all the stress on our local server, which is already taxed heavily and can't handle the increase. We have no plans to change.

> **aysiu said:**
> Your dare is meaningless. I

Instead of having a knee-jerk reaction against Google Analytics, why don't you ask what the forum uses it for and how it benefits the forums' operations?+1 on both counts. Thank you especially for the well-written description of what a poll could and could not accomplish here.

---

### Post by MarkX on 2008-02-26
> **aysiu said:**
> Your dare is meaningless. If all you tell people is that they're "being analyzed," then of course they'll vote against that, since they (like you, apparently) have no idea what benefits analysis can have for the community or the forums.

You'd get similar results if you posted a poll in America saying, "What should the government do about taxes?" with the two answers A) Tax people more and B) Tax people less. People only think about the immediate ramifications of "Well, of course I don't want the government taking more money out of my paycheck," instead of thinking about how those taxes will affect the country, the economy, and even the culture of the country. That's why politicians lie during their campaigns and say things like "Read my lips: no new taxes" and then add new taxes once elected.

Likewise, if you asked a bunch of middle school students "What do you think teachers should do about homework?" with the two answers A) Give homework and B) Get rid of homework, I can assure you the gut reaction will be to vote for no homework. Of course, when it takes them the whole year to read one book, because they couldn't read at home, then maybe (just maybe) they'll realize they could have learned more by preparing for class. Because they're only middle schoolers, it may take ten years for them to realize it, though.

Instead of having a knee-jerk reaction against Google Analytics, why don't you ask what the forum uses it for and how it benefits the forums' operations?

The poll questions were an example. You can make up your own ones if you like, so the dare stands.

 If you want this place to be a "Community" you need to ask it's members if they object to data being collected about them.
That would be an excellent opportunity to tell them exactly:
1) what this data is,
2) why you can't do without it (apparently?) ,
3) who, apart from you, has access to it.
4) who profits financially from it.

Quite importantly, you can tell those who don't want such data to be gathered about them how to bar google analytics from their computers. Preferably it should be an opt-in rather than opt-out choice.
BTW., Corporate image depends on perception (regardless of how inoccuous google anlaytics may or may not actually be) and the fact that you know what the results of a poll are likely to be shows that you've opted to go against the wishes of the alleged "community".
Ubuntu/Canonical have ceased to be a "feel good" company (for now?).

Of course you could instead make a selling point out of *NOT* gathering and passing out data on your "customers", Now that would be what the real open source ethos is about!

---

### Post by matthew on 2008-02-26
Look, you're a good forums member. I appreciate your participation, your helping other users, and I even understand that you have strong feelings on this issue.

There isn't much I can do for you, though.

You are perfectly capable of posting your poll. Daring others to do it is a silly playground game. If you want a poll, post one.

If you want answers to all your questions in the most recent post, read the links I gave you earlier. The only one not answered there is this: no one benefits financially from this data. However, the forum community benefits in other ways through our ability to adjust settings, maintenance schedules, and other stuff to make the forums run well and target the intended audience of Ubuntu users as directly as possible (that means the data helps us make the forums easier to find by giving us ideas for search keywords and software tweaks that help us show up better in Google, Yahoo, and other search engine listings).

Of course, I could make a selling out point of *NOT* using a free and simple tool that enables us to better serve our community, but that wouldn't be what a community is all about at all.

Hey, if it's okay with you, I'm kind of tired of the passive aggressive, silly backhanded slap tone of this conversation. Can we change it now? I'll start.

Google Analytics is not a sinister attempt to track all your actions and connect your visit here to some random other site you were visiting yesterday. The data collected are things like IP addresses, page hits, and so on. They are charted in a very convenient manner over time and can be compared to look for trends like when the server is most busy and least busy or what searches led people to the forums most often or what sites link to us (which can be determined, as popch mentioned, through extremely well-documented protocols). We could get the same data from local log files, but it would be unprocessed and it would take computer processing time, man hours, and therefore more money to do it other ways.

The cool thing is that by using Google Analytics, all the data is correlated ***for us*** in the neat charts and reports. Also, the processing takes place off of our servers, so it dramatically reduces the load locally, allowing us to better serve the community by keeping page load times shorter and downtime to a minimum.

That's really all there is to it. This service saves us time and money by helping us do something we could do by ourselves. 

The TOS says the data may be used by Google internally, but it will first be anonymized, so no one is tracked personally (i.e. IP addresses become IP ranges, localized by country, ISP or region, etc.). They use it to help figure out which sites have more or less traffic, and it helps in the search results within Google (and possibly other search engines, but I'm not sure on that). If that bothers you, you can block it.

---

### Post by MarkX on 2008-02-26
Maybe you people should learn a bit more about how google operates in general:
(scroll down to the numbered points for a jist, more on the rest of the site) 
[http://www.google-watch.org/bigbro.html](http://www.google-watch.org/bigbro.html)

Google certainly wouldn't appear on a share portfolio of ethical companies. 


Matthew: Thanks for answering some questions but I have three more:

1) When the IP on my browser blinks through "google analytics.com" , does that mean it's actually connected to google?

2)If it is actually directed through google, how do you know what the do and collect, apart from just the data they give you?

3) Why do you think "google analytics" is provided free to you?

I don't mind Ubuntu/Canonical collecting operational information but it appears you are donating access to our info to a company whom you have no control over or knowledge of what *they* use it for. Google is a huge  spy-engine, not just a search one.

---

### Post by KiwiNZ on 2008-02-26
> **MarkX said:**
> Maybe you people should learn a bit more about how google operates in general:
(.

With respect , you need to learn how to ask for things in a manner that is more likely to gain results.

Thread closed

---

### Post by matthew on 2008-02-26
I know you have concerns, and I have seen rumors and sites like the one you linked. All I can say is read the info in the Google links. Either they are telling the truth, or they are lying. If they are telling the truth, the rumors and info on sites like you linked to are baseless. If they are lying, we are all screwed whether our forums use Google Analytics or not. This isn't really news. Here are the Google sites where they themselves discuss what they will and won't do with the sorts of data they collect and store.

[http://www.google.com/analytics/tos.html](http://www.google.com/analytics/tos.html)
[http://www.google.com/privacy.html](http://www.google.com/privacy.html)
[http://www.google.com/privacypolicy.html](http://www.google.com/privacypolicy.html)
[http://www.google.com/analytics/](http://www.google.com/analytics/)

> **MarkX said:**
> Matthew: Thanks for answering some questions but I have three more:

1) When the IP on my browser blinks through "google analytics.com" , does that mean it's actually connected to google?Probably.

> **MarkX said:**
>  2)If it is actually directed through google, how do you know what the do and collect, apart from just the data they give you?I only know what the TOS and privacy policy sites above say.

> **MarkX said:**
>  3) Why do you think "google analytics" is provided free to you?Probably both to enhance the search services they already offer, most likely in the hopes of generating better revenues for Google by more accurately targeting search engine users with paid advertisements...which can also be blocked. Cookies can be erased (mine are every time my browser is closed). 

> **MarkX said:**
> I don't mind Ubuntu/Canonical collecting operational information but it appears you are donating access to our info to a company whom you have no control over or knowledge of what *they* use it for. Google is a huge  spy-engine, not just a search one.

None of your concerns are new. Again, either they intend to do what they have stated in the TOS and privacy policy, or they don't. If they are being honest, then there's nothing to worry about. If they aren't, they already know far more about you than you could possibly imagine and the data from this site won't change that. I realize that sounds a little dismissive, either that or incredibly cynical, and I don't intend it either way. I honestly believe the worries here are overblown.

In any case, it's midnight where I live. I need some sleep now.

---

