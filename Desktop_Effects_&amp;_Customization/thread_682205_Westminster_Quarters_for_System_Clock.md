---
title: "Westminster Quarters for System Clock"
date: 2008-01-29
forum: Desktop Effects &amp; Customization
---

### Post by Patriot1776 on 2008-01-29
Hey, I'm wondering if anybody has ever written a script for Linux to play the Westminster Quarters, the chimes made famous by Big Ben, using timidity.  Has anybody ever thought of this?

---

### Post by PinkFloyd102489 on 2008-01-29
Wouldnt be hard. Just make it a cron job to play on the hour and have Timidity play the .mid file.


cron line would look like this:
```

0 *  * * *   command

```


And here's a link to the .mid file.

[http://upload.wikimedia.org/wikipedia/en/d/d3/Westminster-chimes.mid]("http://upload.wikimedia.org/wikipedia/en/d/d3/Westminster-chimes.mid")

and here's the link to setup Timidity:

[http://www.funnestra.org/ubuntu/gutsy/#timidity]("http://www.funnestra.org/ubuntu/gutsy/#timidity")

---

### Post by Patriot1776 on 2008-01-29
Problem is that MIDI file is only of the whole hour and chiming six o' clock.  

I want to set it up to play the quarter bells, on the quarter hours, and then on every hour, besides playing the full chimes, chime the correct number of times for the hour.  So, I need to make myself many MIDI files.  Are their MIDI composition programs that can accept straight input from a normal keyboard?  I don't have a MIDI keyboard and won't buy one for only doing this.

---

### Post by PinkFloyd102489 on 2008-01-29
Im looking for a midi keyboard because I think I saw one in the repos. Here's the edited cron lines for the quarters.

```

#quarters
15,30,45 *  * * *    command.for.quarters

#on the hour
0 *  * * *    command.for.hour

```


MIDI Keyboards and programs include: vkeybd, qsynth, and rosegarden.

---

### Post by Patriot1776 on 2008-01-29
What's with the asterisks?

---

### Post by Patriot1776 on 2008-01-30
Got it working.  Thanks much man!  Rosegarden made it easy to make the extra MIDI files I needed.

---

