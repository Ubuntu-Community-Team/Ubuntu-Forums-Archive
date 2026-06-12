---
title: "America's Army 2.5"
date: 2006-12-23
forum: Gaming &amp; Leisure
---

### Post by lexus_is250_awd on 2006-12-23
Hi all,

I'm new to Ubuntu. I just loaded AA 2.5 successfully and can't get it to run. I installed with
sudo ./"file name" and created a launcher on desktop. When I double click to run it does nothing. ARGH!!!!! Any help?

Am I not running it the proper way in Ubuntu?

---

### Post by WalmartSniperLX on 2006-12-23
> **lexus_is250_awd said:**
> Hi all,

I'm new to Ubuntu. I just loaded AA 2.5 successfully and can't get it to run. I installed with
sudo ./"file name" and created a launcher on desktop. When I double click to run it does nothing. ARGH!!!!! Any help?

Am I not running it the proper way in Ubuntu?

What directory did you install it to? 
Did you leave the settings default, and install the link in /usr/local/bin?

(the game should be in /usr/local/games)

---

### Post by lexus_is250_awd on 2006-12-23
Yes. I left all the defaults. I'm gonna try to install it again.

---

### Post by WalmartSniperLX on 2006-12-24
In that case, after installation, if the links dont work you can always just execute it in the terminal with the simple command 

```
armyops
```

---

### Post by lexus_is250_awd on 2006-12-24
here's the error i get when i run it in console

exec: 50: ./armyops-bin: not found

---

### Post by meborc on 2006-12-24
try armyops without the ./ ... just the text ;)

---

### Post by lexus_is250_awd on 2006-12-24
I did. Can it be that I'm running it on 64 bit Machine?

---

### Post by ChristopherMonahan on 2006-12-24
well from what you said it appears that the link "armyops" links to "armyops-bin" in the same directory, however in your case the the ":not found" says that there is no armyops-bin there, so for some reason it's not installed properly

Any oddities in installation you noticed, try reinstalling it p'haps?

I know nothing of AA, so I can't much help much more than that

---

### Post by lexus_is250_awd on 2006-12-24
Ok. I'll try it one more time. I'll post the results.

---

