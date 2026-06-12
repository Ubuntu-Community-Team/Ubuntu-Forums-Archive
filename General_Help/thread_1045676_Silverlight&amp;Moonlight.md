---
title: "Silverlight&amp;Moonlight"
date: 2009-01-20
forum: General Help
---

### Post by wubrgamer on 2009-01-20
[http://www.mono-project.com/Moonlight](http://www.mono-project.com/Moonlight)

So what I take from that site is that M$ and Novell are working to open up silverlight for *nix platforms.

Sounds like a good thing.

Will/Does this end the "WE HATE SILVERLIGHT" feelings that much of the *nix community seems to have. (at least from my understanding...)

Discuss.

---

### Post by directhex on 2009-01-21
> **wubrgamer said:**
> Will/Does this end the "WE HATE SILVERLIGHT" feelings that much of the *nix community seems to have. (at least from my understanding...)

No chance.

---

### Post by Vince4Amy on 2009-01-21
It's Microsoft or MS, not M$. And I think this is awesome, well done Microsoft and Novell.

---

### Post by peterthewolf on 2009-01-27
Might be well done but moonlight does not work on ubuntu 8.10 firefox 3.0.5
So TV in uk = 
BBC all works fine with iplayer and a little help from get-iplayer
ITV no joy with their player (moonlight) but get-iplayer will download programs
Channel 4 no joy blatantly says it will only work with MS have not tried get-iplayer.

---

### Post by scouser73 on 2009-01-27
Am I right in assuming that Silverlight/Moonlight is like Adobe Flash?

---

### Post by scouser73 on 2009-01-27
> **scouser73 said:**
> Am I right in assuming that Silverlight/Moonlight is like Adobe Flash?

Nevermind, it seems that Moonlight only works on Ubuntu 8.4 anyway. I'm on 8.10.

[IMG][[IMG]http://img150.imageshack.us/img150/1094/moonlighthj5.th.png[/IMG]](http://img150.imageshack.us/my.php?image=moonlighthj5.png)[/IMG]

---

### Post by mister_k81 on 2009-01-27
Huh?  I'm using Ubuntu 8.10 32bit and the Moonlight plugin works fine for me on Firefox. However, Moonlight isn't compatible with Silverlight 2.0 and is limited to Silverlight 1.0 apps at the moment.

---

### Post by directhex on 2009-01-27
> **scouser73 said:**
> Nevermind, it seems that Moonlight only works on Ubuntu 8.4 anyway. I'm on 8.10.

```
jms@destiny:~$ lsb_release -d
Description:	Ubuntu 8.10
jms@destiny:~$ dpkg -l moonlight-plugin-mozilla | grep ^ii
ii  moonlight-plugin-mozilla                  1.0-1~dhx2                                                 Free Software clone of Silverlight 1.0 - Xulrunner 1.9 plugin
```

---

### Post by mb_webguy on 2009-01-27
> **wubrgamer said:**
> [http://www.mono-project.com/Moonlight](http://www.mono-project.com/Moonlight)

So what I take from that site is that M$ and Novell are working to open up silverlight for *nix platforms.

Sounds like a good thing.

Will/Does this end the "WE HATE SILVERLIGHT" feelings that much of the *nix community seems to have. (at least from my understanding...)

Discuss.
If Microsoft really wanted to open Silverlight up to *nix, then they'd simply release binaries for *nix systems.  After all, how difficult is it to compile a program for a particular platform when you're a multi-billion-dollar corporation?  Heck, they could release the source code, as far as that's concerned.  They're not selling Silverlight, so why should they keep it proprietary unless they're once again using their embrace, extend, and extinguish strategy to try to stake their claim on the web?

Instead they deign to give Novell access to test suites and some licenced codecs, and think we should be thankful.  That's the sort of attitude that resulted in many a monarch being marched to the guillotine. 

So no, I doubt that this "gesture of goodwill" is going to change the attitude of many non-Windows users toward Silverlight.  And keep in mind that this is just as much of a problem for Mac users as it is for those of us in the Linux world.  MacOS also relies on Moonlight to run Silverlight content.

---

### Post by jrusso2 on 2009-01-27
No Microsoft has done the port for OS X.

[http://www.apple.com/downloads/macosx/development_tools/silverlight.html](http://www.apple.com/downloads/macosx/development_tools/silverlight.html)

[http://www.versiontracker.com/dyn/moreinfo/macosx/31433](http://www.versiontracker.com/dyn/moreinfo/macosx/31433)

---

### Post by mb_webguy on 2009-01-28
Ah, I stand corrected.  Though I note that it was just released in October...  Of course, since Mac OS X is Unix-based, it just emphasizes the point that they *could* release Silverlight for Linux, but choose not to do so -- which seems a bit petty since Mac and Linux are roughly equal in popularity [according to W3Schools]("http://www.w3schools.com/browsers/browsers_os.asp").

---

### Post by Gizenshya on 2009-01-28
"W3Schools' log-files over a period of five years"

Thats the dataset from which the information was compiled.  Any first year statistician would immediately blow it off as [invalid](http://en.wikipedia.org/wiki/Validity_(statistics)) for the claim that "Mac and Linux are roughly equal in popularity."  It is very clear that there is no reason to think that the visitors to that tech site are random or representative of the claimed population (which was implied to be the world).  Its also worth noting that this is not what w3schools has claimed it to be.

---

### Post by mb_webguy on 2009-01-28
That's why I said "according to W3Schools" as opposed to leaving the statement open.  If I had said "...since Mac and Linux are [roughly equal in popularity]("http://www.w3schools.com/browsers/browsers_os.asp")", then I would concede your point.  But those stats *do* accurately show the popularity of the various OSes *according to W3Schools*, which is what I said. 

Anyway, those were the first and most referenced of such statistics that I was able to find on a brief (<3mins) search of Google, so those are the ones I went with.  I wasn't going to spend more than a couple of minutes of my time doing research for a forum discussion that isn't trying to solve a problem.

---

### Post by 3rdalbum on 2009-01-28
Moonlight started off as a quick and dirty hack, and it's had lots of little quick and dirty hacks applied to it over time to get specific websites to work with it.

People using Mac OS X on PowerPC-based machines need to use Moonlight as Microsoft hasn't compiled Silverlight for PPC. That's all it needs - a recompile on a PowerPC Mac. Lazy beggers.

---

### Post by directhex on 2009-01-28
> **3rdalbum said:**
> Moonlight started off as a quick and dirty hack, and it's had lots of little quick and dirty hacks applied to it over time to get specific websites to work with it.

People using Mac OS X on PowerPC-based machines need to use Moonlight as Microsoft hasn't compiled Silverlight for PPC. That's all it needs - a recompile on a PowerPC Mac. Lazy beggers.

Silverlight 1.0 is available for PowerPC Mac. It's just, as you say, a recompile.

Silverlight 2.0, however, is NOT. It's not just a recompile. SL2 is based on .NET, SL1 is based on Javascript. So whilst SL1 can just re-use the browser's JS engine, SL2 requires the creation of a PowerPC JITter. Which they COULD do, but it would cost them development and testing time, for a dying subset of a platform which only covers a relatively small percentage of users. Frankly, sounds like just the kind of thing Moonlight SHOULD be supporting

---

### Post by directhex on 2009-01-28
And before I hear it, creating a new JIT isn't trivial work - if it were, OpenJDK would run on more than 7 architectures (out of 16 in Debian). Mono is available for 10 of them, so Moonlight 2.0 should be expected to be available on those 10. Moonlight 1.0 on all of them. Same deal as with SL2, really

---

### Post by Gizenshya on 2009-01-28
> **mb_webguy said:**
> That's why I said "according to W3Schools" as opposed to leaving the statement open.  If I had said "...since Mac and Linux are [roughly equal in popularity]("http://www.w3schools.com/browsers/browsers_os.asp")", then I would concede your point.  But those stats *do* accurately show the popularity of the various OSes *according to W3Schools*, which is what I said. 

Anyway, those were the first and most referenced of such statistics that I was able to find on a brief (<3mins) search of Google, so those are the ones I went with.  I wasn't going to spend more than a couple of minutes of my time doing research for a forum discussion that isn't trying to solve a problem.

First of all, those data are a population, not a statistic.  The population is visitors to their site, and especially since its a specialized site, that population is highly unlikely representative of the population (people who use computers, and are on the internet).  Therefore that population cannot be used as a statistic to describe the population of all people who use computers and are connected to the internet, unless it is shown that people who use that site represent said population.

"according to w3schools" ...

No.  You misread/misunderstood (hopefully not willfully misrepresented...) the data on the w3schools site.  They are not claiming anything about the data,other than it represents visitors to their site.  And using that data out of that context is a good example of a gross misunderstanding of basic statistics principles (or as strong of a propagandist misquote) as I've ever seen.

---

### Post by mb_webguy on 2009-01-28
> **Gizenshya said:**
> First of all [...]

*sigh*  Look, I never represented that data as anything other than what it is.  You have a problem with it only because you read meaning into my statement that wasn't there.  I said "according to W3Schools".  According to *one particular website*.  *Of course* those statistics are only going to apply to visitors to that site.  And since that is a specialist website, the statistics collected by that site will not necessarily be representative of the entire population of the computer-using world.  

Now if the site I had referenced had been a widely popular generalist site, such as Google, then those statistics may very well be quite representative of the general population -- but not if one is to be completely strict about proper statistical sampling procedures, since those numbers would still only apply to people who use Google, which is a subset of people who use the World Wide Web, which is a subset of people who use the Internet, which is a subset of all people who use computers, and therefore cannot be said to be said to be statistically representative of the general population of computer users.  But it is *indicative* of that population.

If I could have found a similar set of statistics from Google or a similar widely used generalist website in my brief search, then I would have.  I *did* find the statistics for W3Schools, and several other pages that referenced the W3Schools stats, so I used those rather than spending an inordinate amount of time looking for something more statistically valid.  I my experience, most people don't care about statistical validity in everyday life, and I didn't want to waste too much of my time doing research on a simple forum discussion post.  I likewise didn't feel it was necessary to go into great detail about how the information in the link I provided was only an anecdotal sample and not necessarily representative of the general population for this same reason.  But by the same token I didn't misrepresent the data and claim it *was* ruggedly valid statistically.  All I said was "according to this website".  I think most people -- at least people who are even slightly net savvy, which most Ubuntu forum users tend to be -- would understand that those stats applied only to that particular website, or at least should not be considered representative of the general computer-using population unless verified by other independent sources.

But then you (Gizenshya) went and questioned my intelligence and/or integrity, and in order to defend my reputation (which is the only thing of value on this otherwise anonymous Internet) I had to waste time writing multiple posts defending a simple innocuous statement because you read meaning into it that was not intended.  I am not a fan of symbolism, allegory, or metaphor -- especially when it comes to the Internet -- precisely because of the risk of miscommunication.  I generally try to mean what I write, write what I mean, and no more.  Please to do not cause me to waste even more of my time because of your own preconceptions and misinterpretations.

By the way, shouldn't this thread be in the Community Cafe?

---

### Post by Gizenshya on 2009-01-28
"But by the same token I didn't misrepresent the data and claim it was ruggedly valid statistically."

True.  I felt that you implied that at first, but you have now elaborated to show that thats not what you meant.

The are several routes for me to take from this point (such as... if you weren't trying to generalize as I thought you were, then why would we care about what OS users who visit that particular site use?).  But everything is one the same page now, and thats all that matters.  I just don't want people drawing invalid conclusions from wordings that might have been a bit too concise.  You have clearly shown, however, that you have a good grasp on statistical reasoning.

Another reason for my reply was to show others about how easily statistics dcan be misunderstood.  I failed in that when I made it more particularly about what I thought your interpretation was, instead of elaborating just on the data.  In retrospect that was neither polite nor constructive.  Sorry about that.

---

### Post by mb_webguy on 2009-01-28
No problem.  I understand how you could have interpreted what I said as you did, even though it *isn't* what I wrote, nor what I intended.

As I said, I try to write what I mean and no more than that, especially on the Internet where lack of verbal and visual cues can easily lead to misunderstandings.  And while I understand you were only trying to point out what you believed to be either a fallacy or attempt at deception, I take my online reputation very seriously, since that's really the only thing that has any worth in an otherwise anonymous community.  So when you called that reputation into question, I felt obliged to defend myself.

But I didn't take it personally.  And now everything's cool.  And by "cool" I mean in the colloquial sense of "all right" -- just so there's no misunderstandings...  ;)

---

### Post by shongzah on 2009-02-15
I have to confess that I believe I have just witnessed a thing unheard of. Two people, on a discussion board, actually disagree, discuss, and come to an amicable ending. I stand open mouthed. If I could, I would applaud you both. <cyber applause> I actually backed up and read the posts that I skipped while thinking, "Stupid flamers." 

I would also like to apologize to anyone that I may have offended by posting off topic.:D

---

