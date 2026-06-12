---
title: "Link from Ubuntu Help Pages broken"
date: 2009-04-18
forum: General Help
---

### Post by Poetaster on 2009-04-18
Two related points

1. Clicking on the question mark on the top panel opens the Ubuntu Help Centre.  Typing in a search query brings up a list of possible topics.  At the bottom of the page is an invitation to "Repeat the search online at the Ubuntu Help Pages".  Doing so results in an error 404: URL /help not found.

This looks disastrously bad.  Please look at things from the new user's point of view.  It does not matter that help is available elsewhere.  The new user does not know this - and should not have to trawl round trying to fix his or her problem.

2. There are several discrete sources of help, with too little guidance on which one is appropriate.  Each one may be good in itself, but they overlap on the topics covered and serve different audiences.  They are good if you already know what you are looking for, but seem terribly fragmented if you do not.

I suggest that what is needed is a single point of entry to all Ubuntu help, with links onward, preferably in the location that the Help Centre link points to.  There is good documentation out there, but it is not easy to find.  Besides, what help is offered can be misleading.  For example, the online help facility in Firefox goes straight into Launchpad, yet this is supposed to be for people who are technically skilled.

It is a muddle.  I find it a muddle, being new to Ubuntu, despite having years of IT experience.  How is an intelligent but inexperienced office worker supposed to wade through it?  Yet if Ubuntu is to succeed in the wider world, this is what is required.

---

### Post by zvacet on 2009-04-18
Did you tried again?I ask you because I just try and it worked for me.

> It is a muddle. I find it a muddle, being new to Ubuntu, despite having years of IT experience. How is an intelligent but inexperienced office worker supposed to wade through it?

It is not that bad.Any new Ubuntu user will go to the Ubuntu main page(I suppose they downloaded Ubuntu from there.).There you have all explanations and links how to get help.As extra help you can use [Ubuntu search engine.]("http://www.google.com/search?client=opera&rls=en&q=ubuntu+search+engine&sourceid=opera&ie=utf-8&oe=utf-8")

---

### Post by Poetaster on 2009-04-19
Zvacet,

Concerning your rather surprising first point, that the link works for you, my system generates the following request in the browser:

  [http://search.ubuntu.com/help?os=ubuntu&ver=8.04&q=evolution](http://search.ubuntu.com/help?os=ubuntu&ver=8.04&q=evolution)

but search.ubuntu.com/help does not exist.

I am running 8.10, almost up to date, so "ver=8.04" looks odd.  Nevertheless, my main point stands: the primary point of entry to online help is broken.

---

### Post by spiderbatdad on 2009-04-19
Dear Poetaster,
the help system was much the same when I installed Ubuntu for the first time several years ago. I was new and as green to linux as one can be, however I never had any trouble finding the many resources available to new user.
I propose your premise is flawed. Fell free to join the help wiki community and contribute your ideas. This isn't the right place to complain, nor to make suggestions for improvements to the help system.

---

### Post by kostkon on 2009-04-19
> **Poetaster said:**
> Two related points

1. Clicking on the question mark on the top panel opens the Ubuntu Help Centre.  Typing in a search query brings up a list of possible topics.  At the bottom of the page is an invitation to "Repeat the search online at the Ubuntu Help Pages".  Doing so results in an error 404: URL /help not found.
This looks disastrously bad.
Then, you could fill an appropriate bug report [here]("https://bugs.launchpad.net/ubuntu-doc"), if you want.
> **Poetaster said:**
> Please look at things from the new user's point of view.  It does not matter that help is available elsewhere.  The new user does not know this - and should not have to trawl round trying to fix his or her problem.
This is just a support forum, not the right place for suggestions, I think. There are other venues you can use for that. EDIT: for example, use the [*Ubuntu Brainstorm*]("http://brainstorm.ubuntu.com/").
> **Poetaster said:**
> I suggest that what is needed is a single point of entry to all Ubuntu help, with links onward, preferably in the location that the Help Centre link points to.  There is good documentation out there, but it is not easy to find.  Besides, what help is offered can be misleading.  For example, the online help facility in Firefox goes straight into Launchpad, yet this is supposed to be for people who are technically skilled.
I think *help.ubuntu.com* more or less covers that. It offers links to the official and community contributed documentation.

---

### Post by Rocket2DMn on 2009-04-19
Actually, the bug report should be filed under the ubuntu-docs package [here]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs"), ubuntu-doc is the "upstream" location, but the doc-team wants all bugs filed under the package.

---

### Post by kostkon on 2009-04-20
> **Rocket2DMn said:**
> Actually, the bug report should be filed under the ubuntu-docs package [here]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-docs"), ubuntu-doc is the "upstream" location, but the doc-team wants all bugs filed under the package.
OK, thanks for the info.

---

### Post by coffeecat on 2009-04-20
Having versions 8.04, 8.10 and 9.04 on separate partitions on this multiboot, I can confirm Poetaster's finding, including the fact that it is searching with 'ver=8.04' in all three versions. So how zvacet got a valid link, I do not understand. [http://search.ubuntu.com/](http://search.ubuntu.com/) is a valid url, so perhaps the problem is there, but it's unfortunate that Intrepid and Jaunty are searching for Hardy stuff.

**Poetaster**, although your finding is valid and important, I find your tone overly critical and negative. User-friendliness in an OS is important, but you seem to be as unfamiliar with the Open-Source culture as you are with an Open Source OS. Microsoft and Apple have huge budgets to throw at research into the customer interface. They need to, to survive. The big money in Linux is with the Enterprise market, with the emphasis on server software. For the rest, the developers rely (need to rely) on feedback from the community - which now includes you.

You have now had the benefit of trying Ubuntu with all the software that comes as default, and all the huge range of excellent software that is available in the repositories. How much did this cost you? How much would the equivalent cost in the Microsoft or Apple world? Now that you have tried Ubuntu and have posted on this forum you owe that community something back in return. Since you have discovered this bug, please consider posting a bug report. That would be a good start in contributing something yourself.

> **Poetaster said:**
> Please look at things from the new user's point of view.

I'll emphasise what others have said. The members of this forum are mostly end-users like yourself. You are addressing the wrong people. However, many of us do contribute back, some financially, some by testing Alpha and Beta releases looking for bugs, some in other ways. I very much hope you stay around to gain experience and make your own contribution in your own way.

Good luck.

---

### Post by Poetaster on 2009-04-21
Thank you to those who responded to my posting.  I have submitted a bug report as specified by Rocket2DMn.

I see why I have caused problems.  I find to my surprise that I did not give the context for my remarks, and they do not make sense without them.  My apologies.

Coffeecat, in particular, has reproved me with courtesy and deserves an answer.

We are talking about two different cultures.  Ubuntu and the free software movement in general have many splendid features, and I very much hope they succeed.  The community and the tools it has developed are impressive.  Some of its products are amazing (I still can't believe the on-line updating); some, less so.

I was thinking of another culture.  I have experience in academia, science and the civil service up to inter-governmental level.  I have a pretty good idea of the attitudes of influential users in mainly medium-sized organisations - not, of course, that I am the only one who has, but I have been around the block a few times!  

If you want Ubuntu to be used in these environments, it has to pass what I might call the PA test.  The actual decision-maker will be a senior secretary or PA, who will be highly accomplished, highly efficient and above all, busy.  Time is far more important than money.  If she tries Ubuntu and it does everything - everything - crisply and clearly, she may suggest giving it a try.  If not, it is out.  Harsh?  Yes, but that is the way it is.

So, given that context, when I say that I found the help system a muddle, I did not mean that I could not understand it.  Of course I could, as I have done for many other systems before - but it would take me an hour or two.  When I looked at it with my mind absorbed in something else, as my PA would, I found it wanting.  

Thus when coffepot asks if I do not think Ubuntu a bargain compared with MS, in this frame of reference I answer no (so far).  I have run into several significant problems in only a few weeks.  When I factor in the time it has taken me to sort them out, the deal is not such a good one.  If you are a hobbyist, this is not a problem.  In business, it is.

On the particular point of the help system, could I do better?  Yes, I think so - in outline, anyway.  At least I might bring a different perspective.  I do not envisage any fancy or expensive reworking of the interface, just a gathering together of sources of information for the PA in one or at most two screens.  She must find what she needs in about 30 seconds - or 60 seconds at most.  It should not take more than a few hours to write.

So I accept your challenge, coffeecat.  I am prepared to flesh out these ideas and give a sketch of what I think this presentation of information should look like.  (I do not promise to do it immediately, because I shall have to root around first, but I shall do it.)  I hope it will be useful in the long run, even if it should not be implemented in the way I suggest.  (There may be good reasons why it is not as simple as I think.)

It comes down to what you want, which is not for me to decide.  What I can do is to point out what you need to do to succeed more widely in certain organisations that I know well, if that is your wish.

I accept that this is not the place for any further contributions, so I shall direct them elsewhere.  (But my original point was rather that I did not know where to go ...!)

Again my (puzzled) apologies for the lack of context.  I normally write using a text editor, but I usually proofread on paper.  I do find writing to screen only is psychologically different, but I have never come across any studies explaining why.  (Any pointers?)

Thank you for the exchange of ideas.  I have learned from it.

---

### Post by coffeecat on 2009-04-21
**Poetaster**, thank you for your courteous and thoughtful response. It's late where I am and I must retire soon, but I would like to make an immediate reply, and it will be short perforce. I will think on what you have said and will add to this if I have any more to say.

In fact I very much agree with your point about fragmented help information. It's an inevitable side effect of open source culture, unfortunately. Everyone with an opinion is entitled to publish a howto, set up a webpage or even produce their own distro. And many do with great variation in quality. Which doesn't excuse fragmentation in "official" documentation, but does explain why many new users get confused by the often misleading but seemingly authoritative information that is floating around.

If you wish to address yourself to Ubuntu in particular, you need to explore the excellent documentation that already exists. In case you are not aware of these, here are a few links:

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

[https://wiki.ubuntu.com/Home?action=show&redirect=FrontPage](https://wiki.ubuntu.com/Home?action=show&redirect=FrontPage)

[http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page) (not an "official" Ubuntu source)

And of course:

[http://www.ubuntu.com/](http://www.ubuntu.com/)

All of which bears your point out.

As far as where to direct your contribution goes, I suppose this needs to be somewhere in Canonical (the company behind Ubuntu), or even to Mark Shuttleworth himself. No doubt others will have views.

I wish you well.

**Edit:** actually there is one thing I will add, and again it reinforces your point about the accessibility of help. With those first two links there is a **huge** amount of useful information lurking behind those rather (to my eyes) offputting front pages. If you know what to put in the search field, that's fine. If not, well...

Over to you. :wink:

---

