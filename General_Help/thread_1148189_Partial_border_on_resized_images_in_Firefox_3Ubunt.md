---
title: "Partial border on resized images in Firefox 3/Ubuntu 9.04"
date: 2009-05-04
forum: General Help
---

### Post by darkmire on 2009-05-04
You may think that a better place to have posted this would have been on Mozillazine Forums.  It has in fact and the URL is [http://forums.mozillazine.org/viewtopic.php?f=9&t=1042335](http://forums.mozillazine.org/viewtopic.php?f=9&t=1042335) .

Eve since I started using Firefox 3 with Intrepid, Firefox 3 renders any mages that have been manually resized with a partial border around them.  It's starting to get to the point of being annoying.  It doesn't appear when I use Opera or SeaMonkey.  Since going to Jauuty, the problem hasn't gone away, in fact it's now appeared in Open Office 3 as well in Slide Show mode.  All images there have a partial border on the left and top - this never happened in OO2 and doesn't happen in OO3 on SuSE 10.3 . 

The reason I'm posting here is that the problem seems to be limited to certain distros - Ubuntu being one of them.  Pages render correctly in Firefox 3 and Open Office 3 in SuSE 10 and Windows XP.  As it seems a problem specific to Ubuntu, I thought I would post it here to see if anyone else has it or knows of a workaround.  I can't find any similar threads on Ubuntu Forums.

If you're not sure what I'm talking about, there are screenshots in the MozillaZine thread.

---

### Post by rblst on 2009-05-23
I have the same problem using Ubuntu 8.10 and Firefox 3.0.10.

---

### Post by darkmire on 2011-03-30
Well, it's been a long time but I've worked this one out at last.  The problem seems to have been associated specifically with how Firefox and Open Office rendered graphics on machines with Intel 945 graphics chipsets.   

I think the problem was with the drivers as an upgrade to Maverick has solved the problem.

---

