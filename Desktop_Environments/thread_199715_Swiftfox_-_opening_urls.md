---
title: "Swiftfox - opening urls?"
date: 2006-06-19
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-06-19
I have discovered swiftfox, and quite like it.  However I am having problems setting it up to work well as a default browser.  I have used "system>preferred applications" to set my default browser command as ~/swiftfox/swiftfox", but when I click on URLs from inside thunderbird it just opens a blank page in a new window of swiftfox (even if I have a current swiftfox window open).

How can I fix this?

---

### Post by FredB on 2006-06-19
Erh...

Try adding "%s" at the end of the command line.

---

### Post by Lunar_Lamp on 2006-06-20
Thankyou - I thought I had tried that, but for some reason I had attempted "%u" instead of "%s".

---

### Post by FredB on 2006-06-20
You're welcome. I'm glad it helped you ;)

---

### Post by missmoondog on 2006-06-20
cripe! a mere technicality! what's up that it can't figure out what you meant? :) (that's sarcasm there)

thanks. i was looking for this info myself.

---

### Post by FredB on 2006-06-20
You're welcome. My pleasure is to help.

---

### Post by eladamri on 2006-06-21
Okay, so far this has helped me get on my way to solving the problem. Thanks for that.

Here's where I'm at now:
I extracted Swiftfox to /home/christopher/.swiftfox/ so when I execute ```
/home/christopher/.swiftfox/swiftfox "http://www.google.com"
``` it works appropriately, pulling up Google in a new tab.
Now, since I want all references of firefox to be redirected to swiftfox I backed up /usr/bin/firefox and replaced it with ```
#!/bin/sh

/home/christopher/.swiftfox/swiftfox

``` This allows me to launch the browser without any problems, but the call ```
swiftfox "http://www.google.com"
``` brings me to my blank homepage.

Is my /usr/bin/firefox referencing the right executable?
The original /usr/bin/firefox is 285 lines and mine is only 3. Is the rest necessary?
Any thoughts on a good solution?

---

### Post by Lunar_Lamp on 2006-06-21
I believe you need to allow it to take arguments. 

My bash scripting is very very basic, but I think you may need to try something like this:

```
#!/bin/sh

/home/christopher/.swiftfox/swiftfox $1
```

That could be/probably is a pile of rubbish though.

---

### Post by eladamri on 2006-06-21
Yup, that worked like a charm.

Thank you.

---

### Post by eladamri on 2006-06-25
Actually I found something that worked better. I'm not sure why I didn't think of this first.

I simply made a sim-link from /usr/bin/firefox to /home/christopher/.swiftfox/swiftfox and left my default browser as firefox %s

That solved all of my issues.

---

### Post by FredB on 2006-06-25
[QUOTE=eladamri]Actually I found something that worked better. I'm not sure why I didn't think of this first.

I simply made a sim-link from /usr/bin/firefox to /home/christopher/.swiftfox/swiftfox and left my default browser as firefox %s

That solved all of my issues.[/QUOTE]

It was an answer indeed. But we always searched what is really under our eyes ;)

---

