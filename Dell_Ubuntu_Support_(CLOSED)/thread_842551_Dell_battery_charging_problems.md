---
title: "Dell battery charging problems"
date: 2008-06-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jsned12 on 2008-06-27
I have a Dell Latitude D505. I have recently installed Ubuntu 8.04, and removed Windows XP. Here is my problem, along with steps I have taken trying to fix it:

-Before the switch, my DC outlet in the computer was going bad, so I had to wiggle the power plug to make it power the computer/charge the battery. 

-I had the DC outlet replaced, so I no longer had to wiggle the power plug.

-Then, after the switch, the AC adapter powered the computer fine, but would not charge the battery.

-I sent the computer back to the guy who replaced the DC outlet. He checked that the DC outlet was in properly, and then switched out my hard drive for one with Windows on it to check some other things because he doesn't know how to use Ubuntu. 

-He gave me a new AC adapter to try. The battery had charged to 55% when I got it back, so I assumed it was working. But, it will not charge past 55%, and now I've had it unplugged a little, and it's down to 52% and not charging. The LED light on the system that indicates that the battery is charging is not showing, even though in the top right of the desktop, it says the battery is charging (it just won't go past 52%, and the remaining time is unknown). 

-When I boot up the system, I get a warning message that the AC Power Adapter type cannot be determined. The computer runs fine off of AC, and fine off of battery, but the battery just will not charge. 

Here's what I've determined. The battery charged while the guy had the Windows hard drive in, getting it up to 55%. It won't charge with my hard drive with Ubuntu. So, it seems like the problem is Ubuntu-related. 

When I look at the battery device information, it says that the charge is 52%, the capacity is 67% (poor) (so, I need a new battery soon, but I don't want to get a new one until I can figure out how to charge it). 

Any ideas? 

Thanks.

---

### Post by prshah on 2008-06-27
> **jsned12 said:**
> 

It won't charge with my hard drive with Ubuntu. So, it seems like the problem is Ubuntu-related. 



Here's an easy way to confirm if the problem is in fact with ubuntu. Keep your laptop powered off, plug in the ac adapter and let it charge awhile (1 hour would be nice). Then, start ubuntu and check; has the battery been charged?

Personally, I don't believe ubuntu has anything to do with it; the "wiggle" you speak about is a common fix for a malfunctioning adapter (low/irregular dc output voltage). That could have damaged the battery.

---

### Post by jsned12 on 2008-06-27
Hi, and thanks for the quick reply.

Yeah, it would make sense if it was either a battery or even a motherboard issue, since I've had problems before in that area. The only thing that made me think it was either hard drive or Ubuntu related was that it charged for the guy yesterday when he had the other hard drive in. I'm fairly certain it's not charging when powered off, though I'll check to be sure. So, if this eliminates Ubuntu as a source, then I'm not sure what the problem is...though I wouldn't be surprised if it is in fact a battery or motherboard issue, and there is some other reason it charged with a different, sans-Ubuntu, hard drive. If anyone has any other ideas, I'd be glad to hear them.

---

### Post by Diggs808 on 2008-06-28
> **jsned12 said:**
> ...

-He gave me a new AC adapter to try. The battery had charged to 55% when I got it back, so I assumed it was working. But, it will not charge past 55%, and now I've had it unplugged a little, and it's down to 52% and not charging. The LED light on the system that indicates that the battery is charging is not showing, even though in the top right of the desktop, it says the battery is charging (it just won't go past 52%, and the remaining time is unknown). 


I have a Latitude D820 and my battery behaved in a similar behavior in the months preceding its death.  Its possible that the battery is dying slowly, maybe due to age or the problem you were having with the adapter.  You might boot into the bios and look at battery health.  Similarly you can get the same information by hovering your mouse pointer over the power management app in your panel. It gives a pop up that mentions battery health.  

It seems that Dell batteries are notorious for failing a little over a year old (that way they can sell you a new battery for 200-300 dollars).

---

### Post by unixkids on 2009-01-15
Try a new battery a charger both and detect anything wrong with the bios causing indicating system errors.

---

### Post by liqiong on 2009-08-02
[LEFT]Try a new [battery]("http://www.cheap-laptop-batteries.com/laptop-battery/dell-inspiron-series.html") and detect anything wrong with the bios causing indicating system errors.
[/LEFT]

---

### Post by Qualia on 2010-10-03
It's not Ubuntu, it's most likely the battery or something else hardware related. I had almost the same thing, on my Latitude D520. It would never charge all the way on Ubuntu, but it would say fully charged on Windows XP. 

After a few weeks though, I noticed the maximum battery charge displayed on Ubuntu(it's 9.10 by the way) was steadily declining, but at the same time, XP said that it was holding a normal charge. Eventually, the battery could no longer hold a charge at all, so I had to order a new one from Dell.

So it's probably a battery problem, likely because it's old or (the previous owner?) bought one of those cheap Dell-imitation batteries of the net. Just order a new battery FROM DELL(trust me on this, don't buy them anywhere else, they don't seem to have as long of a battery life, and die quickly), and boot into Ubuntu with it the new battery and AC plug in. After a while, unplug the battery to check its charge or press Fn F3(that will display the basics of the current battery status battery on most Latitudes laptops)

Good luck with your battery issue!

---

### Post by hawthornso23 on 2011-06-23
Be prepared to be seriously annoyed.

Dell chargers have a third wire (the central one). This connects DIRECTLY to the data pin of a memory chip in the charger. The memory chip stores an identification code that identifies the charger as made by Dell.

The BIOS in your Dell computer checks for the presence of this code. If it doesn't see it, it disables the ability to recharge your battery. You can have a perfectly good charger delivering perfect DC current, but if the laptop doesn't see the secret `made by DELL' code on the data wire, it punishes you for not using a Dell charger by refusing to charge your laptop battery.

To make matters worse, the inside of a charger is not a very hospitable place for a memory chip. They tend not to live long in such hot places. And connecting the data pin of a memory chip directly to an external wire is just lousy design. All you need is a single static spark to hit the data wire and zap - you've fried the memory chip with the Dell secret code. If the memory chip dies, your laptop won't recognise that the charger is made by Dell any more and will refuse to charge your laptop.

If you complain to Dell about this, they won't tell you the true nature of the problem. They'll just try to sell you a new charger.

---

### Post by CottonCandy on 2011-07-16
> **hawthornso23 said:**
> Be prepared to be seriously annoyed.

Dell chargers have a third wire (the central one). This connects DIRECTLY to the data pin of a memory chip in the charger. The memory chip stores an identification code that identifies the charger as made by Dell.

The BIOS in your Dell computer checks for the presence of this code. If it doesn't see it, it disables the ability to recharge your battery. You can have a perfectly good charger delivering perfect DC current, but if the laptop doesn't see the secret `made by DELL' code on the data wire, it punishes you for not using a Dell charger by refusing to charge your laptop battery.

To make matters worse, the inside of a charger is not a very hospitable place for a memory chip. They tend not to live long in such hot places. And connecting the data pin of a memory chip directly to an external wire is just lousy design. All you need is a single static spark to hit the data wire and zap - you've fried the memory chip with the Dell secret code. If the memory chip dies, your laptop won't recognise that the charger is made by Dell any more and will refuse to charge your laptop.

If you complain to Dell about this, they won't tell you the true nature of the problem. They'll just try to sell you a new charger.
Thank you for posting  this!! I'm not thrilled at having to buy a new charger, but at least I know the problem now. Thank you! :)

---

