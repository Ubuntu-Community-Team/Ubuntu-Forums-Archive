---
title: "Any libs/tools for calculating astronomical data?"
date: 2011-02-21
forum: Education &amp; Science
---

### Post by Buttons840 on 2011-02-21
In Stellarium ([http://www.stellarium.org/](http://www.stellarium.org/)) or KStars (though I haven't used KStars) you can view real time astronomical data about the Sun and Moon.  IE, you can view the altitude and angles of the Sun through the day.  The times of the solstices, etc.

I'd like a simple script that can calculate the same, and I've had some success in my searches for astronomical formulas, but they're very complicated.  I was wondering if there are any libs or lightweight tools which can do the heavy math for me?  Any suggestions?

One the subject, I read some interesting things about leap-seconds.  [http://en.wikipedia.org/wiki/Leap_second](http://en.wikipedia.org/wiki/Leap_second)  Apparently the earths rotation is slowing down at an unpredictable rate, depending on how the continents shift and such, and so creating mathematical formulas 100% accurate forever is probably impossible.  Even so, I'm hoping there is something good enough to assist me.

---

### Post by rewyllys on 2011-02-26
> **Buttons840 said:**
> . . . . I'd like a simple script that can calculate the same, and I've had some success in my searches for astronomical formulas, but they're very complicated.  I was wondering if there are any libs or lightweight tools which can do the heavy math for me?  Any suggestions? . . . . 

I'd suggest that you take a look at *GNU Octave*, a good open-source program for doing sophisticated mathematics. Among commercial software programs, *Mathematica* will, of course, do what you're asking; it runs natively in Linux. There is a student version of it that I think is available for home users at a moderate cost.

---

### Post by Buttons840 on 2011-04-18
I know there are a variety of language capable of doing the calculations (I would use python probably), I wondered if there is any existing code for calculating these things?  The math looks complicated and would take a lot of work for me to figure out.

---

### Post by rewyllys on 2011-04-18
> **Buttons840 said:**
> I know there are a variety of language capable of doing the calculations (I would use python probably), I wondered if there is any existing code for calculating these things?  The math looks complicated and would take a lot of work for me to figure out.
I suggest that you take a look at the book, *Astronomical Algorithms*, by Jean Meeus, which should be available from university libraries and larger public libraries (or, of course, from Amazon.com).  It, like other books by Meeus, contains detailed algorithms for a great variety of astronomical calculations; and these algorithms can be easily implemented in, e.g., Python.

---

