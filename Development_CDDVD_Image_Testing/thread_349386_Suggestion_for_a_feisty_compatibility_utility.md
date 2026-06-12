---
title: "Suggestion for a feisty compatibility utility"
date: 2007-01-30
forum: Development CD/DVD Image Testing
---

### Post by UBfusion on 2007-01-30
It's a bit out of topic, but I have been a victim and maybe others in the future (and in future ubuntu releases) will experience the same type of problem.

In [this thread]("http://ubuntuforums.org/showthread.php?t=346453") a user struggled for 4 days installing feisty and failed because of relatively new and not well supported hardware (965 chipset with core 2 duo - just like my setup, this is the reason I still test daily builds in vmware).

Would it be feasible/desirable/useful to develop a utility running after the boot of daily-live builds that warns users and pinpoints possible incompatibility problems due to well known bugs or not yet supported hardware?

Since the kernel detects most hardware existing on the planet, isn't such a utility feasible in principle?.

---

### Post by pochu on 2007-01-30
Hi UBfusion

I'm not sure if what you are saying could be implemented, but if you would like to see it, I suggest you to go to Launchpad and write a [new spec]("https://blueprints.launchpad.net/ubuntu/+addspec"). Doing that, you will let devs to see it, and, if they like it, it's easy to implement, and it's useful, the will do it ;)

Regards
Pochu

---

### Post by Henrik on 2007-01-30
> **UBfusion said:**
> Would it be feasible/desirable/useful to develop a utility running after the boot of daily-live builds that warns users and pinpoints possible incompatibility problems due to well known bugs or not yet supported hardware?


We will be doing something similar as apport and Malone re developed further. We'll  collect more information about what went wrong on the Lie CD and Malone should do a better job of guiding the user through the bug report.

---

### Post by UBfusion on 2007-01-30
Thanks a lot pochu, i had no idea what addspec was up to now.

From what I see, several people in the past had submitted similar ideas but noone was really interested to discuss or work towards that direction. However, things change very fast, and when linux gets a significant desktop market share, I am sure hardware compatibility - related warnings upon installation will definitely appear. I think that moment is not very far in the future from now, since software and operating systems are getting more and more expensive. As seen in recent news, a dvd player is now cheaper than the media it plays. 

Today vista will reach the masses and sooner or later people will start experiencing many surprises. Won't many of them sooner or later experiment installing the most popular linux distro? (hint, hint!). Imagine the satisfaction of a potential switcher seeing a live cd message like "Your multimedia hardware appears to be 100% compatible with Ubuntu" or "Support for your tv tuner card is currently under heavy development, read this Ubuntu forum thread".

---

### Post by pochu on 2007-01-30
That would be fine, really :)

If there are other similar specs, pick that which has been more discussed, or which has been drafted, or whatever you want, and work in it. Then, when a new uds is announce, suggest your spec to be discussed there ;)

Regards
Pochu

P.D.: My hardware is 100% Linux Compatible :D

---

### Post by old_geekster on 2007-04-15
> **pochu said:**
> That would be fine, really :)

If there are other similar specs, pick that which has been more discussed, or which has been drafted, or whatever you want, and work in it. Then, when a new uds is announce, suggest your spec to be discussed there ;)

Regards
Pochu

P.D.: My hardware is 100% Linux Compatible :D
Mine, too.  See my "signature".:D

---

