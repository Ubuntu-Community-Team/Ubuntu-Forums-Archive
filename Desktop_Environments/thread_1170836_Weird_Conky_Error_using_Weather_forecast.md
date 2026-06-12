---
title: "Weird Conky Error using Weather forecast"
date: 2009-05-26
forum: Desktop Environments
---

### Post by archeryguru2000 on 2009-05-26
I've never really noticed this error message before, as I use a startup script to execute my conky.  However, upon testing some new changes using my CLI, I've noticed the following output;

```

$: conky -c ~/Conky/conkyweb &
[1] 17198
Conky: desktop window (10000b3) is subwindow of root window (1a6)
Conky: window type - normal
Conky: drawing to created window (3c00001)cfile$: 
Conky: drawing to double buffer
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  58 (X_SetDashes)
  Value in failed request:  0x0
  Serial number of failed request:  13526
  Current serial number in output stream:  13531

```

Is there anything to this error?  I do receive (only occasionally) some "extra" lines on the screen every now and then.  I'm not sure if I'm able to decipher the error message.  If anybody has any useful info, I'd greately appreciate it.

I've been able to take a screen capture of the lines (when they occur).  I assume that there is a connection between the error message and the lines since they seem to occur together.

Thanks
~~archery~~

---

### Post by Sarai the Geek on 2009-05-26
> **archeryguru2000 said:**
> I've never really noticed this error message before, as I use a startup script to execute my conky.  However, upon testing some new changes using my CLI, I've noticed the following output;
...
Is there anything to this error?  I do receive (only occasionally) some "extra" lines on the screen every now and then.  I'm not sure if I'm able to decipher the error message.  If anybody has any useful info, I'd greately appreciate it.

I've been able to take a screen capture of the lines (when they occur).  I assume that there is a connection between the error message and the lines since they seem to occur together.

Thanks
~~archery~~

Can you post your .conkyrc and any bash scripts you might be using?

---

### Post by archeryguru2000 on 2009-05-28
Here's the conkyForcast script.  Let me know if you see anything... out of the ordinary.  I've also posted my e-mail script just in case there's something wrong with it instead.

Thanks,
~~archery~~

---

### Post by Sarai the Geek on 2009-05-29
Well, I tested your script and it made conky, if you'll pardon the pun, go wonky. Are you using Kaivalagi's weather script?

Also, can I get your whole conkyrc, not just the weather section?

---

### Post by archeryguru2000 on 2009-05-30
> **Sarai the Geek said:**
> Well, I tested your script and it made conky, if you'll pardon the pun, go wonky. Are you using Kaivalagi's weather script?

Also, can I get your whole conkyrc, not just the weather section?

I'm actually visiting my parents at the moment.  Yeah, I know... I should be conversing with them instead of searching the net.  Anyway, when I get back to my laptop I'll post the entire script.  And, yes (I think), I'm using Kaivalagi's weather script.

~~archery~~

---

### Post by archeryguru2000 on 2009-05-30
Here's the entire conky script.

~~archery~~

---

### Post by Sarai the Geek on 2009-05-30
> **archeryguru2000 said:**
> Here's the entire conky script.

~~archery~~


I'm not sure K's weather script supports the use of templates. In any case, I got it working (at least on my end) with this somewhat more cluttered conkyrc. It should look the same, though, try it out-

---

### Post by archeryguru2000 on 2009-06-05
Umm, no go.  Still have the lines showing after first update interval.  I'm gonna play around (again) with my settings.  I think I'll first remove one section at a time (Forecast, E-Mail, Network Connection).  This ought to narrow my focus on which area the problem is occurring in.  I'll keep you posted on my progress.

By the way, thank you very much for the assistance thus far.  I do appreciate it.

~~archery~~

---

### Post by archeryguru2000 on 2009-06-05
I've noticed an error that may (or may not) have something to do with the lines showing up.  When I run conky from my CLI, I receive this error message after a few update intervals.

```

$: X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  58 (X_SetDashes)
  Value in failed request:  0x0
  Serial number of failed request:  30513
  Current serial number in output stream:  30516

[1]+  Exit 1                  conky -c ~/Conky/conkyweb

```

Is anybody able to make any sense of this error message?  I'll keep poking around to see if I can reduce the error any further.

~~archery~~

---

### Post by archeryguru2000 on 2009-06-05
Ok!  I've found that when I delete the following line of code the horizontal lines disappear:

```

${execpi 1800 conkyForecast --location=<location near me> --template=<link to my template>conkyForecast.template}

```

Now onto debugging my forecast template.

~~archery~~

---

### Post by Sarai the Geek on 2009-06-05
> **archeryguru2000 said:**
> Ok!  I've found that when I delete the following line of code the horizontal lines disappear:

```

${execpi 1800 conkyForecast --location=<location near me> --template=<link to my template>conkyForecast.template}

```Now onto debugging my forecast template.

~~archery~~

Um, like I said, I'm not sure that the conkyforecast script even supports the use of templates. That's why, in the conkyrc I uploaded for you to try, I didn't use the template... did you make any changes to the one I provided prior to testing it?

---

### Post by archeryguru2000 on 2009-06-05
I most certainly did use your script and there was zero change to the appearance... including the vertical lines showing up after each update interval.  I'm quite sure that my using templates is not the problem.  I've always used these templates.  After changing positions and appearances of my conky (windows, fonts, symbols, etc.) is when I noticed the mysterious bars showing up.

Please do not get discouraged, I do appreciate your help with this.

Thanks,
~~archery~~

---

### Post by archeryguru2000 on 2009-06-05
However, if there has been some sort of an update that challenges the use of templates.  Then my scripts may be rendered... useless!  I'll continue to investigate.

~~archery~~

---

### Post by Sarai the Geek on 2009-06-05
> **archeryguru2000 said:**
> However, if there has been some sort of an update that challenges the use of templates.  Then my scripts may be rendered... useless!  I'll continue to investigate.

~~archery~~

Well, here's what's got me confounded: you managed to show quite well that the problem seems to stem from your weather layout, but when I tested your weather layout it worked fine for me! So I'm stumped... You might try reinstalling K's weather script, perhaps an update got botched?

---

### Post by archeryguru2000 on 2009-07-01
WOOHOO!  \\:D/  I fixed the problem with the vertical lines.  Apparently putting my weather forecast into an if statement created some sort of confusion with conky (I have absolutely no clue why though).

What happened was... I was tired of seeing a blank spot on my screen when I would take my laptop somewhere with no internet connection.  This would happen (the blank spot that is) because my weather forecast would try to acquire data from the net but would not succeed.  So, like any good programmer (which I am not, by the way), I decided to invoke an if statement to check for a connection.  I already had such a loop for my internet activity monitor and my e-mail monitor (both in conky).  However, for some reason why, placing my weather forecast in such a loop was less than successful.  Anyway, I may try to figure out a work around for this... but probably not any time soon.  ;)

Thanks again for your assistance Sarai.  This thread isn't truly solved, for I still do not know why those lines show up when my weather forecast is presented within a loop.  However, I now know how to get rid of those pesky lines.

~~archery~~

---

