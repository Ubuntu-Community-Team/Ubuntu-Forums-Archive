---
title: "Would this work???"
date: 2007-10-23
forum: Education &amp; Science
---

### Post by fingerless fred on 2007-10-23
Want to get some feedback...
I manage and maintain 3 computer labs in a windows domain enviornment. OS: XP Pro. I have recently gotten into Ubuntu, and have used it for a console (intra-web server) machine for my web development class. Anyways, I just bought 34 new machines with XP Pro. Could I have saved the money on the OS and used Ubuntu and still have the same server side securities for the students to log into the school domain? :confused:
Thanks in advance for the input and time.

PS: Is the a lab management app that would allow me to remotely control each machine individually or as a lab??

---

### Post by kidders on 2007-10-24
Hi there,

The short answer to your question is "Yes".

Since we're talking about doing it on a reasonably large scale though, I would (from experience) strongly recommend against making such a switch with any speed.

I'm certain you don't need to be *told* this, but over time, network admins become so familiar with the quirks and hairy bits of the operating systems & network architectures they use, that they operate almost instinctively, side-stepping hidden gotchas without even thinking about it. The garden variety Linux + Windows mix has its own set of quirks, some of which can be quite time-consuming to figure out & get the hang of ... so no matter how good you are, making an overnight switch would be certain disaster.

I would suggest spending a few months playing around with one or two machines ... be they Samba-based domain controller + Windows box or MS-based domain controller + Linux box ... just to be sure you know your way around annoying troublemakers like NTLM, roaming profiles, centralised management, etc. Once you get good at it, seamlessly integrating Ubuntu (or any other Linux) into a pre-existing MS domain is quite easy, and even has a few up sides. :-)

I hope that helps. Interestingly, the request most often made of me (the physical person, not the forum member hehe) by people interested in building a hybrid network is how to serve Windows clients with a Linux PDC ... essentially the opposite of what you're thinking of.

---

