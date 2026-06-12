---
title: "Any word on a &quot;Fuzzy Clock&quot; for Gnome, yet?"
date: 2008-07-01
forum: Desktop Environments
---

### Post by swoody on 2008-07-01
Well I love the fuzzy clock option in Kubuntu, (the clock setting that tells you the aproxomite time in words rather than numbers, for those who don't know about it. e.g. "Quarter after Four" rather than "4:13") I've tried Googling it, and searching on the forums, but the only posts I can find are old and don't have any definitive answers in them. I've also tried to install a couple other clock apps through the repos, with the hope that one might have the fuzzy clock option, but to no avail. I don't have ANY programming knowledge, so I would have no idea how to whip up a code or anything for it, but I could try to help out in any way I can. Any info would be greatly appreciated! Please and thank you all very much!!

-Woody

---

### Post by SEMW on 2008-07-03
I don't use kde, but I can see what you're getting at, and you're right, it looks like a nice idea.  Here's some quick-and-dirty Python code to start you off on the actual fuzzy clock bit:

```

#!/usr/bin/python

import time

currenttime = time.localtime()
minute = currenttime[4] #int
hour = time.strftime("%I", currenttime).lstrip("0") # string with no leading 0s

if 0 <= minute < 3:
    print hour, "o'clock"

elif 3 <= minute < 8:
    print "Five past", hour
    
elif 8 <= minute < 13:
    print "Ten past", hour

elif 13 <= minute < 18:
    print "A quarter past", hour
    
...
```

Etc, etc.  I've done up to 18 past, I'll leave it to you continue it up until 59.

Of course, that's the easy part; the hard part is getting that code into a Gnome panel applet so you can use it as a normal clock.

I'm afraid I won't be much help with that,  but as a workaround for the time being, you could use a terminal as a makeshift clock.  Here's another script, this time bash rather than python:

```

#!/bin/bash

while true; do
	clear
	python ./nicetime.py
	sleep 1m
done
```

I've assumed that you've called the python script "nicetime.py", and that it's in the same directory that that bash script is in.

If you now open a terminal, navigate to the directory you've saved those scripts, and run the bash script, the terminal will act as a makeshift clock.

Of course, a terminal window is rather big and ugly as a clock, but there are loads of tutorials to make your desktop a [nice pretty transparent terminal]("http://rotyyu.files.wordpress.com/2008/02/terminal.png") (taken from [this tutorial]("http://rotyyu.wordpress.com/2008/02/25/transparent-terminal-on-your-desktop/")).  If you follow one of those, select a nice clock-like font for that terminal, and run the bash scipt in it, the result might not be too bad.  Tell us how you get on!

---

### Post by swoody on 2008-07-03
SEMW - Thanks for the help! I finished off the code for the clock, but one question. When the time is 6:45, and I want to display "Quarter to Seven" how would you do that in the code? The way I have it right now, the hour would still say 6. Can you just use a 
```
print "Quarter to", hour+1
```
or something similar? I hope I made that clear enough to understand, lol.

Here's the code all the way up to 60. Is there anything that needs to go at the end, or is that it?

```
#!/usr/bin/python

import time

currenttime = time.localtime()
minute = currenttime[4] #int
hour = time.strftime("%I", currenttime).lstrip("0") # string with no leading 0s

if 0 <= minute < 3:
    print hour, "o'clock"

elif 3 <= minute < 8:
    print "Five after", hour
    
elif 8 <= minute < 13:
    print "Ten after", hour

elif 13 <= minute < 18:
    print "Quarter after", hour

elif 18 <= minute < 23:
    print "Twenty after", hour
    
elif 23 <= minute < 28:
    print "Twenty-five after", hour

elif 28 <= minute < 33:
    print "Half after", hour

elif 33 <= minute < 38:
    print "Thirty-five after", hour
    
elif 38 <= minute < 43:
    print "Twenty to", hour

elif 43 <= minute < 48:
    print "Quarter to", hour

elif 48 <= minute < 53:
    print "Ten to", hour

elif 53 <= minute < 58:
    print "Five to", hour

elif 58 <= minute < 60:
    print hour, "o'clock"
```

---

### Post by SEMW on 2008-07-04
> **smwoodruff0908 said:**
> I finished off the code for the clock, but one question. When the time is 6:45, and I want to display "Quarter to Seven" how would you do that in the code? The way I have it right now, the hour would still say 6. Can you just use a 
```
print "Quarter to", hour+1
```
or something similar?
Good point -- no, as the code is now you can't do that.  *hour* has [datatype]("http://en.wikipedia.org/wiki/Data_type") "[string]("http://en.wikipedia.org/wiki/String_(computer_science)")", so you can't do [integer]("http://en.wikipedia.org/wiki/Integer_(computer_science)") operations to it.

We could just cast the string into an int.  But that wouldn't be very satisfying, as, after all, the code is deliberately using a library function that returns a string (time.strftime) rather than an int-- why do that only to turn it into an int?  

So instead we'll change to using the same library function that we used for minutes (time.localtime()), which returns an int, and we'll do the conversion from twenty-four hour to twelve hour time ourselves.  *currenttime[3] % 12* (% is the modulo operator) would return values from 0 to 11 inclusive rather than 1 to 12 inclusive, so instead we'll do *((currenttime[3] - 1) % 12 ) + 1*, which does what we want.

> Is there anything that needs to go at the end, or is that it?
There's often an *else:* clause after a long string of *elif:*'s, to handle any unhanded cases; but in this case if there somehow are any (e.g. if the library function goes crazy) then the worst that'll happen is that the script will quit without printing anything on the terminal; so I wouldn't worry about it.

Latest code, then:
```
#!/usr/bin/python

import time

currenttime = time.localtime()
minute = currenttime[4] #int
hour = ((currenttime[3] - 1) % 12 ) + 1 #int

if 0 <= minute < 3:
    print hour, "o'clock"

elif 3 <= minute < 8:
    print "Five after", hour
    
elif 8 <= minute < 13:
    print "Ten after", hour

elif 13 <= minute < 18:
    print "Quarter after", hour

elif 18 <= minute < 23:
    print "Twenty after", hour
    
elif 23 <= minute < 28:
    print "Twenty-five after", hour

elif 28 <= minute < 33:
    print "Half after", hour

elif 33 <= minute < 38:
    print "Thirty-five after", hour
    
elif 38 <= minute < 43:
    print "Twenty to", hour + 1

elif 43 <= minute < 48:
    print "Quarter to", hour + 1

elif 48 <= minute < 53:
    print "Ten to", hour + 1

elif 53 <= minute < 58:
    print "Five to", hour + 1

elif 58 <= minute < 60:
    print hour + 1, "o'clock"

```

---

### Post by swoody on 2008-07-04
SEMW - Excellent! Thanks for your help! Now all we have to do is get this into a Gnome panel applet?? lol

---

