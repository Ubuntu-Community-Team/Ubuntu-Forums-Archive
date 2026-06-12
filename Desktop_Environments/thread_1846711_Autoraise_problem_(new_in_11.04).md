---
title: "Autoraise problem (new in 11.04)"
date: 2011-09-19
forum: Desktop Environments
---

### Post by rainy-day on 2011-09-19
Hi, I've used and loved the autoraise feature in 10.04 but after upgrading to 11.04 I find that it's effectively unusable: when you switch windows using alt-tab, autoraise kicks in and raises whatever window was under cursor (usually the old active window).

How can I fix this?

Bonus points if the old issue with autoraise kicking in on switching desktops can be also fixed since it's a similar problem.

I'm using 11.04 classic.

thanks!  -ak

---

### Post by rainy-day on 2011-09-20
Additionally, autofocus is broken in exactly the same way.

On top of that, this breaks xtest automation with xte command unless you do additional mouse manipulation, which is both more complicated and annoying because mouse moves from where it was left (is there a way in xte to save mouse location and move back to it?)

Two important features appear to be broken and nobody has any comment?

---

### Post by Krytarik on 2011-09-20
> **rainy-day said:**
> Two important features appear to be broken and nobody has any comment?
I'm still on Lucid 10.04, otherwise at least I would have noticed and would care about this. :p It seems like both of these features aren't very popular. I know because I'm subscribed to a related [bug in AWN]("https://bugs.launchpad.net/awn/+bug/500981") that affects a pretty essential feature, and doesn't seem to care too many people either, neither the devs.

Greetings.

---

### Post by Copper Bezel on 2011-09-20
Yeah, this is a sore point for me, too. I don't use autoraise, but I have in the past, and I found it to be very useful for some situations. Odd little features like this don't seem to be taken account of in a lot of apps (which I guess explains, to some extent, why Ubuntu and Gnome are pushing toward removing a lot of the more granular customization features outright, which is at least self-consistent.)

Certainly _[file a bug]("https://bugs.launchpad.net/ubuntu/+source/compiz")_. The only related issue I see listed is a similar but distinct issue regarding the Scale plugin.

---

### Post by rainy-day on 2011-09-20
Thanks for the response!

It seems like a feature that'd be useful to nearly all users, switching windows is something you do very often and autofocus/autoraise make it that much easier when you're using mouse.

I found a workaround using mousetweak + dwell. In fact, this feature is also broken in 11.04, so I have to do this:

killall mousetweaks
mousetweaks --dwell --dwell-time=0.5&

This works fairly well so far and in fact I like dwell click, but I bet a lot of people won't.

What is it with 11.04 and mouse features? Nothing works..

---

### Post by rainy-day on 2011-09-20
> **Copper Bezel said:**
> Yeah, this is a sore point for me, too. I don't use autoraise, but I have in the past, and I found it to be very useful for some situations. Odd little features like this don't seem to be taken account of in a lot of apps (which I guess explains, to some extent, why Ubuntu and Gnome are pushing toward removing a lot of the more granular customization features outright, which is at least self-consistent.)

Certainly _[file a bug]("https://bugs.launchpad.net/ubuntu/+source/compiz")_. The only related issue I see listed is a similar but distinct issue regarding the Scale plugin.

Thanks, will file a bug.

I have to say that often I don't file ubuntu bugs if they're present in some basic features available from default ubuntu interface. It just feels like nobody tests them and nobody cares. And there are so many of them.

I've used Ubuntu since Dapper (version 6), and I've never seen even the slightest improvement in terms of number of bugs in new release, and it's always the kind of bugs that are apparent with even the most cursory, superficial testing.

 What I love about Ubuntu is that after I spend 20-30 hours fixing the rough edges, it works like a tank for the next 2-3 years. Windows is exactly the opposite in my experience - it always works perfectly on a fresh install, and then things start slowly breaking, getting corrupted misteriously, etc.

Unfortunately, I'm afraid new users assume that initial flakiness is an indication of overall quality, and I can't blame them..

---

### Post by Krytarik on 2011-09-20
> **rainy-day said:**
> It seems like a feature that'd be useful to nearly all users, switching windows is something you do very often and autofocus/autoraise make it that much easier when you're using mouse.
Well, what can you say?! Another default behaviour is to not autoraise a window if it "demandsattention", and not too many seem to care about that as well.

---

### Post by Krytarik on 2011-09-20
> **rainy-day said:**
> What I love about Ubuntu is that after I spend 20-30 hours fixing the rough edges, it works like a tank for the next 2-3 years.
[...]
Unfortunately, I'm afraid new users assume that initial flakiness is an indication of overall quality, and I can't blame them..
True, and true.

EDIT: Excluded the Windows part because yes, the default system functionality is there in most cases, right after a fresh install, but you spend much more time on installing all needed apps/tools, which is much more easier with Ubuntu's package management. Not to mention that you apply things to Ubuntu which you can't even think of in Windows. But, of course, +1 reg. the slowly-breaking part.

---

