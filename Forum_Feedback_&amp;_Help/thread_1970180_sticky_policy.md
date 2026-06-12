---
title: "sticky policy"
date: 2012-04-30
forum: Forum Feedback &amp; Help
---

### Post by Kevin McCready on 2012-04-30
Do we have a policy on stickies? eg if a title search finds more than so many hits, should that encourage us to have a sticky. Or could we have a longer page of stickies, instead of the few currently there.

I raise this because it has taken me much much effort to learn out to turn off my touchpad permanently. There were well over 250 hits when I did a title search for "disable touchpad permanently"

BTW the soln is:
create a file  
sudo leafpad /etc/modprobe.d/blacklist-touchpad.conf
add: 
blacklist psmouse
save. Reboot.

turn on touchpad again:
sudo modprobe -r psmouse
turn off touchpad:
sudo modprobe psmouse

---

### Post by bodhi.zazen on 2012-04-30
> **Kevin McCready said:**
> Do we have a policy on stickies? eg if a title search finds more than so many hits, should that encourage us to have a sticky. Or could we have a longer page of stickies, instead of the few currently there.

I raise this because it has taken me much much effort to learn out to turn off my touchpad permanently. There were well over 250 hits when I did a title search for "disable touchpad permanently"

BTW the soln is:
create a file  
sudo leafpad /etc/modprobe.d/blacklist-touchpad.conf
add: 
blacklist psmouse
save. Reboot.

turn on touchpad again:
sudo modprobe -r psmouse
turn off touchpad:
sudo modprobe psmouse

The staff places threads we consider of interest to the community as stickies.

In your case, that solution is quite esorteric.

My suggestion would be to encourage people to maintain the Ubuntu wiki. I think we should consolidate the information in one location.

It would help if you would contribute by posting that information, the wiki is community maintained.

---

### Post by Kevin McCready on 2012-05-03
I merely gave the example. My question remains. What about a sticky policy along the lines I suggest, ie when searches reach a certain number, isn't that an indication that people are having difficulty?

---

### Post by bodhi.zazen on 2012-05-04
> **Kevin McCready said:**
> I merely gave the example. My question remains. What about a sticky policy along the lines I suggest, ie when searches reach a certain number, isn't that an indication that people are having difficulty?

I do not understand how you would envision such a policy. We are a busy forums, and so we would have to have a very  high threshold, or everything would be a sticky. We have many popular threads in the support, security, cafe, etc.

Plus search terms are very non-specific. "Upgrade problems" for example are going to yield a large number of threads across a large number of releases with a varied set of problems. 

How would you go through such a list and identify information that most users should read ?

I think your question is best solved by asking the community to maintain the community wiki pages. You then search the wiki for technical information, and use the forums for questions and debugging.

We sort of use tags to identify popular topics the way you envision stickies. Take a look at the tags and see if they help you.

You are of course free to suggest a sticky if you come across an appropriate thread.

---

### Post by Kiltapps Mikael on 2012-05-12
At least I now have a vague notion of what a "sticky" is.

---

### Post by Kevin McCready on 2012-05-14
You'd have sticky on "upgrade problems". You'd be able to do an advanced search for stickies only. Someone would have done a nice sticky on "upgrade problems" and stickies for whatever reaches a threshold number of search. My latest problem now is having to shut down the whole computer each time the router is rebooted. I'm sure there's a nice terminal command but I'm damned if I can find it.

---

### Post by Kevin McCready on 2012-06-21
I've since seen more threads asking for better way to search for the gems that are here among the dross. (Hope that doesn't mix metaphors but since switching to Linux I miss my onboard Complete Oxford English Dictionary)

Anyway, I can't see why my suggestion (as modified in this discussion) isn't a goer?

---

### Post by bodhi.zazen on 2012-06-21
Best thing to do is to migrate the gems to the wiki.

[https://blueprints.launchpad.net/ubuntu/+spec/ubuntuforums2ubuntuwiki](https://blueprints.launchpad.net/ubuntu/+spec/ubuntuforums2ubuntuwiki)

Join us on irc if you wish to discuss it.

---

### Post by Dave_L on 2012-06-22
Maybe a wiki page could be added that lists solutions to the most common problems, unless such a page already exists.

---

### Post by Elfy on 2012-06-22
> **Dave_L said:**
> Maybe a wiki page could be added that lists solutions to the most common problems, unless such a page already exists.

As far as I am aware there is not one. 

There's nothing to stop anyone starting one and then the rest of the community can add things - if there was one I'd be happy to keep an eye on it :)

---

### Post by Dave_L on 2012-06-22
I assume this is the wiki? [http://wiki.ubuntu.com/](http://wiki.ubuntu.com/)

I couldn't find a link to it here.

Where would you suggest hooking in a page with solutions to the most common problems? On the front page?

---

### Post by cariboo on 2012-06-22
> **Dave_L said:**
> I assume this is the wiki? [http://wiki.ubuntu.com/](http://wiki.ubuntu.com/)

I couldn't find a link to it here.

Where would you suggest hooking in a page with solutions to the most common problems? On the front page?


[Help.ubuntu.com]("https://help.ubuntu.com/"), is the wiki you are looking for, search for what you need help on..

---

