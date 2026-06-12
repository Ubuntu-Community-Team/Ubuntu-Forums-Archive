---
title: "Major failure - search system"
date: 2014-03-24
forum: Forum Feedback &amp; Help
---

### Post by Ace..... on 2014-03-24
I wanted to check user numbers of a solution I'd posted, in order to verify its relevance, so copied the 'post title' to the search box.
This, we would presume, place the post at the top of the first page, unless another post had the same title.

In fact the post was displayed on page 5 of the results or 124th on the list.

Above it were a whole host of posts totally (I mean completely) unconnected with the subject matter.

Here is the title:

**How to add --disable-bundled-ppapi-flash %U to launch script?**

Around 4,000 people have used it (which is gratifying as the problems it solved were very annoying to say the least)

Can you imagine that above it were titles such as:


[LIST]
[*]HOWTO: CJK in Wine (Chinese, Japanese & Korean)
[*]rtcwake issue and time problems
[*]Questions about best practices in downgrading / pinning
[*]No Grub bootloader. Help!
[/LIST]

I haven't checked every listed post, but it seems like the only valid post to match the search query was hidden away on page 5 (124th).

How is it possible that 'search' can produce such an enormous quantity of astoundingly false results?

---

### Post by coffeecat on 2014-03-25
The vbulletin search function is known to have limitations. You have found one of them. In the situation you describe use this in google:

```
site:ubuntuforums.org "How to add --disable-bundled-ppapi-flash %U to launch script?"
```

One hit - problem solved.

**EDIT:**

I was wrong to say that you have found one of the limitations of the vbulletin search. You were using it wrongly. You were using the thread title as your search. In which case next to the keyword field in the advanced search, choose "search titles only". Try it now with **How to add --disable-bundled-ppapi-flash %U to launch script?**. Then make sure you have Threads, not beans, ticked under "show results as"....

One hit - problem solved. :wink:

---

### Post by Ace..... on 2014-03-26
> **coffeecat said:**
> 
You were using it wrongly. You were using the thread title as your search. In which case next to the keyword field in the advanced search, choose "search titles only". Try it now with **How to add --disable-bundled-ppapi-flash %U to launch script?**. Then make sure you have Threads, not beans, ticked under "show results as"....



Yes .... sure..... but that was not really the point of my post.

While you are obviously correct; and of course I did find the post using 'advanced search'...... this does not alter the fact that I pasted and searched on the 'exact' title.

When one has the 'exact' title, and that title is unique.... should there really be a need to use Advanced Search?
It is certainly counter-intuitive.

And, regardless of that:
The work-around **doesn't explain the weird results that 'standard search' produced**.
Bear in mind that I knew exactly what I was looking for (in this case).

This experience has certainly provided me with a sort of explanation as to why I often struggle with the search service.

But the reason that I posted was to alert the community to what was clearly a major fail; raising the question:
If it fails like this, then surely there is something wrong with the system.

Was it a major fail?
Ie. Did the search go badly wrong?

I would say "124th on the list and and a whole host of what were effectively 'gobbledygook' results, for a document search within the site that holds the document" is a major fail.

I don't know what can be done with this information, other than raise the problem for the community to consider, and assess whether action is required.

I'm just being a responsible community member.:cool:

---

### Post by coffeecat on 2014-03-26
Please read my post again. When you are searching for a thread title, then select "search titles only".

---

### Post by coffeecat on 2014-03-26
Also - the search defaults to a boolean OR with those keywords that it doesn't discard for being too common. So.. with this below as the search, and "search entire posts":

```
disable AND bundled AND ppapi AND launch AND script
```

Two threads are found - the one you were looking for and this one. 

If you want to read up how to use the vbulletin search utility properly, this may help:

[http://www.vbulletin.org/forum/showthread.php?t=253432](http://www.vbulletin.org/forum/showthread.php?t=253432)

---

### Post by Ace..... on 2014-03-26
> **coffeecat said:**
> Please read my post again. When you are searching for a thread title, then select "search titles only".

Sorry coffeecat, it's my fault.
I've failed to explain my point.
I can see that you thought I was in need of help (as is often the case :) ).
In fact the post has only raised 5 views - those probably being yours and mine.

I think we should just let this one pass ;)

Thanks for your interest in this issue.

:cool:

---

### Post by coffeecat on 2014-03-26
> **Ace..... said:**
> I can see that you thought I was in need of help

You do need help. What you were describing is not a defect of the forum search, but the result of you using it incorrectly. In your OP you say:

> In fact the post was displayed on page 5 of the results or 124th on the list.

Above it were a whole host of posts totally (I mean completely) unconnected with the subject matter.

Of course there will be posts unconnected with what you were searching for. And this is why:

> **coffeecat]the search defaults to a boolean OR with those keywords that it doesn't discard for being too common.[/quote]

You had "how to" in your search string. That's why the search came up with a load of howtos unrelated to the one you were looking for. Ditto for the other keywords in your search.

Let me repeat. If you are looking for a thread title, select "search titles only". If you use "search entire posts" you need to use boolean AND, NOT and/or quotes to limit results to those that are relevant to you.

Yes, I did get your point. You thought you were reporting a fault in the search function - for which thanks for your interest. But in fact the case you describe does not reveal any fault in the forum search. Believe me, the inbuilt vbulletin search does cause us the staff much frustration - it does have its limitations, but this is not one them. That is why I sometimes use "site:ubuntuforums.org" in google. However, the forum vbulletin search is more powerful and flexible than a lot of people realise. It simply needs to be used properly. 

[QUOTE=Ace..... said:**
> In fact the post has only raised 5 views - those probably being yours and mine.

Not so. See: [http://ubuntuforums.org/showthread.php?t=2212625](http://ubuntuforums.org/showthread.php?t=2212625)

There is a problem with the view counter that is being looked into. So far 28 forum members have read this thread.

---

### Post by Ace..... on 2014-03-26
I do understand everything you say.
**I've got the concept.**

You've explained perfectly how it works, and this I don't dispute.
And; it's all fine because this is what we've got, so that's that.

However... none of this deals with the core issue that would present itself to a user.
That being that a user will often try to formulate a search query that might match the key elements of interest (regardless of certain words being dropped or emphasised).

And... to be fair... you have not addressed one of the key issues; that being the quantity of totally irrelevant results which appeared
eg. **'Questions about best practices in downgrading / pinning' **(what?) just to name but one (do the search and see for yourself).

Here is the post:
[http://ubuntuforums.org/showthread.php?t=2044987&highlight=add+%25U+launch+script%3F](http://ubuntuforums.org/showthread.php?t=2044987&highlight=add+%25U+launch+script%3F)

I don't see anything in that thread that would put it above my search query.

I guess the same goes for most of the results (but I haven't checked them).

But, apart from all that.
You are still referring to 'me' needing help.
That was not the point of the post.

The post was not about me.... it was about the search system, and other users looking for answers.

I honestly don't know what to say to help you understand the point I'm making.
However, I reckon If you asked 100 people what they thought of 'a search system that put all those weird results above the correct result', then I think you would understand.

But overall, your failure to understand the point I'm raising, is just making me feel crap for raising it in the first place.
This is why I don't wish to continue this discussion, in this vein.

Address the real issue.... or simply say: "that's how it is.... live with it".
I'm fine with that.
Just don't make people feel bad about raising issues on behalf of the community, otherwise they might just stop doing so.
This was not about me.
I simply provided the example.
Take your focus off me, and look at the example.
And then say: "tough titty....that's how it is.... live with it".

I can live with that, and I won't raise the issue again 8-)

---

### Post by SeijiSensei on 2014-03-28
On another vBulletin forum I frequent, the admin replaced the vB search engine with [Sphinx]("http://sphinxsearch.com/").  It's a very impressive search tool that is designed specifically to index materials kept in a database like vBulletin does.  Of course, that required some major surgery on the vB code.

---

### Post by Elfy on 2014-03-28
> **SeijiSensei said:**
> On another vBulletin forum I frequent, the admin replaced the vB search engine with [Sphinx]("http://sphinxsearch.com/").  It's a very impressive search tool that is designed specifically to index materials kept in a database like vBulletin does.  Of course, that required some major surgery on the vB code.

WE have thought about this in the past. It's got no further than that.

---

### Post by Ace..... on 2014-03-28
Thanks for those last 2 posts.
I feel vindicated, in terms of the fact that I was raising an issue that others have attempted to fix.

I personally believe that 'search' is particularly important for Ubuntu forums, because the main body of 'relevant' information is held here.
I say 'particularly' and 'relevant', because windows information is ubiquitous.
There is Ubuntu information out there, but one tends to trust the ubuntu forums.

The saving grace, is that the forums are v.active, so obviating the absolute need for a search engine..... just ask the question again, and somebody will answer it (again).

It is not very efficient, but at least the information is current.
However, there are many people who like to search for answers, before posting a question; further, we are advised to do so.

So let us assume that I'm one of those.
I search and fail.

Hmmm okay - let me search on: 'how to search ubuntu forums'.
What do we get?

Top result is: **Ubuntu Studio or FL Studio?** (what?)
Just do the search and weep.

So even if we ask 'how to search'...... we don't get an answer.

Something is definitely wrong here.... but like, so wrong, it's off the scale.

?

:(

---

### Post by Elfy on 2014-03-28
In the 7 years that I have been using the forum - I've only really ever used the forum search for very specific things - I might know enough of the thread title to search that, or might know the name of the poster and then search for that.

For everything else I use search engines like googlubuntu.

---

### Post by Ace..... on 2014-03-28
Yes; I understand this.
But I do truly believe that the reason people don't use Ubuntu search is because it demonstrably doesn't work.
I actually don'#t know how to configure my search to find the document that will tell me how to configure my search to find a document.

That is just a statement of fact.
I'm not thick.
I've been working with computers since IBM DOS.
Perhaps I should know.... but I don't.

Thank god for the forums eh?
:)

---

### Post by bapoumba on 2014-03-29
I think we used the Sphinx search at some point, and it was really hard to maintain or had other issues. Things may have changed, now, I have not looked. When the advanced search does not get me what I want, I sometimes rely on Google search with site:ubuntuforums.org.
Not recently though.

Edit : [http://ubuntuforums.org/showthread.php?t=1091310&p=6870910#post6870910](http://ubuntuforums.org/showthread.php?t=1091310&p=6870910#post6870910)

---

### Post by Ace..... on 2014-03-30
Yes.... what we have is what we have.
However.... are we helping people to effectively use what we have?

At first base; if we search on 'search' we get nothing helpful - even in help.ubuntu.com

Is it possible to implement a set of rules, so that if a user searches on 'search', that they at least get offered some documents that might help them understand how to use ubuntu search?

If people are at least trying to discover how to use ubuntu search.... is it not reasonable to ensure they are provided with the relevant documents?
Like - top of the list - how to use search to find what you are looking for.
Wow... that would be a well hammered document :)

---

### Post by coffeecat on 2014-03-31
> **Ace..... said:**
> trying to discover how to use ubuntu search.... 

You seem to be labouring under a misapprehension. There is no "Ubuntu search" as such, although Elfy has pointed you to googlubuntu which does a good job of searching for Ubuntu related links. The search utility you are complaining about is the one built into the vbulletin software. Vbulletin is the forum software that we use. That is why you won't find anything in help.ubuntu.com. If anything I find the search in help.ubuntu.com less easy to use than the forum vbulletin one, but I have never complained, merely ascribing my difficulty to having less familiarity with it than with the forum search.

Earlier, I posted a link to a how to search vbulletin effectively. Did you find it useful? Did you read it? Do you think it would be useful to have that linked permanently somewhere in the forum? My small reservation with it is that the date suggests it was written at the time of vbulletin 3. We are using VB4 and there are a few differences in the search but perhaps not as much as to make the link inappropriate.

There is also this:

[http://ubuntuforums.org/faq.php?faq=vb_faq#faq_booleansearching](http://ubuntuforums.org/faq.php?faq=vb_faq#faq_booleansearching)

It's well hidden at the moment, mainly because it's not the most user-friendly set of instructions and it's really only about boolean operators, not a comprehensive guide to the advanced search page. Would you like to see that linked more obviously somewhere? It doesn't spell out how to search for thread titles which was your original complaint - perhaps the vbulletin people think that with "search titles only" as an option in the advanced search it wasn't necessary.

---

### Post by Ace..... on 2014-04-02
> **coffeecat said:**
> You seem to be labouring under a misapprehension. There is no "Ubuntu search" as such, although Elfy has pointed you to googlubuntu which does a good job of searching for Ubuntu related links. The search utility you are complaining about is the one built into the vbulletin software.

To be fair... this is not the case (and as stated before).... in this instance "this is not a 'me' problem" ie. replace 'you' with "a large proportion of the community".
[INDENT][I]IE. Why point 'ME' to google-ubuntu.... I thought this was not about me?
Why not point the entire user base to this search method?[/I][/INDENT]

While I do admit that I wasn't originally aware of the underlying software that runs Ubuntu forums; this changes nothing vis a vis the perspective of a good proportion of the user base.

For those users interested in getting to grips with ubuntu.... they are unlikely to be versed in the ways of vbulletin (and probably have no knowledge of it).
For them it is 'ubuntu search', because its not google, bing, or ask..... and the software type is not stated (er... except in the small print at the bottom of the page).

So it IS ubuntu search - vbulletin search, effectively badged as Ubuntu search.

But all that has got nothing to do with the price of fish.

The real issue is what you touched on, vis a vis:** a user set of instructions, hidden away cos they're not user friendly.**

Well I have to say:

[LIST=1]
[*]A lot of people who wish to try Ubuntu are not thick... and are probably leaning towards being open to thinking about more complex computing scenarios.
In effect: even if the instructions are complex, they must surely be better than nothing.
[*]If linked directly from the search section 'box' or 'advanced page menu', they would certainly be read by vast numbers of people who failed to understand how to use 'Ubuntu search'.
[*]From all those people..... some 'kind & knowledgeable soul' might be prepared to write a user-friendly guide to 'Ubuntu search' (as a replacement).
[*]Your point RE: the vbulletin programmers not giving weight to 'titles' .... OMG perhaps you're right.... imagine all those years when we learned that web docs should be constructed with the primary info contained in the titles (1 -5).
It was a good system that forced you to think about how information should be presented.
Apparently dead & buried.
Sometimes we chuck out the baby with the bath-water.........
[/LIST]

Remember the days when there used to be 'search help'?
It would tell you how to use + - " etc.

Search help has gone out of fashion since google, however the need has not disappeared (at least not for 'vbulletin search'/'ubuntu search').

Really... it's a no-brainer.
With the search results we get; at the very least, we should have a 'search help' document, to help the users of the forum, and to propagate the knowledge that has already been documented.

Not just for me; but for everyone.

;)

---

### Post by Elfy on 2014-04-03
Write one - we'll stick it - or try and link it to the help system if that's possible.

When you've done that - let us know and we'll look it over.

---

### Post by Ace..... on 2014-04-03
> **Elfy said:**
> Write one - we'll stick it - or try and link it to the help system if that's possible.
When you've done that - let us know and we'll look it over.

Speaking for myself, I certainly would, if I could.:p
Helping people on this site, with their problems, certainly makes oneself feel good.
I don't know what chemistry is taking place, but a feeling of good karma pervades afterwards - prolonged, if the assistance is constantly being accessed.
My 're-installation' guide is still being used, so the effort that went into creating it is more than compensated.
Imagine writing the ideal 'search help' doc!
How many people would ultimately be helped (before the system is finally replaced)?

But who is capable.... and...... **is it possible?**

[B]I'm wondering whether the system is actually 'broken' or 'never worked correctly in the first place'...
... but that the fails are passed off as 'known difficulties', ensuring that nobody verifies the system to see if it is actually working as intended.
[/B]
Don't scoff... this is not unheard of - in fact it is a scenario consistent with complexity.
(a few acolytes often stand up to offer blind support, and **usually this is enough** to keep the intelligent class at bay (they are busy with their own stuff, and are happy to hear that innovation x is going well) :neutral: 

How many users have set out to test the search capabilities of vbulletin?

[B]Take for example my 're-installation guide'.
[/B]
Here is a search that worked for me:

**In Advanced** 
**Keywords:** Re-install ubuntu
**Search:** Titles Only
**User Name:** Ace.....

I cheated cos I used my name.
I provide this link so that you can see that the primary keywords were "re-install ubuntu" and they are listed as keywords.

The words are also listed in the title.
The words are also re-stated in the text...
.... I was being uber clever repeating the title in the text, and matching the keywords...
.... this to ensure that with the 'keywords', 'title', and 'message contents' - all covered, I was certain that anybody on the planet searching for this guide would be able to find it.
However, like a plonker; I never checked to see if it would show up in a search (I had thought that you can't do more than what I'd done).

So try entering "re-install ubuntu" into the keyword box on the advanced search page.
We know they are the keywords, the title, and the text - every angle is covered.
One would first automatically choose 'entire post', and one would fail.
Next up 'titles' - again a fail.

At what point do we say "the emperor is not wearing any clothes"?

What more could I have done, as the author, to help the users (who need the information) to find the document?
What more could the user do when they want to 're-install ubuntu'?

Is it possible to write a help doc, that would enable a searcher to find this information?
I'm increasingly doubtful (but somebody can prove me wrong).

Actually, the best move ever; would be to simply replace 'ubuntu search' with google.
I typed  **"How to re-install ubuntu" in google**, and my guide came up 5th on the list (fail cos it should have been 1st) :D 

I guess now we know where all the hits are coming from ;)
Recently I checked the hits for this doc and it was 7,000 - now it is 8,000.
This increase in hits cannot be down to ubuntu search.
**************

So that's the challenge... as a user who is wanting to re-install ubuntu - how do they find a guide (through searching ubuntu).... or more pertinently:
how do they find the list of guides that are relevant to their question/need?
 
However, I would say..... unless you are confident of coming up with a truly universal solution.... don't waste too much time on this challenge.
It really does look like we should be removing the ubuntu search box, and replacing it with a google search box.

I understand that this is heresy, however there is nothing like a big wall of hard facts, to stop you in your tracks.
Others on this thread have suggested using google to search the ubuntu site.
I simply used native google.
If you use:
"site:ubuntuforums.org how to reinstall ubuntu" in the google search box..... my doc is 2nd on the list.

So... for a well prepared document, using keywords, title, and text.... the document is listed 2nd (fine).
bizarrely, the top doc had no effing keywords listed, and 're-install ubuntu' was repeated only once in the text (whereas in my thread it was repeated throughout the thread) - plus his doc has only 470 views ( [http://ubuntuforums.org/search.php?searchid=3048574](http://ubuntuforums.org/search.php?searchid=3048574) ) whereas mine has 8,000 plus :o :D

Clearly, our pre-conceived opinions, on how search should precisely work, may need adjustment.... but also clearly; google search is working well, while ubuntu search is not working at all.

I'm not saying we should necessarily admit defeat (but maybe that is prudent), however I am suggesting that  a 'help doc' may be the wrong path to take.

If vbulletin search is so badly broken (please use stated examples to show otherwise).... perhaps writing a help doc may simply lead the unsuspecting user down a complete dead end (leaving them thinking that it must be 'their fault that they failed' - nightmare scenario). 

_[SIZE=4]**Address the issues:**[/SIZE]_

Can a universal help doc be written, that will ensure that results are relevant to the search (a la google)?
or, if not:
why not create a search box with 'site:ubuntuforums.org ' pre-coded  :?:

---

### Post by Ace..... on 2014-04-17
[[SIZE=3][COLOR=#0000ff]_**Okay.... so here is the 'help document'.**_[/COLOR][/SIZE]]("http://ubuntuforums.org/showthread.php?t=2217540&p=12991059#post12991059")

I've posted it on 'General Help' as that is where it really belongs.

Let's see what reaction is generated.

**What do you think?**

:)

---

