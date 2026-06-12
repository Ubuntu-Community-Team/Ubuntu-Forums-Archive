---
title: "lincity windmills"
date: 2008-03-29
forum: Gaming &amp; Leisure
---

### Post by billybag on 2008-03-29
for some reason my lincity-ng is missing the help/info for WINDMILLS.

anyone care to post the info/help for it. i dont know anything about them except they produced some electricity. i also dont know why some of them spin/work and some of them dont

thanks

---

### Post by deveras on 2009-07-15
Hello my good man. One year and a few months and days later here...
I enjoy the game so much that i registered here to get back to you on this :)

So go to your installation folder, or if you are unsure where it is do:
[B]sudo find / -iname lincity*
[/B]
I found my instalation in /usr/share/lincity-ng/

go to the folder help (on my pc is /usr/share/lincity-ng/help so)

**cd /usr/share/lincity-ng/help**

edit the wildmill.xml file

**sudo vi wildmill.xml**

Go to this line:
 <li><a href="powersolar">Solar power station</p>

Make it:
 **<li><a href="powersolar">Solar power station</a></li>**

Then the manual should work.

---

