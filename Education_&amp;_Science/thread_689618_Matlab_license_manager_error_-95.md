---
title: "Matlab license manager error -95"
date: 2008-02-06
forum: Education &amp; Science
---

### Post by ecmerkle on 2008-02-06
I recently installed matlab r2007b on my gutsy box and had a problem with the license manager (I have a single user license).  I figured out the solution and am posting it here in case it can help anyone else.  Maybe it is obvious for more experienced linux users, but not for me...

After installing matlab, I kept getting the License Manager Error -95, which is described here:

[http://www.mathworks.com/support/solutions/data/1-19X9I.html?solution=1-19X9I](http://www.mathworks.com/support/solutions/data/1-19X9I.html?solution=1-19X9I)

I tried all the solutions I could find, and nothing seemed to work.  My problem ended up having to do with the fact that I had renamed my computer in the past.  

1) I went through the menus: System -> Network, then the "General" tab to see my Host name.

2) I then clicked on the "Hosts" tab within the Network menu, and the 127.0.1.1 ip address had a different alias than my host name on the "General" tab.

3) I changed that alias to match my Host name, and the license manager worked.  I could then run matlab.

---

### Post by kbless7 on 2008-02-07
I wasn't aware that r2007b was out for linux. I have it in XP and I love but unfortunately i have to use 2007a in gutsy

---

### Post by ecmerkle on 2008-02-11
I double-checked, and I'm definitely running r2007b.  I ordered matlab for the first time about 3 months ago, and the dvd they sent contains r2007b for linux.

---

### Post by kelowe on 2008-02-15
Many thanks, ecmerkle, worked like a charm for R2007b on 64 bit Gutsy. :)

---

### Post by pould on 2008-02-23
Cool. Thanks for the info.

----------------
[http://kb.x-formation.com](http://kb.x-formation.com)

---

