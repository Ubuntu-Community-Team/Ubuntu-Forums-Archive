---
title: "Firefox and Google spyware?"
date: 2006-05-31
forum: Desktop Environments
---

### Post by panurge77 on 2006-05-31
I just posted this on the Mozilla thread but I think it deserves a thread with a straight name:

The problem with firefox is that it uses google's spyware (at least on windows.. I have not tested it on linux). Mozilla should be free of that. Seamonkey will probably use it too. I'm not sure of that, though.

Well, I did a google search trying to find the page with all the information about that and guess what? Google won't find it anymore ( it was the first link of a 'firefox savvis' search last month, and now Google won't find it, not even if you use the whole page title in the search... looks like google is ignoring pages that criticize them). Yahoo did find it though:

[http://217.115.198.3/content/topic/57686/](http://217.115.198.3/content/topic/57686/)

Yes. I used to be a google/firefox fan. But then I found out Google was buying privileges from ISP's and then this firefox thing. It makes one wonder...

PS: Yes, it's not a very bad spyware. You almost can't notice it. The problem is: firefox misbehaves if your IP blocker block google trackers (it slows down your surfing trying to reach the tracker repeatedly) and it pisses one off having to make enable rules for trackers on your blocker, which is made exactly to block this stuff.

(Am I too paranoid?)

I'm thinking of testing this again with mozilla, firefox and seamonkey and see how differently they behave but I'm actually lazy about having to install peerguardian and all that. 
Maybe someone who's already got everything installed could check that easily?

---

### Post by Or'Enn on 2006-05-31
If this is true I have to seriously reconsider my views on Google and Firefox. No secrecy is good, whatever the reason. Epiphany looks more and more appealing.

---

### Post by SeanTater on 2006-05-31
It's a good thing I use Konqueror..

---

### Post by glotz on 2006-05-31
Guys, go ahead and read the comments. It's BS. And making a claim that an open source app contains spyware is braindead.

---

### Post by panurge77 on 2006-05-31
I just added a few lines above about google not finding that page and I'm now wondering... If google is ignoring a page that criticize it, who else they might be protecting?

---

### Post by bruce89 on 2006-05-31
Download Firefox's source code and have a look then!

---

### Post by Hairy_Palms on 2006-05-31
if u read the comments near the bottem, you see that none of it is actually spying, it turns out the guy was using pages that had google ads down the side, that would be why it was connecting to google ads, funny that...
:rolleyes: :rolleyes: :rolleyes: :rolleyes:

---

### Post by ssam on 2006-05-31
is not just that its connecting to google to download the google adverts? it seems that most page on the web these days have adverts by google. also isn't it possible for page display to be delayed untill various components (ads) are loaded?

all the big interent advert companies use cookies to give you a unique id number, and record which site you see their ads on. then they can make a better guess as to which ads to show you.

i would not be supprised if google were beginning to tie in which pages you look at (that contain google ads), with search results. for example when i search for 'gimp' on google i get [www.gimp.org](www.gimp.org). maybe if i spend all day looking a bondage, then i would get different results.

like one person on that page says someone should investigate this with a packet sniffer (ethereal is a good one).

if you're paranoid browse the web with wget or telnet

---

### Post by Or'Enn on 2006-05-31
*relieved*

---

### Post by lithorus on 2006-05-31
The thing is that the google trackers are indeed being contacted, but how many pages doesn't have an ad which uses the google ad system? Blocking the ip's with a firewall rule which doesn't give a reply back to the browser will surely make alot of pages slow. IE for instance doesn't care much, since it's simply ignore all rules about how tcp/ip *should* work. [http://grotto11.com/blog/slash.html?+1039831658](http://grotto11.com/blog/slash.html?+1039831658)

---

### Post by mannheim on 2006-05-31
ssam and lithorius are surely right. The same point is made further down on the page that the original poster linked to: see the comment there by Ronnie Flow. Slashdot displays google ads; so if you are sufficiently paranoid about conspiracy theories that you choose to block connections to google ... what do you expect?

---

### Post by rcarring on 2006-05-31
I do know that the Search bar in SeaMonkey uses google to search for stuff,  Mozilla loads Debian local page for use by computers not connected to a network, rather than open a customized Google search page.

I use Google as it lets me construct complex search queries and I don't think Yahoo supports this.

---

### Post by SkyNet2029 on 2006-05-31
Like the man said, checking the source code reveals it all.

---

### Post by bruce89 on 2006-05-31
[QUOTE=SkyNet2029]Like the man said, checking the source code reveals it all.[/QUOTE]
Does it?  What file is it in?
Or do you mean it shows there isn't any spyware?

---

### Post by bruce89 on 2006-05-31
I grepped the firefox source code for google and this is what I get.

---

### Post by seanUSXIII on 2006-05-31
[QUOTE=SkyNet2029]Like the man said, checking the source code reveals it all.[/QUOTE]

Wouldn't it be possible then to delete any spy sections of the source and recompile it yourself? That in my opinion would be the true benefit of open source. :-D

---

### Post by moitio on 2006-05-31
You'd think that if an open source project that big with as many users and developers as Firefox has spyware, everyone would know about it. Plus why would an uncommercial company want to extort money out of its users. It doesn't make sense.

There is no spyware in firefox. It's common sense.

---

### Post by bruce89 on 2006-05-31
Looking through the grep, there is nothing wrong, except the search engine plugin being made by amitp+mozilla@google.com

---

### Post by ubnoobie on 2006-05-31
the only thing that's "spyware" about the association between mozilla and google is that google logs and tracks every search. even without the "perma-cookie" from google, they still can log your ip address and track & match you & your searches that way.

this is the case regardless of whether you use the google search box in firefox or go straight to google's web site to conduct the search there.

mozilla has nothing to do with google's tracking & logging, other than that they are helpling google track more searches by making google more prominent in their browsers in exchange for a bit of cash.

---

### Post by glotz on 2006-05-31
[QUOTE=bruce89]Looking through the grep, there is nothing wrong, except the search engine plugin being made by amitp+mozilla@google.com[/QUOTE]
And this is a problem exactly because of...?

---

### Post by bruce89 on 2006-05-31
[QUOTE=glotz]And this is a problem exactly because of...?[/QUOTE]
Nothing, it's the only link I could find that was coded by google.

---

### Post by steve.horsley on 2006-05-31
Google offer a service that gives you stats on you web site - hit count etc. The service is one you have to ask for, and I can't remember the name now. But I have noticed some sites cause your browser to connect to that google service. I guess you just embed a small object from the Google site in your web page. I don't think it's spying, just the web site trying to collect stats. And yes, I believe google's stats give a breakdown of visitors by country and other stuff. I don't have a good example at the moment.

Edit - found google's description of the service: [http://www.google.com/analytics/](http://www.google.com/analytics/)

---

### Post by panurge77 on 2006-05-31
I never thought of looking the code. I found that page in first place trying to find out why was savvis always beeping on peerguardian. Searching for savvis at google led me to that page. I tested a few pages on the browser I had on windows and it looked like firefox made more connections than the other browsers while loading the same pages. Anyway, it's obvious any browser will load the ads on the pages and those pages had google ads. Problem is: is it loading just the ads? Or is it trying to provide extra information to google analytics and related trackers? Your browser history maybe? Anyway, greping code for google might not do the trick, since you don't need to write google on the code, right? You maybe just need to enable some "features" which are not necessary but are easily used by the trackers/ads. Anyway, I did not now firefox was open-source, I thought mozilla was open source and firefox was a commercial branch and that made it all more plausible for me. It's really strange to think about it in open-source. Anyway, History is there to prove money can corrupt almost anything.

---

### Post by bruce89 on 2006-05-31
[QUOTE=panurge77]Anyway, greping code for google might not do the trick, since you don't need to write google on the code, right? [/QUOTE]
The word google would come up if was being sent to their servers.  Of course, they could use the raw IP address.
[QUOTE=panurge77]Anyway, I did not now firefox was open-source, I thought mozilla was open source and firefox was a commercial branch and that made it all more plausible for me.[/QUOTE]
How else could Ubuntu ship it?  If it wasn't open-source, Ubuntu wouldn't touch it.

---

### Post by awaldram on 2006-05-31
install adzapper if your really botherd that'l speed up your browsing

build server install squid proxy and adzapper trust your browsing will realy fly.

then you can set up danguardian and keep the kids safe 

ip table will give you firewall protection and transerant proxying.

Oh I've just described my system cooooool

Happy Dapper Day

---

### Post by panurge77 on 2006-05-31
I dont think you need to code the ip either. It's maybe just something on how it reads the pages. The link to the tracker is probably on the pages. The hipothesis is that the browser is coded to be more 'friendly' with the tracker than one would like.

---

### Post by benuski on 2006-05-31
[QUOTE=panurge77]I dont think you need to code the ip either. It's maybe just something on how it reads the pages. The link to the tracker is probably on the pages. The hipothesis is that the browser is coded to be more 'friendly' with the tracker than one would like.[/QUOTE]

That doesn't really make much sense, in my humble opinion.  If google were to use something in the code of the browser itself to make tracking easier, wouldn't they choose something that could be found in any browser?  I would assume that google would want to get information from more than just 10% of the internet browsing community, a 10% that is more computer savvy than the average internet user.  I would think they would want to find track what the average computer user, the average IE user, would want, because that would end up being more profitable for them.

---

### Post by panurge77 on 2006-05-31
It is also known that google general approach to business is making partners. They won't partnership with MS since they're fighting each other. They made gmail, google-talk, google toolbar, orkut etc. All that is oposed to hotmail, msn messenger, msn toolbar, myspace etc. What's missing here? An IE rival? Now you can say IE is not related to msn and google rival is msn, not MS. But then, firefox comes with google search and IE comes with msn search. Hmmm... Well... Google is just making some fine stuff  and competition is good for everyone. Now MS is gotta make better apps and msn will provide better services and we reap the smiles. But then you try to find a page that was easily found last month and google wont find it anymore. Exactly the page talking bullshit about google and firefox? Why can't google find it anymore? I swear it was very easily found a couple weeks ago. Why would they hide it? I bet they're saving you from reading crap. Then you see google has bowed down to china's internet policy. Of course, they couldn't lose a market that big. Well, maybe they learned something about censorship? Hmm... I bet that does not make sense either. I just love google and I don't care if they track a few clicks to provide me the ads I want to see. I don't care either if they're choosing what I read. :mrgreen:

Extras:
1- Go to google toolbar homepage. Can't you see a firefox link over there?
2- Google analytics link is coded on the header of a page. MS will probably (already has?) copy that. I wont be surprised when people start calling MS names because they're using the page header, loading their stuff before the page you want. When MS trackers start appearing on everybodys browser, will you be smiling?

---

### Post by SyntaxTerror on 2006-05-31
That link to that Hardware analysis sites was the most frustrating read I've ever read.

To think that Spyware would be present in an open source app is the most absurd thing I've ever heard.

Also, this guy is blocking over 2 billion IP addresses?!  That's insane.  What has he got left of the internet?

It's not only a shame that this stuff gets published online, but people spread it on and make the situation worse :(

---

### Post by panurge77 on 2006-05-31
OK, let's not call it spyware. That only happens on windows cruel world. Open source is like marxism, it would never hurt anyone. Just look all those cubans, they're so happy swimming.

PS: I still like better google, firefox and Castro. I just cant say they're still very different from msn, IE and Bush. The main difference is who's holding the power and who's trying to reach it.
PPS: I quit this thread. I hoped someone would check how different browsers were interacting with google trackers. I only pissed off some people and now I'm starting to enjoy it. Shame on me, but I love rethorics. And if by chance someone does get the time and patience and will to test the browsers, send me a PM with the results, and I'll be grateful.

---

