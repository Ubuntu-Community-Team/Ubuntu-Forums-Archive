---
title: "Evolution, mono, patents contamination"
date: 2009-03-25
forum: General Help
---

### Post by HowardJZ on 2009-03-25
How to get rid of Evolution?

Here's the problem:
Several colleagues use Evolution for syncing their address books with their handheld device (Palm). They all use Thunderbird for email. So, no other reason exists to use Evolution.

Given the problems with Novell and Microsoft, patents, helping Microsoft destroy Linux, I need to find another application suitable for an address book application that will sync with a Palm device.

Suggestions, please.

Related: There are some threads related to mono's tight integration in Ubuntu and the dissatisfaction with this. Is there any meaningful effort, plan, intent to get mono and related patent encumbered Microsoft stuff removed from Ubuntu?

---

### Post by directhex on 2009-03-25
> **HowardJZ said:**
> How to get rid of Evolution?

Here's the problem:
Several colleagues use Evolution for syncing their address books with their handheld device (Palm). They all use Thunderbird for email. So, no other reason exists to use Evolution.

Given the problems with Novell and Microsoft, patents, helping Microsoft destroy Linux, I need to find another application suitable for an address book application that will sync with a Palm device.

Suggestions, please.

The old jpilot or kpilot apps? A bit long in the tooth, but that's what they were designed for

> Related: There are some threads related to mono's tight integration in Ubuntu and the dissatisfaction with this. Is there any meaningful effort, plan, intent to get mono and related patent encumbered Microsoft stuff removed from Ubuntu?

Those threads can generally be traced back to a FUD site that makes up stories to get Google ad money. There was one blueprint filed with zero worthwhile technical content on removing Mono from base Ubuntu installs, and it wasn't given the time of day by a single relevant Ubuntu developer - Canonical has absolutely no concerns about Mono.

---

### Post by neighborlee on 2009-05-24
> **HowardJZ said:**
> How to get rid of Evolution?

Here's the problem:
Several colleagues use Evolution for syncing their address books with their handheld device (Palm). They all use Thunderbird for email. So, no other reason exists to use Evolution.

Given the problems with Novell and Microsoft, patents, helping Microsoft destroy Linux, I need to find another application suitable for an address book application that will sync with a Palm device.

Suggestions, please.

Related: There are some threads related to mono's tight integration in Ubuntu and the dissatisfaction with this. Is there any meaningful effort, plan, intent to get mono and related patent encumbered Microsoft stuff removed from Ubuntu?

You  are only getting ONE side of the story..here is the other one:

[http://www.groklaw.net/article.php?story=20080528133529454](http://www.groklaw.net/article.php?story=20080528133529454)

Please read that in its entirety if you can and then come to your own conclusion, based on what you decide, not based on what others ubuntu users tell you in regard to what is FUD and what isn't FUD.

cheers , and if you have any questions reply here..or  if you like also feel free to come to:

irc.freenode.net, on channel #boycottnovell, where you will find people willing to discuss with you these issues. YOu may not have much luck on ubuntu forums , but thats up to you. Just remember in life we get one side of the story sometimes, and its not always the correct one,- its up to you to do some possible homework and decide . Things aren't always as they seem, remember that, which applies to good journalism not just distros ;)

We are all able to make choices, its America, land of the free and home of the brave, or so last time I checked,-  so there you go ;)

cheers
nl

---

### Post by alternatealias on 2009-06-02
As far as I'm aware, the "evil Novell" has given Evolution to the community (i.e. they no longer require copyright assignment of patches) and the current Evolution Mail maintainer, Matthew Barnes, appears to be from Red Hat. The addressbook maintainer appears to be from OpenedHand (which I think got bought by Intel recently?).

Clearly such charity to the Free Software community reeks of evilness. Only evil companies would do such a thing!

---

### Post by Benanov on 2009-06-02
Evolution seems to be harder to remove (I saw a message on the gNewSense mailing list that says it was tough to remove without breakin' stuff.)


If you'd like to remove mono:

You can remove mono by removing libmono0. This is the root library all .NET applications require. Remove this package and you'll be prompted to remove all packages that depend upon it as well.

For the record, I remove Mono from all my Ubuntu machines mainly to reduce installed footprint. I also have not found a slower Photo Manager than F-Spot. (I run older computers; fastest is a P3-850.) It took noticeably longer in 8.04 to transform and display images than gThumb. gThumb also imports images quite well.
(8.10/9.04 may change things, YMMV, etc.)

There are many other reasons to remove mono, but for now they are simply speculation as opposed to definite policy, and nothing has come of them.

Someone had a good Tomboy replacement; I forget what it was. You should be able to find something digging in Synaptic; post it here once you do.

--BK

---

### Post by directhex on 2009-06-02
> **Benanov said:**
> You can remove mono by removing libmono0. This is the root library all .NET applications require.

TECHNICALLY that's not correct. However, in practical terms, it happens that way on Jaunty and below. The libmono0 package contains a library called libMonoPosixHelper.so which almost all Mono apps people use require (as it's required for Linux-style Internationalization support).

mono-common is a better target. Or mono-runtime on Karmic+

---

### Post by jeremy on 2009-06-09
> **Benanov said:**
> 
Someone had a good Tomboy replacement; I forget what it was. You should be able to find something digging in Synaptic; post it here once you do.

--BK

gnote repo:

[http://ppa.launchpad.net/gnote/ppa/ubuntu](http://ppa.launchpad.net/gnote/ppa/ubuntu) jaunty main

---

### Post by adrianx on 2009-06-09
Apparently, from Fedora 12 onwards, Mono apps will no longer be included in live media:

[http://www.theopensourcerer.com/2009/06/02/redhatfedora-drops-mono/](http://www.theopensourcerer.com/2009/06/02/redhatfedora-drops-mono/)

They will, however, still be available in the repos.

---

### Post by knopper67 on 2009-06-11
Regarding Tomboy alternatives:

I'm in the process of creating a note-taking application. It's written in python and I'm aiming to make it better than tomboy (or gnote for that matter). 

It's far from finished, but I just thought I'd mention it anyway...:popcorn:

---

### Post by jeremy on 2009-10-21
> **knopper67 said:**
> Regarding Tomboy alternatives:

I'm in the process of creating a note-taking application. It's written in python and I'm aiming to make it better than tomboy (or gnote for that matter). 

It's far from finished, but I just thought I'd mention it anyway...:popcorn:
That sounds good, how is it shaping up?

---

