---
title: "Website Popularity, how to boost it"
date: 2009-01-25
forum: General Help
---

### Post by clegends on 2009-01-25
Hi folks, got a question for the web gurus out there. I know there are various ways to boost your web popularity (making links to others websites being one of the foremost), however I've had an idea for awhile I'd like to try, and need some advice about scripting to make it work.

Firstly, I could be way off about how the web, and google in particular work. If I am, please let me know. As I understand it, google searches are based on popularity, and to a lesser degree, on site metatags. Say I have a site advertising kids birthday parties, and I set the metatags to 'Birthdays' 'Kids' 'Parties' 'Fun' and the local area I live, 'Melbourne'. So far as I know these tags are useless for Google until enough people visit the site to make it show up on a search. Even then, if there are more popular sites, mine will appear way down the list. Of course I could advertise in the paid section, but that gets expensive, and is also easily outranked.

When I first started my business, no-one could find me on the web. After a few weeks of setting my browser home page to my site, this changed. You could then google 'Curious Legends', and find us. Of course, we were one of the only groups under that name, so it was easy. 

So this is what I'm asking. 
1. Is there a way to create a script to 'ping' my site in a way that mimmicks web traffic, and to bypass web browsers to do it?
2. How would I create such a script, and where would I find the information to do it?

I tried creating something similar in a simple bash script with Firefox:
```

#!/bin/bash

firefox (website) &
firefox (website) &
firefox (website) &
firefox (website) &
etc.....

```

And found that while an instance of firefox opened with multiple tabs, eventually it chewed up my system resources and spat them out. Would 'pinging' my website provide the same effect as a web browser finding it, and use less system resources? How would I go about doing this? Could I set it up to periodically ping my site over the next few days, and just forget about it? Do I need to be careful about how I do this so I don't crash my server, computer, or both? 

Thanks people!
~clegends

---

### Post by cprofitt on 2009-01-25
I would not pad your stats... it just is morally wrong to do that.

---

### Post by paultag on 2009-01-25
First of all:  Ouch.
Second of all: D'OH.

1) Looping through app instances is really not that great of an idea, you totally could have used curl or wget if you _really_ wanted the hits.

2) Website traffic has nothing to do with google page rank.

[http://www.webworkshop.net/pagerank.html](http://www.webworkshop.net/pagerank.html) <-- Read up.


Should probably put basic search engine optimization on the checklist of stuff to read up about.

Cheers

---

### Post by clegends on 2009-01-25
Thanks Paultag, that answers my question. I suppose if a shortcut was that easy, everyone would have been doing it. Cheers.

---

