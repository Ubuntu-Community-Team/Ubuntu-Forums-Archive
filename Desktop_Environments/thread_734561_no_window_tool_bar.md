---
title: "no window tool bar"
date: 2008-03-24
forum: Desktop Environments
---

### Post by taekwondosnw on 2008-03-24
ok, i'm new to ubuntu and i kinda know what i am doing but kinda don't... 
i don't seem to have a tool bar type thing anymore...

EXAMPLE IMAGE OF MY PROBLEM
[IMG]http://img143.imageshack.us/img143/8196/errorhz8.png[/IMG]

[IMG]http://img405.imageshack.us/img405/4681/error2hn1.png[/IMG]

[IMG]http://img442.imageshack.us/img442/8800/error3ny9.png[/IMG]

you can see that above file or at the top there is not X to quit or __ to minimize or box to maximize and i can't move the window in less i hold alt down and drag.
Thanks for the help 


-DeRiK!

---

### Post by Hilko on 2008-03-24
This is really weird. I have never seen anything like this before. Looks like a problem with the theme.
You could try changing to another theme: System -> Preferences -> appearance.
Hope it helps.

---

### Post by taekwondosnw on 2008-03-25
[COLOR="DarkGreen"]well i fixed it by upgrading from 7.10 to the new 8.04 i believe it is ( Beta one ) 
so that is all fixed but now i can't get compiz-fusion to be enabled [/COLOR]
[COLOR="Red"](SORRY IF THIS IS POSTED IN THE WRONG PART OF THE FOURMS I'M JUST CONTINUING WITH MY NOVEL OF "MYPROBLEMS" :lolflag: )[/COLOR]

EXAMPLE OF MY PROBLEM

[IMG]http://img377.imageshack.us/img377/65/error12tn5.png[/IMG]

COMPIZ isn't enabled where it says custom. it's not there^^

[IMG]http://img380.imageshack.us/img380/491/error11sl0.png[/IMG]

^^ But i do have advanced desktop effects settings but it won't be enabled inless i can get the above image to display that other thing.


Sorry for my english. it isn't too good :) 

thanks

once again sorry if this is posted in the wrong section

-DeRiK

---

### Post by andyr354 on 2008-03-25
I rebooted this evening and now have the same problem?

Any resolution?

Never had some many problems with an OS!


Andy

---

### Post by andyr354 on 2008-03-25
Ok, after some messing around.  Found out it was the restricted nvidia driver doing it.  I removed it and rebooted, had the borders back.

My mistake was I saw there was a (new version) driver listed below the one I had, installed it back on instead of the one I had... did not work!

I ended up using Envy to get it back to normal now with the nvidia driver loaded so I can run my 1680x1050 monitor.

Andy

---

### Post by firecrow8 on 2008-03-26
I had the same window toolbar. 

I had been screwing around with the /etc/X11/xorg.conf 

I switched the default depth from 24 to 16 and that did it. 

I also have Nvidia. 

haven't had any monitor/video issues since.

---

