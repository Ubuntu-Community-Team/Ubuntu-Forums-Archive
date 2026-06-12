---
title: "ubuntu virgin can't get wireless working on XPS M1710"
date: 2007-12-01
forum: Dell  Ubuntu Support
---

### Post by cotc2001 on 2007-12-01
Ok this is the first time i've ever played or used Ubuntu (or any other type of linux) but after getting so frustrated with Vista i thought i'd give it a go as for years i've been wanting to have a crack at linux

So installation of ubuntu onto the Dell XPS M1710 and after fiddling around withe the gfx card drivers i finally got it to the 1920 x 1200 res screen that im used to.

But the final hurdle is getting it to recognise the Dell wireless 1500 draft N wifi card that is in the machine.

Can anyone give me any pointers (keeping in mind that i've not been able to learn how to install any drivers yet)

I've had a look at the restricted drivers manager as was recommended in one of the posts but nothing in there (apart from Nvida driver)

Im sure I will have lots of questions later but would really like to get this one done first so I can stop having to switch to vista just to look up answers on the net.

---

### Post by Skuzniak on 2007-12-01
If you follow the steps in this thread (just replace the downloaded driver with the proper one for your card), it should get your wireless up and running.

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

---

### Post by cotc2001 on 2007-12-02
Nope still cant get it to work I followed the tutorial to the letter.
got past point 4 and it does say that

> bcmwl6 : driver installed
 device (l4E4@4328) present

but no wifi light comes on and if i do

> sudo iwlist scanning

I get 

> lo Interface doesn't support scanning
eth0 Interface doesnt support scanning
I have to apologise im a completley new at linux (far too much time on amigas and then PC's) but would really like to get the oppurtunity to get up and running so i can delve in more rather than having to switch to my pc to find answers on the forum

---

### Post by cotc2001 on 2007-12-02
Ok found my problem.
Although I followed the instructions to the letter on that post the mistake i made was to download the vista wireless network drivers (as that was what came preinstalled with the laptop) rather than the XP wireless network drivers from dell.

Ok so it wasn't to the letter because if I had then i would of downloaded the correct driver.

Well im a happy chappy now - off to explore the world of ubuntu (next stop beryl)

---

### Post by Skuzniak on 2007-12-02
Good to hear you got it working. :)

---

