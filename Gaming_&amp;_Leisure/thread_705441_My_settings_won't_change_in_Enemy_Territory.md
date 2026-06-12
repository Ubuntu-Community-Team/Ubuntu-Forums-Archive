---
title: "My settings won't change in Enemy Territory"
date: 2008-02-23
forum: Gaming &amp; Leisure
---

### Post by Shadowmeph on 2008-02-23
I play ET a fair amount and o course I have Key binds that I use the one thing that I cannot change no is the r_gamma when I play some maps that are a little dark it is nice to be able to see a in the dark even it is a little so I had a key bind that work perfectly on windows but on linux it doesn't work even if I go directly into my confog file and change the r_gamma setting to like 2.5 or even 3 it doesn't change is it a Linux thing .
the other thing is how do I get my Mouse buttons working in game?

---

### Post by Perfect Storm on 2008-02-24
How did you install it? And how do you launch the game?

Also run the game via the terminal which will show you if any error happens.

---

### Post by Shadowmeph on 2008-02-25
I launch the game through the terminal and I checked it but it I don't see  any errors even when I use my key binds the echo shows that my gamma is going up or down but the brightness or for that matter nothing changes

---

### Post by almostlinux on 2008-02-25
That's strange .. I have no issues with gamma change. This may sound stupid, but have you exec-ed your script at all?
Here's the script that I use and it's works fine:

```
 
set gammafix "vstr gammafix1"
bind del "vstr gammafix1"
set gammafix1 "r_gamma default; bind del vstr gammafix2"
set gammafix2 "r_gamma 2; bind del vstr gammafix1"
```

---

