---
title: "Firefox - Strange Font Display after Crash"
date: 2009-04-03
forum: General Help
---

### Post by kennycason on 2009-04-03
I am currently running Ubuntu 9.04b.
This error occured after firefox crashed. My default language was Japanese. I logged out then logged back in using english. 

And no all the text in firefox is displayed strangely.
There are large spaces between words, and it doesn't not appear to be aligned like normal English.

I searched and searched google but all the comes up is stuff about html,css,etc for web programming. all of which seem irrelevent.

heres a screenshot:

[IMG]http://ken-soft.com/images/firefox/fontdisplay.png[/IMG]

any help would be greatly appreciated. Thanks.

---

### Post by kennycason on 2009-04-03
I also just found this related post. 
[http://ubuntuforums.org/archive/index.php/t-1103133.html](http://ubuntuforums.org/archive/index.php/t-1103133.html)

The problem was also not solved.

---

### Post by kennycason on 2009-04-03
Problem fixed

[https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/247129](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/247129) 
It's bug with pango-grapfite


remove it and it works fine!

Sorry I didn't notice the solution before posting here.

---

