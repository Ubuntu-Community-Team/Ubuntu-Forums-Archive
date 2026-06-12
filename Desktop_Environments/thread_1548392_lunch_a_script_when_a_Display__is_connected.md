---
title: "lunch a script when a Display  is connected"
date: 2010-08-08
forum: Desktop Environments
---

### Post by tawalaya on 2010-08-08
Hi I am currently thinking about buying a new computer; it is supposed  to be a server kind of thing, at least most of the time. So basic HTTP, SQL…
I want it to run all day 24/7... but after looking for a good PC I got a  idea... since any new PC supports HD Video and all I thought why not  add something like Boxee to my little server... but then I thought it  don't have to run Boxee all the time and the graphical user interface  only needs to run when Boxee wants to run or don’t I not need the XServer  to run and display Boxee? 
Anyways Boxee should only lunch when a Display aka HD TV is connected and also turned on. 

So my question is that even possible? To lunch a script if a TV is  turned on and than start the XServer and Boxee (or some other Media  Browser) with it or if not is there a workaround like some key  combination or signal (power button on a remote control) that can lunch  that script? And is there a script that will do this?

It would be great if someone can answer all my questions because if this isn’t going to work a can by a much cheaper PC.

Thanks for all your help

---

### Post by clrg on 2010-08-08
I recommend you to use a server as a server and a client as a client. Linux/GNU is designed to do one thing, but to do that one thing very well. 

Why don't you buy a PC and use it as server, and buy a media receiver and connect it to your TV? That way you have a convenient way of viewing your HD content.

([SIZE="1"]For the sake of being a smartass:

lunch: A meal usually eaten around midday, notably when not as main meal of the day
launch: establish, set up or found
)[/SIZE]

---

### Post by tawalaya on 2010-08-08
mostly because i than had to buy tow devices!! and a switch since i only have one port left on my router (what would be my problem anyway)

and like i tried to write before, I found at least 100 mainboads that already come with a good hd video card like the ION chip sets ... for more or less 50 € more... so, i thought why not ...

and when i look @ ubuntu desktop edition it seams to me that it doesn't be so limited or black and withe as u just proposed? i mean its right that a server and a media box would be better but why do both on one until i have a second box?

So is there a way to do what i won't to do? or du i have to by to separated boxes for that?

---

### Post by clrg on 2010-08-08
Of course it is possible to do it. Anything is possible =D

Try it. If you run into any trouble, I'm sure the forum will be glad to help.

---

### Post by tawalaya on 2010-08-08
Ok it is possible but how can i lunch a script only when a display is connected and how do i lunch a script if a display becomes disconnected again? 

I have found a few post on how to do it when using a wireless remote but it would be munch better withe the display thing? any idears there?

---

### Post by clrg on 2010-08-08
Watch dmesg or /var/log/messages for your display to connect. Then configure it using xrandr or gnome-display-properties.

---

