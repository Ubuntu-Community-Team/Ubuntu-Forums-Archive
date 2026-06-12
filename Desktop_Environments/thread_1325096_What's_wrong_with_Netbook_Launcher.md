---
title: "What's wrong with Netbook Launcher ?"
date: 2009-11-13
forum: Desktop Environments
---

### Post by jthirt on 2009-11-13
While waiting for the delivery of my Netbook I thought I should try the latest Karmic Netbook live CD and see how the specific launcher looks. But what a disappointment! Not in terms of look. It does look really cool (when it displays correctly), but I have yet to find one PC that runs it properly.

I tried it on 7 different PCs (Dell, Medion, Gateway desktops and Dell, IBM and Gateway laptops with various specs and ages...) and none of them were able to operate properly with that desktop launcher! None are actual Netbooks, but that shouldn't be an issue (from [Launchpad]("https://launchpad.net/netbook-remix")): 

> Ubuntu Netbook Remix is a 'remix' of the standard Ubuntu Desktop release to enable it to work better on devices with small screens, such as Netbooks (sub-notebooks), although these packages will work on any 8.04 (Hardy) or 8.10 (Intrepid) installation. 

Well, it doesn't say 9.04 or 9.10, but I would expect the idea extends to later versions too.

I was particularly keen to use this launcher on laptops that I want to dedicate to my kids (5 & 7 years old now), but the only way to make it work is using the keyboard and even then you better be prepared for a challenging exercise:

1) Work your way down the left pane with the down arrow to highlight the requested topic.
2) Press Enter to select the topic.
3) Move to the right into the topic's items area and use any arrow keys to select the required item. Forget about Home or End, they don't work either. 
NB: Forget the favorites topic as it won't work at all. 

Moving back into the left pane is also kind of a challenge and I will not even try to explain how it can be done.

This experience may differ from system to system. If you're lucky, the mouse moves may trigger some change of appearance in the left pane, but no actual result when clicking on a topic or after so long that you have gone somewhere else in despair!

I have been browsing the forum in search for evidence of an issue, but it is not obvious. 

- Am I the only one suffering like this?

Trying to understand, I switched on the control center that kind of does the same thing but obviously using a different (less sophisticated) technique that works a treat (except if you try to use the arrows, but that I can accept it was not designed for). 

- Anyone else interested to see this launcher work for non netbooks?

:frown:         I am!

JT - Frustrated

---

### Post by jthirt on 2009-11-14
Hello again everybody.

Further to my post from yesterday, I have now received my Netbook (a Samsung NC10 by AGnes B with a cool Lizard, with 1gb memory and 160gb disk) and I installed Karmic Netbook Remix on it. The Netbook Launcher works just fine and it is a real pleasure on that machine. It is yet a bit early to draw conclusions, but so far except for the known microphone issue (witch is annoying if you intend to use stuff like Skype!) it is brilliant!

I am still curious to know if anyone uses the Netbook Launcher on anything else but Netbooks. Perhaps we should do a survey to find out: Who uses it ? and Who wants to use it (or is interested)?

In another life, we introduced a similar feature into our software suite and it attracted limited interest from knowledgeable consultants who were used to the classic menu driven launcher, but users when introduced to the other desktop alternative were really enthousiastic about it. But for people to adopt a new feature, it must work fairly well otherwise they immediately reject it.

Any views?

:)    JT - Smiling again

---

### Post by dhans462 on 2009-11-14
I'm having the same problem as the OP...

Trying to run NBR on an older Thinkpad.. x40.   The mouse doesn't work properly with the NBR gui.. Keyboard works but in a wacky way..  Is this a video driver issue?  

Here's a discussion I found via google : [https://bugs.launchpad.net/netbook-remix-launcher/+bug/368394](https://bugs.launchpad.net/netbook-remix-launcher/+bug/368394)  Most of it is too linuxy for me to understand  ;)  (I'm new to it all)

Important to note that other elements of the OS work fine, such as adjusting system time, and using the wireless setup pulldown menu, mouse is accurate and works as normal.  So the problem lies within the quick launch GUI of NBR

Really annoying!  Hopefully somebody can shed some light on this!

Thanks,
D

---

### Post by jthirt on 2009-11-14
Thank you for pointing me in that direction!

It's good to see that the issue is actually being looked at. I will track this bug. I also can't understand the story about L shaped memory or whatever. Also, I need to check the various systems I tried but only a couple maybe had intel video cards. Most have either NVidia or ATI radeon. So it's all very confusing. 

What I do not understand is why this appears to be designed to work on rather specific hardware. If it requires quite special graphic capabilities, then it should be mentioned somewhere in the requirements related to UNR so that we do not waste hours or even days trying to find out what's going on.

On the other hand, I'm quite sure there are improvements to make in the keyboard handling of this launcher. Even on a working Netbook the favorites won't react like the rest and navigation up and down the left pane is not straight forward. 

I would be curious to see the code, if I can understand any of it! :-k

Cheers,
JT

---

### Post by jthirt on 2009-12-07
I have now managed to overcome the problems that I had on one of my laptops thanks to the instructions related to a reported [bug]("https://bugs.launchpad.net/netbook-remix-launcher/+bug/368394/comments/55"). 

This was with an intel video card. Not sure what is the status for other cards as I had no time to experiment further. 

I must also say that I am quite happy using this launcher on my Netbook!

JT

---

