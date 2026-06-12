---
title: "X2GoServer view only for desktop sharing"
date: 2015-05-27
forum: Desktop Environments
---

### Post by bargmann on 2015-05-27
I am looking for a linux solution for screensharing with my team. 
I would like to share my screen in "view mode only" with 10 to 15 people.

I am using X2Go and it works very well. Problem is that the client decides whether it will connect with full control of the server (over mouse and keyboard) or view only.
I could not find in x2go wiki a way to setup **the server** to allow only "view-only" incoming sessions - and it is very odd to me.

Is there a way to configure the server to not allow "full control" client sessions?

Thanks in advance!

---

### Post by TheFu on 2015-05-27
I'm interested in this too for about the same number of viewers for a completely volunteer-run organization that meets monthly.

Mikogo seemed to be the best option outside google-hangouts (which we can't use due to political reasons).  There was an *Ask Ubuntu* question about this with a few other options. All are commercial now. 

In theory, there should be some HTML5-based solutions like [http://deadsimplescreensharing.com/](http://deadsimplescreensharing.com/) soon. Sadly, we cannot use Chrome (same political issue), but perhaps you can?

[https://jitsi.org/Main/HomePage](https://jitsi.org/Main/HomePage) looks interesting. Cross-platform. Can run the entire infrastructure yourself or use existing services - XMPP-based. Sadly, it is java-based. This is the most promising for my needs right now.

[http://www.webrtc.org/](http://www.webrtc.org/) is also encouraging for the future. Just tried to get this working and didn't see anything.

I do use x2go, but never thought it would have a view-only mode.

---

