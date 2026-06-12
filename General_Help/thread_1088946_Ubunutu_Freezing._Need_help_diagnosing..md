---
title: "Ubunutu Freezing. Need help diagnosing."
date: 2009-03-06
forum: General Help
---

### Post by Gidgidonihah on 2009-03-06
I recently installed ubuntu on my home machine. I've been using it at work for a while, but now I'm working from home, so...

Ubuntu is running fine except for 1 huge issue. At apparent random times, it freezes. No response from keyboard and mouse. Any indicators and spinners just freeze.

I'm not sure where to start to figure out the problem. It'll happen maybe 4 or 5 times in a typical day that I'm working on it.

My first feeling is that it's some sort of hardware issue, but I really have no idea.

Are there any logs that might help? What other information would you like to know?


This whole thing is really frustrating since it keeps interrupting my work.

---

### Post by beno1990 on 2009-03-06
1. Does ctrl+alt+backspace work or does it remain frozen?

2. Does /var/log/Xorg.0.log show anything unusual around the time of the freeze? (If everything is frozen, just note the time the Gnome clock shows and that'll be the time it froze and you should look there in the log)

3. What programs are you running at the time of the crashes? Are any of them acting abnormally shortly beforehand?

---

### Post by jwbrase on 2009-03-06
Overheating? I know that it's one fairly frequent cause of repetitive random freezing. Is there alot of dust in the case?

---

### Post by Gidgidonihah on 2009-03-06
Wow, thanks for the speedy replies guys.

beno1990:
1. Not sure. Next time it freezes, I'll check.

2. I will look at that the next time I boot into Ubuntu. I'm in windows right now for gaming and probably will be until Monday :)

3. Mostly just using firefox, pidgin and scite. With Apache2 and MySQL as well.

jwbrase:
No, there isn't any dust. I keep it clean and have a very nice box with good cooling. I've run speedfan in windows while gaming and there haven't been any issues, though I haven't checked the temps while running linux. Though if gaming doesn't throw it over the edge, I doubt firefox would :)

---

### Post by beno1990 on 2009-03-07
The current version of Pidgin has a few bad bugs, actually. It's been known to cause Xorg freezes, in fact it's caused one a couple of times on my box too.

I'm suspecting that Pidgin might be the cause. But the good news is that these bugs are being fixed for the next version.

---

### Post by Gidgidonihah on 2009-03-07
Oh ok. Thanks for the tip. I'll try not running pidgin and see if that helps.

---

### Post by Gidgidonihah on 2009-03-16
Okay, once again today I was working and it froze.

Ctrl-Alt-Backspace didn't do anything.

Pidgin wasn't running at the time and I didn't see anything in the Xorg log. I've attached it for reference. Any other ideas?

---

