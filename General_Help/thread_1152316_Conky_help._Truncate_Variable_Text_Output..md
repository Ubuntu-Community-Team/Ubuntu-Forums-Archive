---
title: "Conky help. Truncate Variable Text Output."
date: 2009-05-07
forum: General Help
---

### Post by Akovia on 2009-05-07
Hi,
Was hoping someone could tell me if I could take a conky variable output and truncate it before it is displayed. I'm sure a script could be made but I think that is beyond my ability. Something as simple as using the -cut command I think but I'm not sure how to "inject" it before the variable is spit out to conky.

My target is to cut off the output from ${top name} and limit it to something reasonable. Vowel decimation would be ideal, but a simple cut would be fine. I can't use the minimum_text to accomplish what I want in this case because of the unique setup I have. At lease I haven't figured out a way to do so yet. If anyone has any ideas I'd be elated to hear them.

Best Regards,
Akovia

---

### Post by qweru on 2009-09-06
hi
i dont know if it would help you know but i could cut text with $scroll.
using it like this ${scroll 7 0 ${top name 1}} this will cut the name after 7 letters.
i used this until now but unfutinatly it dosent work anymore with conky 1.7.2 so if there are other possibilities that would be nice

---

