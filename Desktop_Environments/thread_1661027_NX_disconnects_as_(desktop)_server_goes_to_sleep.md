---
title: "NX disconnects as (desktop) server goes to sleep"
date: 2011-01-06
forum: Desktop Environments
---

### Post by johmut on 2011-01-06
Hi All, 

My remote "NX Client" disconnects after 60' when server goes to sleep, leaving my session suspended. 

My server is running Ubuntu 10.10 Desktop Edition,  Power Management is configured to sleep after 60'
I need the server to go to sleep if nobody's using it. I don't need the server to go to sleep in case:

[LIST]
[*]media is being streamed
[*]remote connections are in use
[/LIST]
How to configure my system to look further than just keyboard and mouse activity before initiating sleep?

PS: 

[LIST]
[*]Media streaming can be DAAP/RhythmBox; DLNA/MediaTomb; SLIMP3/Squeezebox server
[*]Remote connections can be SSH/PuTTY; SSH/NX Client
[/LIST]
TIA for any help you can provide,
Best Regards,
johmut

---

### Post by johmut on 2011-01-15
Gentle Bump ? Really no one having issues with Ubuntu Desktop power management versus remote sessions being active and media streaming ?

---

### Post by fugazer on 2011-01-31
I would like to learn the same

---

### Post by jdlk on 2011-02-16
Yes, same issue here, Setup of Ubuntu streaming media server went flawlessly, except that the system goes into standby while streaming. I can't find any workaround for this (apart from disabling standby obviously, but as the server is only in use a few hours a day that's something I don't want to do).  What I think we're looking for is something like Windows' "Away Mode", which allow an app to make the system enter "Away Mode" instead of the regular sleep mode. This leaves the PC capable of background tasks not requiring user input.

---

### Post by hjr65 on 2012-08-26
Also me would like to learn about this, since there is no solution out for ubuntu 12.04. 
I solved this challenge on another linux (gentoo) server box by just entering sleep mode when cpu load reports for some period only idle load. That is a bit fuzzy, but works reliably. 
The same experiment on my ubuntu 12.04 box ended up with in an unwakable state. I never looked into what is wrong with the commandline hibernate tools.

I'd love to hear there is a simple solution.

---

### Post by hjr65 on 2012-08-26
Hey, there is a new package "powernap" available for ubuntu 12.04. According it's description it fits 100% into what we need.

I'll give it a try.

---

### Post by overdrank on 2012-08-26
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

