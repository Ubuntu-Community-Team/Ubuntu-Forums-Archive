---
title: "Problems with the forum again :-("
date: 2010-12-10
forum: Forum Feedback &amp; Help
---

### Post by Quackers on 2010-12-10
About 5 or 6 weeks ago I was having bad problems trying to post on the forum and refreshing screens etc. I had a host of "server timeouts" and it became impossible to view the forum.
I am having problems today of a similar nature, though not as extreme.
Refreshing screens is largely unusable. It just sits there with the circle spinning in the tab.
Accessing different sections of the forum is similar too.

I am now on a different system (natty) than I was last time and a different browser version. Both of which have worked faultlessly before today.

I know it's UF that is the problem because other sites work fine - even other forums in other countries.

I have cleared the Firefox cache and disabled ipv6.

Is anybody else having similar problems?
Any advice?

---

### Post by Quackers on 2010-12-10
An update.
Half the time I can't even get back to this forum section at all! This visit took 4 attempts.

---

### Post by coffeecat on 2010-12-10
The forum has been OK for me today. Except for a period around 4-5pm GMT when my broadband slowed right down. I think the hamster in the local exchange needed feeding.

Whatever, have you tried using openDNS to see if there is any difference? It shouldn't do because you can access other forums, but might be worth trying. At least you can get into network manager, which is more than I can do in my Natty atm! :p

---

### Post by Quackers on 2010-12-10
Dude, I wouldn't know where to start :-)
I'm downloading all the updates that broke your Natty and I'm installing them to my 2nd Natty install. I'll be in touch :-)

---

### Post by ajgreeny on 2010-12-10
Could this be a java problem?

I had a few problems with a netbook running openjdk instead of sun-java a while ago when using Mint 10 as a try-out.  That distro was using openjdk, whereas  on my Ubuntu machines I have always used sun-java, and that seemed to make all the difference.

---

### Post by Quackers on 2010-12-10
Thanks ajgreeny for the suggestion.
As it's a testing system, I only use default (or nearly default) packages, so I am using openjdk. It is possibly a problem, but I wouldn't expect it to affect just this site, unless java is used more on this site - is that the case? It would also not explain that the site ran ok yesterday and for weeks before.
But I'm willing to look at anything :-)

---

### Post by coffeecat on 2010-12-10
> **Quackers said:**
> Dude, I wouldn't know where to start :-)

[OpenDNS]("http://www.opendns.com/start/").

Although it invites you to sign up, it shows you the two IP addresses for their DNS servers at the bottom of the page. You simply use them instead of your ISP DNS servers. You can either do this in your router or by using network manager. From memory - since I can't get into nm in Natty :( - you right-click on the nm applet > edit connections > find your connection > edit (or something) and... You're on your own now. It's all fairly obvious. :)

I've used openDNS in the past when my own ISP's DNS servers went on a prolonged go-slow.

**Edit:** just seen your reply to ajgreeny. No, I'm on my half-broken Natty with openjdk and this site is OK for me.

---

### Post by Quackers on 2010-12-10
Thanks for that too coffeecat. I'll mosey on over there :-)

---

### Post by cariboo on 2010-12-10
I have the same problem around 23:00 UTC to 00:00 UTC on a regular basis, I just go do something else for a while. Local time thats 15:00 PST - 16:00 PST, which is when a lot of kids are getting home from school.

---

### Post by Quackers on 2010-12-10
Well, I gave up.
I booted Win 7  and am now trying IE8 or 9 whatever and things are not perfect but definitely more stable. Must be a Firefox thing methinks. 
Thanks for the suggestions and help people :-)

---

### Post by mc4man on 2010-12-11
> Is anybody else having similar problems?
Was seeing pretty much the same and some - (some sub forums where I had threads w/ previous posts was getting info on left side as to number of posts in thread, date of last post, ect.

Installed chrome which had no issues, so was also thinking firefox(4) issue till I noticed I wasn't logged in with chrome. (use the remember me with firefox

So opening firefox, opening main page, logging out, then logging back in has resolved all firefox issues with this forum.( atm.

---

### Post by Quackers on 2010-12-11
Thanks for that mc4man.
I'm still having some of the slowness behaviour. Sometimes I give up and close the sites window and log back in and try again. This fixes it for about 10 minutes then it's back again. Very annoying at times.
I'll see how things go tomorrow. Maybe I should give chrome a go :-)

---

### Post by mc4man on 2010-12-11
> This fixes it for about 10 minutes then it's back again. Very annoying at times.
I'll see how things go tomorrow. 
Pretty much mirroring that here... took 3 tries to post this. No evident rhythm or reason as of yet.

---

### Post by Lucradia on 2010-12-11
Around 5 AM Eastern, it gets annoying at times.

---

### Post by coffeecat on 2010-12-11
Now I'm getting it. For the last half hour or so, it was timing out completely. For the last minute or so it has been snappy and just now I've had to click on the reply button a couple of times to be able to get the message field. Let's see whether it actually posts or not.

---

### Post by Quackers on 2010-12-11
It's spreading I see! Are you using Firefox as well coffeecat? I tried IE overnight and although it was much better, it still wasn't perfect.

---

### Post by coffeecat on 2010-12-11
> **Quackers said:**
> It's spreading I see! Are you using Firefox as well coffeecat? I tried IE overnight and although it was much better, it still wasn't perfect.

Firefox in Ubuntu. I had issues for another half-hour after I last posted in this thread and then it seems to have cleared up again. I tried openDNS myself and it didn't make a jot of difference. It's been OK for me for some hours now.

Famous last words. Tempting fate, and all that. :|

---

### Post by Quackers on 2010-12-11
Lol. It's definitely a little better so far today but it still struggles to change forum sometimes. Also refreshing screens is very hit and miss. 
What I have noticed actually sounds ridiculous. If I change forum section or refresh a screen it seems to have a much better chance of working normally if I move the scroll wheel. If I don't, about 50% of the time the screen just hangs with the spinning circly thing in the tab. If I move the scroll wheel I would say 75% of screens refresh ok.
Maybe I'm just going mad though.

---

### Post by coffeecat on 2010-12-11
For the brief period it was playing up for me I found this helpful. If I was left with the swirling orange thingey (in Firefox 4.0beta) and nothing happening, I would hit ESC and often the screen would go blank. Then I would click on the address bar to get the cursor there and press enter. After which, more often than not, I would go straight to the requested page.

One time I was trying to post and the thing hung completely. I couldn't get anywhere. So as not to lose my post,  I copied and saved my text. I managed to get back to the thread eventually to find my post had been added. I wonder if there is an intermittent forum database issue which would explain the occasional rash of double-posts and double-threads (sometimes triple) that we've seen recently. Only it seems to be affecting you all the time and the rest of us some of the time.

Can you prevail upon a friend or neighbour to try their broadband connection? So long as they have a different ISP. At least that way you can exclude or confirm some weird ISP caching issue

---

### Post by Quackers on 2010-12-11
I hear you cc.
I wrote a reply to a thread last night. It took about 15 seconds or so after clicking on submit post for the screen to clear. When I looked again my post was in the thread. When I returned to the main forum page my reply wasn't listed. Ok, I thought, no problem, that happens sometimes. After viewing other pages I returned and it was still not showing my last post. I clicked on the thread again and viewed my post - except it wasn't there! It had been there, but now it wasn't. I reported this to make sure that it had not been removed for some reason. Cariboo907 kindly replied and said that there was no trace of my post and no other Mod. had removed it.
Very odd.
It may point to a database problem of some kind, but I don't know anything about that kind of thing.

With regard to the ISP, I really can't see any benefit boss. I can post ok in other forums which are based in the UK and in the States without any of these problems. The problems only arise on UF.
Scratching my head :-)

---

### Post by coffeecat on 2010-12-11
> **Quackers said:**
> With regard to the ISP, I really can't see any benefit boss.

Tbh, I wouldn't know, but I've seen it suggested. Anyway, I'm now back on line after my ISP collapsed for a couple of hours. To give them credit they got a message on their 0845 status line quickly and have now resolved it. :fingers_crossed:

---

### Post by Quackers on 2010-12-11
I'm still having similar problems, but only with FF in UF. All other sites/forums are fine :-(

---

### Post by lisati on 2010-12-11
/me ponders reflectively: I had a couple of issues in the last 24 hours which I initially put down to quirks in my setup at home. (FF 3.6.13, Ubuntu 9.10, squid proxy, blah blah blah other possibly irrelevant info)

---

### Post by Quackers on 2010-12-11
I've tried no proxy at all and re-enabling ipv6 (which gave a small increase in usability) but I've thrown in the towel with FF for the moment. In desperation I am now using Chromium for UF and  although it seems a bit basic, it is much quicker and more stable when in UF. Not one stuck swirling swirly thing yet! Screen refreshing is much quicker and the whole feel is noticably snappier. At least for the moment :-)

---

### Post by coffeecat on 2010-12-12
One last throw of the ideas dice. Quite frequently I am afflicted with the can't login issue which crops up from time to time in this subforum. I login, the forum says, "Thank you for logging in, coffeecat," I'm returned to the forum page, but I'm not logged in. I try again. The same happens. And again. And again...

I've tried various combinations of repeatedly trying to log in, refreshing the page, clearing cookies and restarting the browser, all with unpredictable results. More often than not, trying to log in again fails. Since it seems to affect only a minority of members, it's fair to say it could be a cookie issue. (Tried eating some - didn't help either.)

What I find works most of the time now when login fails is to open the Preferences window and delete the Ubuntu forums cookies only. Look for them all. I've got 'ubuntu-ky.ubuntuforums.org as well as ubuntuforums.org at the moment; goodness knows why. Then I do a single page refresh of the main page before logging in and then I log in, usually successfully. Assuming this could be a cookie problem your end, give this a try.

---

### Post by Quackers on 2010-12-12
I just had ubuntuforums cookies so I deleted them. When I tried to post this it wouldn't let me :-) It said I needed to log in but I was logged in. Nevermind I refreshed and logged in. I'm testing now :-)

---

### Post by Quackers on 2010-12-12
I'm not noticing a huge difference. It's curious that it's just happened for the last couple of days. Chromium is definitely better.

---

### Post by coffeecat on 2010-12-12
Actually, I do have a last suggestion. It's from the seriously weird department, but it must have a logical explanation. If you don't have a N-capable router, read no further, unless you're a connoisseur of weird.

I have a 802.11N router but I had configured it to G because I had been using an older G USB dongle with my desktop. When I switched back to wired for the desktop I re-configured the router back to N speed because both my laptops have N-capable wireless chips - an Intel in the Sony and an Atheros in the Acer. The Acer/Atheros connected just fine - I was using either Maverick or Lucid - and I managed to surf the internet just fine. Logged into Ubuntuforums - no problem - and looked at various threads. Then I tried to post. I clicked on 'Submit reply' and waited, and waited and waited.... I could do anything but post or preview post. All other sites with the exception of Yahoo seemed fine - it wouldn't render properly - and I could post on another forum. Thinking it was a forum issue I shut down and, later, booted into Windows 7 (on the Acer) and was able to post here OK. When I next booted up Ubuntu I wasn't able to post again.

Long story short: with the router on the N setting and using Ubuntu and Firefox I could do everything I tried on the internet except post to UF and view Yahoo properly. With the router on the G setting I had no problem.

Question: how can an issue that is clearly between the Linux Atheros driver and my router set on N affect my ability to post in this forum, when it doesn't affect my ability to surf the forum?

Answers on a postcard please. :-k

---

### Post by Quackers on 2010-12-12
I do have an N compatible wireless card, but I have no idea whether it is being used in that mode :-)

---

