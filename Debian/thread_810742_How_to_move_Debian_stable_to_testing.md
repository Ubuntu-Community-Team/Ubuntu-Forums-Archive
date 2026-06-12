---
title: "How to move Debian stable to testing?"
date: 2008-05-28
forum: Debian
---

### Post by hockeyfighter09 on 2008-05-28
Right now I am running Debian etch on a desktop, but I am interested in moving that into the testing branch.  How do I do that?  I want to make it so that it will be a rolling release in that it will move directly onto the next testing version once Lenny is released.  Thanks ahead of time for youre responses!

---

### Post by regomodo on 2008-05-28
go to "/etc/apt/sources.list" and change any mention of "etch" (or stable) and swap with "lenny"

Then, "apt-get update && apt-get dist-upgrade"

---

### Post by SunnyRabbiera on 2008-05-28
> **regomodo said:**
> go to "/etc/apt/sources.list" and change any mention of "etch" (or stable) and swap with "lenny"

Then, "apt-get update && apt-get dist-upgrade"

true, also if you have snaptic you can just add the lenny repos.

---

### Post by kerry_s on 2008-05-28
> **hockeyfighter09 said:**
> Right now I am running Debian etch on a desktop, but I am interested in moving that into the testing branch.  How do I do that?  I want to make it so that it will be a rolling release in that it will move directly onto the next testing version once Lenny is released.  Thanks ahead of time for youre responses!

also keep in mind lenny moves quick, there have been updates at least every other day, i have had no problems, but problems are possible.

---

### Post by SunnyRabbiera on 2008-05-28
> **kerry_s said:**
> also keep in mind lenny moves quick, there have been updates at least every other day, i have had no problems, but problems are possible.

well that is why its called "testing" :D

---

### Post by hockeyfighter09 on 2008-05-28
> **regomodo said:**
> go to "/etc/apt/sources.list" and change any mention of "etch" (or stable) and swap with "lenny"

Then, "apt-get update && apt-get dist-upgrade"

Now this is what confuses me.  I read that if I do this that when Lenny becomes stable I will be stuck with it and not move on to the next testing version, is this true?  What if I were to replace stable with "testing" rather then "Lenny" then would that be able for me to move onto the next test version after lenny came out?  :confused:

---

### Post by kerry_s on 2008-05-28
> **hockeyfighter09 said:**
> Now this is what confuses me.  I read that if I do this that when Lenny becomes stable I will be stuck with it and not move on to the next testing version, is this true?  What if I were to replace stable with "testing" rather then "Lenny" then would that be able for me to move onto the next test version after lenny came out?  :confused:

using "testing" is fine.

---

### Post by hockeyfighter09 on 2008-05-28
So basicially I go into /etc/apt/sources.list then change wherever it says Etch or stable and replace them with Testing?

---

### Post by kerry_s on 2008-05-28
> **hockeyfighter09 said:**
> So basicially I go into /etc/apt/sources.list then change wherever it says Etch or stable and replace them with Testing?

yes, just change etch to testing, you don't need stable if your not planing on using anything from it. i use the stable kernel, cause the testing kernel does not work for me, so i keep the stable repos for the kernel updates for 2.6.18 kernel on my system.

don't forget the sources.list needs to be edited as root. you can also use synaptic if you have that. (see pics)

---

### Post by Raven_Oscar on 2008-05-29
Well as it was said you have to change "etch" in your sources.list on "testing" or "lenny". And do apt-get update && apt-get dist-upgrade. So that's all you need to do.

---

### Post by oswaldkelso on 2008-05-29
> **hockeyfighter09 said:**
> So basicially I go into /etc/apt/sources.list then change wherever it says Etch or stable and replace them with Testing?


As I understand it he way it works is stable, testing, unstable, and experimental.

old stable is sarge
current stable is etch 
current testing is lenny 
unstable is always sid
experimental is for uber geek developers

At this moment in time lenny and testing are the same, but

if you put lenny in your sources.list you will be running testing until the point that lenny becomes debian stable then you be running stable.

if you put testing in your sources.list you will be running testing for ever.

Some people like only run testing when its getting near to becoming debian stable, others like a rolling release and run testing all the time.

---

### Post by jdhore on 2008-05-29
> **oswaldkelso said:**
> As I understand it he way it works is stable, testing, unstable, and experimental.

old stable is sarge
current stable is etch 
current testing is lenny 
unstable is always sid
experimental is for uber geek developers

At this moment in time lenny and testing are the same, but

if you put lenny in your sources.list you will be running testing until the point that lenny becomes debian stable then you be running stable.

if you put testing in your sources.list you will be running testing for ever.

Some people like only run testing when its getting near to becoming debian stable, others like a rolling release and run testing all the time.

You're correct on all that except for two things. 

1. Experimental. Experimental is not a true version. It doesn't have nearly the number of packages required to have a full system (only about 1000 packages in the whole repo compared to ~20,000 for Etch, Lenny and Sid) and it's not really uber-breakage, it's just for packages that haven't gone to a final version yet such as e17, Firefox 3, KDE 4.1, you get the idea.

2. Testing is just as stable today (like 6 weeks from release/RC) as it is when Testing development starts after a new release. That's part of what makes testing so great, the rules are pretty much the same whether we're 2 weeks away from a release or 2 years away from a release.

---

### Post by keithpeter on 2008-05-29
> **oswaldkelso said:**
> 
if you put testing in your sources.list you will be running testing for ever.


So if I put 'stable' in sources.list instead of 'etch' I'll be running stable on a rolling upgrade basis? Just apt-get update && apt-get upgrade now and again?

---

### Post by jdhore on 2008-05-29
> **keithpeter said:**
> So if I put 'stable' in sources.list instead of 'etch' I'll be running stable on a rolling upgrade basis? Just apt-get update && apt-get upgrade now and again?

Yes, but i wouldn't recommend that as Debian Stable is really only meant for uber production-quality servers and you wouldn't want to "blindly" upgrade to a new release on a production-level server unless you test the hell out of it. Hell, my home server (not production-level,but i prefer to have good stability) is running FreeBSD 6.3 and i refuse to upgrade to FBSD 7 till 7.1 comes out so i know it's stable.

---

### Post by keithpeter on 2008-05-31
> **jdhore said:**
> Yes, but i wouldn't recommend that as Debian Stable is really only meant for uber production-quality servers and you wouldn't want to "blindly" upgrade to a new release on a production-level server unless you test the hell out of it. 

Well, I'm using Etch on a domestic desktop because its light and fast, so I have changed the sources.list and await fun in september as 'stable' points to Lenny in place of Etch.

[http://ubuntuforums.org/showthread.php?p=4860994#post4860994](http://ubuntuforums.org/showthread.php?p=4860994#post4860994)

This is the post that started me playing with Debian (not that I had any problems with 8.04 and I plan to dual boot so I can bug fix and do some work now and again :) ]

---

### Post by hockeyfighter09 on 2008-06-02
> **keithpeter said:**
> Well, I'm using Etch on a domestic desktop because its light and fast, so I have changed the sources.list and await fun in september as 'stable' points to Lenny in place of Etch.

[http://ubuntuforums.org/showthread.php?p=4860994#post4860994](http://ubuntuforums.org/showthread.php?p=4860994#post4860994)

This is the post that started me playing with Debian (not that I had any problems with 8.04 and I plan to dual boot so I can bug fix and do some work now and again :) ]

Hey, thanks for posting that link.  It really put things in perpective for me.:guitar:

---

### Post by oswaldkelso on 2008-06-03
> **jdhore said:**
> You're correct on all that except for two things. 

1. Experimental. Experimental is not a true version. It doesn't have nearly the number of packages required to have a full system (only about 1000 packages in the whole repo compared to ~20,000 for Etch, Lenny and Sid) and it's not really uber-breakage, it's just for packages that haven't gone to a final version yet such as e17, Firefox 3, KDE 4.1, you get the idea.

2. Testing is just as stable today (like 6 weeks from release/RC) as it is when Testing development starts after a new release. That's part of what makes testing so great, the rules are pretty much the same whether we're 2 weeks away from a release or 2 years away from a release.

Thanks for correcting me on Experimental. I agree with your comment on testing, thats why I said "some people". I think it's fine to run testing at all times. I do.

---

