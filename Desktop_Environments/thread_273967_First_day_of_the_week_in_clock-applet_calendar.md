---
title: "First day of the week in clock-applet calendar"
date: 2006-10-09
forum: Desktop Environments
---

### Post by Thruston on 2006-10-09
On my British install of Dapper, with the locale set to en_GB, the clock-applet calendar shows weeks starting on Sunday.  And this despite the fact that I have told Evolution to show weeks starting on Monday.  Worse still clock-applet has no preference setting of it's own to say "start weeks on Monday".

The reason for this irritating behaviour is that clock-applet gets its settings from the locale file and the en_GB locale defines Sunday as the first day of the week.

1) this is wrong (so I have raised a bug against the locale for en_GB)

2) you can choose a different en locale, like en_DK or en_IE that correctly specifies Monday as the first day of the week.  If you do this the clock-applet calendar looks better, but other things might be wrong.

3) you can patch your own copy of en_GB using the (obscure and poorly documented) localedef tool.

None of these is a very satisfactory solution.  Even if they do fix en_GB upstream, *some* people in the UK like weeks starting on Sunday, so then it will be wrong for them.

So.... (in my opinion)

clock-applet should either provide a week-starts-on setting or use the setting stored by Evolution

---

### Post by KhaaL on 2006-11-06
This has annoyed me for a while and I'd like it to be fixed too.

---

### Post by atari_ on 2006-12-16
I agree with the first two posters, it would be nice if you could change the first day of week.

actually I thought had I set all my location and stuff to Estonia, or as much as there was to set during the installation (timezone and keyboard)... I like my desktop in eglish so I didn't change any language settings ...which may be the reason im getting the en_GB time.

---

### Post by ftmichael on 2007-05-09
I'm using Feisty (had the same problem in Edgy, can't remember about Dapper) and also have an en_GB install, and it's starting my week on Monday, despite the fact that I told Evolution to start it on Sunday, which I prefer.  wtf?

Michael

---

### Post by mdurham on 2007-07-22
Surely someone has an answer to this annoying problem!

---

### Post by lisati on 2007-07-22
I would hesitate to call this a bug; rather it would be a "desired feature" of setting the locale. My own preference is for starting the week on Sunday, which is what the clock applet on my machine defaults to, but for reasons that are better discussed elsewhere...

How important is it?

---

### Post by mdurham on 2007-07-22
> How important is it?
It's not important at all, just annoying.

---

### Post by z0phi3l on 2007-07-22
Sunday IS the first day of the week, so what's the problem?

It's a feature issue not a bug, and maybe they'll "fix" it some time

---

### Post by mdurham on 2007-07-22
If it's not a bug, why does it show Monday as 1st day on one of my computers & Sunday on another? Do you think it just randomly selects when it's installed? I would say it's a bug.
Cheers, Mike

---

### Post by mdurham on 2007-07-23
See [here]("http://zapek.com/?p=10") for a fix, thanks to Zapek.

---

### Post by SirOracle on 2007-07-26
> **z0phi3l said:**
> Sunday IS the first day of the week, so what's the problem?

It's a feature issue not a bug, and maybe they'll "fix" it some time

You do know that monday is the first day of the week in most countries, right? And wouldn't you consider it as a bug if your calendar for instance had friday as the first day of the week?

---

