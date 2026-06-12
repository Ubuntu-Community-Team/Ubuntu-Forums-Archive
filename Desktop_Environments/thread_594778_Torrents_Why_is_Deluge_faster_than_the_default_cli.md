---
title: "Torrents: Why is Deluge faster than the default client?"
date: 2007-10-28
forum: Desktop Environments
---

### Post by keyboardashtray on 2007-10-28
I'm wondering why Deluge is downloading the same file more than 5x faster than the default Bittorrent client.

Last night I spent 13 hours downloading the alternate iso for Xubuntu with the default bittorrent. It was driving me nuts - a lot of the advice on what to tweak gets pretty technical, fooling around with IP tables, router settings, etc.

I'm on Clearwire, 1.5 mb/sec service.

Here is what I've done: I've set the router's port forwarding to an appropriate range of ports outside the default bittorrent zone (in case it was Clearwire throtting the default ports).

I've used the Gnome configuration editor to set the bittorrent client to those ports.

I've enabled those ports on Firestarter.

And still, the default bittorrent ranges from 5 - 25 kb/s download and a generous .1 kb/s upload. Which is the same as it did before I adjusted any of that.

Figuring then that the only possibility was that Clearwire detects torrents and throttles them, I tried Deluge, for the encryption. Today I used the Kubuntu iso. And almost instantly it was capping my bandwidth with 150kb/s. But heres the kicker: I experimented, paused the download, and disabled the encryption, restarted the program, and resumed the download and it still was getting really high speeds. I tried plain Bittorrent again, on the same download, and it was only capping at 25 kb.

I don't get it - what could Deluge be doing that the default client doesn't do? I would like to know for two reasons: One, that I don't plan on using it for music/movies - I'm just looking for something for the occasional large file (like a distribution on release day, learned the hard way there),  just to spare a grassroots server once in a while. And the default client's interface would be just fine for that.

The other reason is I would like to know if it is my ISP's fault, if they do some crooked throttling/etc., that some Deluge setting manages to circumvent (but like I say, I tried turning off encryption and it was still faster). Some sources say Clearwire does, but what other setting in Deluge would workaround that besides encryption?

---

### Post by Mcavity on 2007-10-28
Well i have an idea.
no expert take this with a grain of salt..
but Im researching my own "slow speed problem" and I noticed people have been talking about problems with ipv6 causign things to slow down. 
it vould be that one client is trying to use ipv6 and the other is not. 
maybe try disabeling IPv6?

---

### Post by Wiebelhaus on 2007-10-28
From my simplistic view it's because deluge kicks ***.

---

### Post by keyboardashtray on 2007-10-28
> **Mcavity said:**
> Well i have an idea.
no expert take this with a grain of salt..
but Im researching my own "slow speed problem" and I noticed people have been talking about problems with ipv6 causign things to slow down. 
it vould be that one client is trying to use ipv6 and the other is not. 
maybe try disabeling IPv6?

Yeah, whats the deal with that huh? That ipv6 seems to be the buzz, I did a search on it and there were several current posts (not to mention plenty of old ones).

Well, I gave disabling it a shot and it didn't seem to make a difference for me. I'm now trying the Gobuntu torrent, and default bittorrent still crept along with 20 kb. Deluge, oddly enough,, did worse this round, which is crazy because it burned through the Kubuntu iso. But I've switched back, and Deluge is still going slow with it. I'm going to chalk it up to less people downloading Gobuntu at the moment. I'm not experienced with the torrenting, I'm sure thats the norm that some files just suck.

Maybe sx66gns is right and Deluge just kicks ***, but I'd still like to know what makes it work better.

---

