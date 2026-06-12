---
title: "please save me from myself"
date: 2009-03-12
forum: General Help
---

### Post by sneakk on 2009-03-12
hello all, i have been using ubuntu about a week, i got rid of win vista, and i have been for a week trying to properly install mythtv to play tv. i have purchased an hvr 1600 and i have followed a number of tutorials staying up countless hours ad i cant manage to get it to work..... i admit i am a lot ignorant to some of the stuff ihave read, but I REALLY NEED HELP... i m hoping someone will assist me i have comcast cable with a cable box and again hvr 1600 all i want to do is have it play live tv:popcorn:

---

### Post by pbpersson on 2009-03-12
I know nothing about the topic at hand - but the first questions that come to mind are what specific tutorials you tried, what problems you had, and did you Google those specific problems to see how other people solved them?

---

### Post by sneakk on 2009-03-12
i have tried installing mythbuntu several times only to later find out that my card tv wonder pcie not supported, so i did a little research found hauppage hvr 1600 is suppose to work went out purchased it. well its pci so i lost my slot for wireless card... i thought i just use linksys router with dd-wrt as client bridge no problem...WRONG I WAS....ethernet not  working on intel mother board so 2 usb wireless dongles later im on the net... fresh install ubuntu updates installed i followed this tutorial [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php) to no avail. i then looked the card up on google and found this [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)
but again im new to this, so ifollow along and get up to wher i am suppose to copy the downloaded stuff into /lib/firmware but it tells me i cant copy it or erase the exisiting ones......... i m tire going on 20 hours no sleep..... ireally want to get this workimg i feel so dfeated right now and for the last few days and it doesnt help hearing the wife and kids mocking me..... CAN WE WATCH TV IN THE ROOM YET.... i hope this give s alittle more insight if not pleas instruct me on what i should post and a lot of instructions how to get it......rambling be cause im tired

---

### Post by wildman4god on 2009-03-12
Have you tried xmbc it's like mythtv but I hear its better, i don't know personally because I don't have a computer powerful enough to run it.

check it out here:

[http://xbmc.org/](http://xbmc.org/)

---

### Post by wildman4god on 2009-03-12
> **sneakk said:**
> i have tried installing mythbuntu several times only to later find out that my card tv wonder pcie not supported, so i did a little research found hauppage hvr 1600 is suppose to work went out purchased it. well its pci so i lost my slot for wireless card... i thought i just use linksys router with dd-wrt as client bridge no problem...WRONG I WAS....ethernet not  working on intel mother board so 2 usb wireless dongles later im on the net... fresh install ubuntu updates installed i followed this tutorial [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php) to no avail. i then looked the card up on google and found this [http://www.mythtv.org/wiki/Hauppauge_HVR-1600](http://www.mythtv.org/wiki/Hauppauge_HVR-1600)
but again im new to this, so ifollow along and get up to wher i am suppose to copy the downloaded stuff into /lib/firmware but it tells me i cant copy it or erase the exisiting ones......... i m tire going on 20 hours no sleep..... ireally want to get this workimg i feel so dfeated right now and for the last few days and it doesnt help hearing the wife and kids mocking me..... CAN WE WATCH TV IN THE ROOM YET.... i hope this give s alittle more insight if not pleas instruct me on what i should post and a lot of instructions how to get it......rambling be cause im tired

Also I would suggest getting some sleep, no one can work properly without proper sleep, tell the kids to read a book while they wait TV isn't everything (I barley watch TV at all any more, and I don't mean to sound bossy) once you get that sleep, make sure your card is setted correctly by pushing straight down firmly, then boot up the computer and open a terminal and type:

```
dmesg
```

and post the results of that so I can see if you have the correct driver, the site link you provided said that some users may have problems with drivers.

Edit:

I found a page that has instructions on obtaining and compiling the correct driver for your card:

[http://ivtvdriver.org/index.php/Cx18](http://ivtvdriver.org/index.php/Cx18)

---

