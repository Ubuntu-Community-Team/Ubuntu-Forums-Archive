---
title: "Wesnoth 1.4 SOLUTIONS"
date: 2008-03-19
forum: Gaming &amp; Leisure
---

### Post by RagingPoopBall on 2008-03-19
Sup Sup! First post. Well after the long painstaking process of figuring out what's wrong in getting Wesnoth 1.4 to run. Banging my head against the wall for about 3 hours and a whole lot of cigarettes. I'm going to list what I did to fix issues, so no one else will get into the same crap!

1) The requirements! Just type this to get all of them. And my dumb tail was actually getting each one individually

apt-get build-dep wesnoth

2) After running into a configure error.

> Fix the checking for Boost headers version >= 1.33... no
configure: error: Could not find Boost headers version >= 1.33

Did this in the terminal and it fixed the problem

sudo apt-get install libboost-iostreams-dev imagemagick

After that just open up the file on the terminal and do the thing

./configure ;make ;make install

Hope this helps all those people who ran into the same problem I did and big thanks to allonby on the Mental Enema site for his post. BE EASY!

---

### Post by Cappy on 2008-03-19
Getdeb has the newest Battle for Wesnoth as a debian package
[http://www.getdeb.net/app/The+Battle+for+Wesnoth](http://www.getdeb.net/app/The+Battle+for+Wesnoth)

---

### Post by anjilslaire on 2008-03-19
Yes, but the getdeb version doesn't include the new default campaigns...

---

### Post by RagingPoopBall on 2008-03-19
Man I am happy just being able to play 1.4. All the time I took to get the stupid thing going, it was worth it though. Besides, there's so many maps and I don't have time for all of them anyway. I'd rather not dedicate such a vast amount of time to a game when I got other things to hold down. I think whoever views this would agree that they would be happy just being able to play the new version.

---

