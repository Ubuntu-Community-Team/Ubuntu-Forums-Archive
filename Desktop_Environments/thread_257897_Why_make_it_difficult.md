---
title: "Why make it difficult?"
date: 2006-09-15
forum: Desktop Environments
---

### Post by luckyaba on 2006-09-15
I am curious as to why every time i install ubuntu i have to install build essentials, gcc, and change the sources.list file for the right repositories. I am sure there are a few other little things like that but i really would like to know why these things don't come in the base install? If liunx is trying to gather attention and users then why not have these things built in?

i am sure there is a good reason or... maybe not. I have installed enough times for it to not take me anytime to do these things but for the sake of my own curiousity i thought i would ask.

sorry if this thread is in the wrong place. not sure where to put it.

---

### Post by TLE on 2006-09-15
Deciding which packages go on the cd has to be a difficult job, and will almost certainly involve a prioritizing. IMHO the optimal way to do this is to fill the cd up with all the things a newbie would need. That increases the chance that the a users first experience is a good one. And...
Since all the tools that I would consider to be in the "Non-newbie" categori are also mainly used by non-newbies... They will also, like you, know how to easily install them.

So in that way it all fits perfectly and I think Ubuntu does weel in this prioritizing.

Regarding the list of repos', the reason other repos'(inuverse and multiverse) are disabled per default is to make it very clear that: These packages are not maintained by the Ubuntu team and are thus potentially more buggy. This difference have to be marked, so that people that use Ubuntu in their buisnesses can choose only the most stable and best supported software.
Regards TLE

---

### Post by luckyaba on 2006-09-15
Ok the repository thing i totally get and agree with now. I never thought of it like that really.

As for the packages included.. I suppose Ubuntu comes stock with programs for just about everything. I guess i just prefer alternative programs to some which are included and always end up needing additional packages like Gcc and such. Seeing as people who do like Ubuntu and stick with it, would it be all that difficult to include those packages with it? i mean is there some kind of technical or legal issue with not including them?

---

### Post by nereid on 2006-09-15
Why don't you write yourself a install script, which installs all your needed packages after you've installed Ubuntu? Just to save some typing.

---

### Post by TLE on 2006-09-15
> **luckyaba said:**
> ... Seeing as people who do like Ubuntu and stick with it, would it be all that difficult to include those packages with it?
I understand what you mean, but the thing really is, for every app you add you have to remove something else and maybe, just maybe, one of the reason people come to know about it and stick with it, is that it come "almost" newbie useable by default. The community could always need more people so we're not doen making it easy and comfortable for newbies untill [bug #1]("https://launchpad.net/distros/ubuntu/+bug/1/+viewstatus") i resolved.

> **luckyaba said:**
> i mean is there some kind of technical or legal issue with not including them? Not with those two packages, not as far as I know anyway.

BTW: The install script is a very good idea, I use one myself. Just write in this thread if you need inspiration, I know that both nereid and I know our way around scripts and the CLI ;)

---

### Post by luckyaba on 2006-09-15
> **nereid said:**
> Why don't you write yourself a install script, which installs all your needed packages after you've installed Ubuntu? Just to save some typing.

because uuhhhhh that would make to much sense? haha. i like that idea. going to try that when i get home.

---

### Post by luckyaba on 2006-09-15
Don't get me wrong. I am a big fan of Ubuntu and have been for quite some time. I just always had that qusetion in the back of my mind.

---

### Post by TLE on 2006-09-15
> **luckyaba said:**
> Don't get me wrong. I am a big fan of Ubuntu and have been for quite some time. I just always had that qusetion in the back of my mind.

Oh I didn't, I think I know what you mean and you aren't the only one, I think I saw a thread just like this one just the other day.

---

### Post by Lord Illidan on 2006-09-15
I wish build-essentials was included in the box...but I think the CD is too full up already..

---

### Post by nereid on 2006-09-17
> **luckyaba said:**
> because uuhhhhh that would make to much sense? haha. i like that idea. going to try that when i get home.

No problem, this is that we are there fore :D

---

### Post by aysiu on 2006-09-17
> **Lord Illidan said:**
> I wish build-essentials was included in the box...but I think the CD is too full up already..
Nope. It already is taking up room on the CD. It's just not installed. Don't believe me? Pop your Ubuntu CD in (either Desktop or Alternate) and look at the contents.

Ubuntu doesn't include a lot of stuff for philosophical reasons. If you don't agree with that philosophy, you can add those things yourself... or use another distro. Mepis and PCLinuxOS are great distros for new ex-Windows users and have stuff new ex-Windows users could find immediately useful (say, Flash in Firefox, for example).

---

