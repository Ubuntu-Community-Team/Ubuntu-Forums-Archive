---
title: "Help me Power Router with 12V Car battery"
date: 2009-05-03
forum: Education &amp; Science
---

### Post by HunterThomson on 2009-05-03
I took electronics in high school but that was 8 years ago. So, I could use some help with this one.

I have a Linksys WRT54GS. The AC/DC addapter said the output is "+12V at 0.5A". I need to power it with a car battery that is 12V-14V and like 800 cranking amps... So, like all I need is like a 0.5A resistor to get +12V at 0.5A, Right?

I am asuming "+12V = 12V-14V". Am I correct about this ?

Any knowledge would be vary helpfull. Also, any equations that I need to re-learn.

---

### Post by gnulogic on 2009-05-03
your are correct you can get them at radio shack or online. a +12 volt car battery is +-2 volts it floats from 10 to 14 and averages out at 12 at the battery gets drained the amps go down but so will the voltage a little bit.

---

### Post by HunterThomson on 2009-05-03
> **gnulogic said:**
> your are correct you can get them at radio shack or online.

Cool. Thank you. I'll keep checking back to see if anyone has anything to add.

---

### Post by HunterThomson on 2009-05-03
> **gnulogic said:**
> your are correct you can get them at radio shack or online. a +12 volt car battery is +-2 volts it floats from 10 to 14 and averages out at 12 at the battery gets drained the amps go down but so will the voltage a little bit.

Ok, so all I need to do charge the battery back up when the volts drop below 12? I live on solar and I see the batterys I use at 13.5v when charged then drop down as the get drained.

---

### Post by HunterThomson on 2009-05-03
Ok I found the vary reassuring link that describes the power suply of the WRT54GS 1.0 and 1.1. I have vertion 7.2 but I bet it is close to the same.

[http://kioan.users.uth.gr/wireless/wrt54g/supply.html](http://kioan.users.uth.gr/wireless/wrt54g/supply.html)

---

### Post by HunterThomson on 2009-05-12
Just to complet this.

No, you do not use a resistor.... Realy you don't need  anything. You can just sodder lead form the + & - prongs of the DC/in jack on the bottom of the board.


I did put in a 12V/1A voltage regulator on a breadboard just for redundancy but the WRT54GS and WRT54G alredy have a voltage regulator. As for the Amp's well the router will only pull what it needs so it dosn't madder if the battery can push more. I then stuck two screws through the vent on the router and sodered the wire's to them. That way it was simple to just use aligator clips on the screws sticking out the router to power it. I also used the extra wire from a $5 100' roll form radioshack to make a ~25' powercord with Big 30A aligator clips to connect to the batter on the ground. The battery last about a two weeks for 12hr's a day On.

I put my router with DD-WRT in a 5Gal bucket and then through a rock with a string tide to it up in a big tree. Then I undid the rock tied the string to the 5Gal buket and hosted it up there ~20 feet. Now my WiFi network spans and the whole lot ( 3 acer 1/4 acer wide spaghetti lot) and into the nabers lot. I am at the far end of the lot. The router gets 30% signial and I get 20% form it. (3Mbis/s at gateway I get 1.5Mbis/s)

---

### Post by Bartender on 2009-05-13
Hunter -
I've always wondered about powering low consumption devices with a car battery that's capable of high amps.  Thought that the car battery's massive amp capacity might somehow burn up delicate little things like routers.
But this is working fine for you?

---

### Post by HunterThomson on 2009-05-14
> **Bartender said:**
> Hunter -
I've always wondered about powering low consumption devices with a car battery that's capable of high amps.  Thought that the car battery's massive amp capacity might somehow burn up delicate little things like routers.
But this is working fine for you?

Ya that is what i was thinking. But ya no problems. Been running for... well when did I start this thread....

I just make sure when I clip the cable to the battery that I do it in one motion making sure not to power on/off/on real fast.

---

### Post by hubie on 2009-05-15
One thing you might want to consider is to put in an in-line fuse to avoid any spikes you might get when connecting or unconnecting to the terminals.  All-in-all you should be fine.  What you are doing is no different than using one of those cigarette lighter power plugs to power something.  Usually those power plugs have a fuse built-in.

---

### Post by HunterThomson on 2009-05-15
Ya your right a fuse is a good idea. But heck it is working maybe next time.

---

### Post by samden on 2009-05-15
Good on you, nice to see someone with a practical mind! Now you just need to hope it doesn't rain and soak your router...

---

### Post by HunterThomson on 2009-05-16
> **samden said:**
> Good on you, nice to see someone with a practical mind! Now you just need to hope it doesn't rain and soak your router...

Owe got that covered. I have it sealed up tight in a 5gal bucket and taped up just incase. I also taped the router to the inside of the bucket so if it falls for somereason it stands a good chance of surviving.

---

### Post by HunterThomson on 2009-07-31
> **homemade wind generator said:**
> Yikes! Get it off that car battery! Your battery bank (what your solar panel charges through a controller) should use deep cycle batteries only. A car battery will do two things, one, stop working after only a few draw down, charge back up cycles, or two, actually explode on you. Car batteries are not meant to repeatedly drop down, then charged back up, liike deep cycle batteries are.

All that is true to an extent. The router uses 0.5 Ahr. So, the battery is charged like once a week and a half. So, this is A OK not a problem and I have proven so over the past... when did I start this tread?... 3months.

But ya, if you have a solar system or something and are taking heavy loads you need deep cycle batteries.

One cool thing I learned, these Linksys routers are bulletproof. One time the router was powered on and half submerged in watter because the lid was not closed. I let it dry out and the next day it was working good as new :) Crazy. Owe it also fell out of the tree one time a good ~25' drop.

---

### Post by HunterThomson on 2009-08-01
> **Graco said:**
> I didn't that if you have a very low amp device connected in a solar power configuration, you don't have to use deep cycle batteries, nice to know.

Ya, the thing is that car battery's are not made to "hold" "Amp-hr's" a lot of power. They have vary thin lead plates and a lot of them so they get a lot of service area. This way the battery can give an extreme amount of amps "800 cranking amps" but for a short amount of time. However the thin lead plates don't have the mass "lead atoms" to hold a lot of elections. 

Deap cycle battery's have really thick lead plates "lots of lead atoms" so they can hold "Amp-hr's" a lot of power. However, they don't have as much service area so they can't supply a whole lot of Amps all at once like car batterys.

Also, Car batterys are just low quality design and parts. Deap cycal batterys have a lot more thought put into them and have high quality parts. Basically deep cycle batterys are made to last and car batterys are made to be cheap.


So, ya use a deep cycle battery if your going to go out and buy one but if you have a car battery laying around it will work just fine for a low power device like a +12 0.5Amp-hr router.

[COLOR="Red"]**Also, ya you can hurt/kill yourself with a battery if your a dumbass. If you cross the terminals that thing will fry your hand off in one second.**[/COLOR]So don't be a dumbass and all will be fine.

---

### Post by tgalati4 on 2009-08-01
5-gal bucket is a good idea.  It will also protect it from bears.  

A simpler solution is to use 2-3 12 volt gell cells wired in parallel.  You should get several days of coverage from them.

3 12-amphour batteries will give you 36 hours of wireless for a 1-amp draw.  If your router draws only 0.5 amps then you might get 72 hours.  Gell cells can be charged by a car battery and act as a back-up jump start battery when your car battery runs down.

---

### Post by HunterThomson on 2009-08-02
> **tgalati4 said:**
> 5-gal bucket is a good idea.  It will also protect it from bears.  

A simpler solution is to use 2-3 12 volt gell cells wired in parallel.  You should get several days of coverage from them.

3 12-amphour batteries will give you 36 hours of wireless for a 1-amp draw.  If your router draws only 0.5 amps then you might get 72 hours.  Gell cells can be charged by a car battery and act as a back-up jump start battery when your car battery runs down.

That sounds cool. I have never heard of gell cells.
Also, I think the router is a MAX of 1/2 Amphr so it mite last even longer then 72hrs. Ya, the 5gal bucket is the perfect thing. I taped the router to the bottom of it. This way it is like a hard case so if it falls out of the tree it stands a vary good chance of survival.

---

### Post by tgalati4 on 2009-08-03
Gell cells are used inside uninterruptable power supplies.  You also find them inside emergency lights and alarm systems.  Find a local electronics dealer.  They are pricey.  I just bought 3 for $40 each from allelectronics.com.  Shipping is a killer.

You could also use a motorcycle battery.  It's a wet cell, but inside a bucket, who cares?

Hang Ten
Mainland Howly

---

### Post by HunterThomson on 2009-08-03
> **tgalati4 said:**
> Gell cells are used inside uninterruptable power supplies.  You also find them inside emergency lights and alarm systems.  Find a local electronics dealer.  They are pricey.  I just bought 3 for $40 each from allelectronics.com.  Shipping is a killer.

You could also use a motorcycle battery.  It's a wet cell, but inside a bucket, who cares?

Hang Ten
Mainland Howly

Ya, see that is what makes this in the tree repeater work. It only cost me <$10 with the old car battery. Really could be free. All you need is solder, wire and a breadboard and a voltage regulator for whatever your router needs. Owe, and a 5gal bucket and some battery.

---

### Post by tgalati4 on 2009-08-04
You probably don't need the voltage regulator as the router probably has some power conditioning circuitry already.  Open up the router and look for a 5-pin LM-something chip and do a search to confirm that the router has a regulator in it.  If so, then you have saved yourself $3.

---

### Post by Dark-Star on 2009-08-05
> **Bartender said:**
> Hunter -
I've always wondered about powering low consumption devices with a car battery that's capable of high amps.  Thought that the car battery's massive amp capacity might somehow burn up delicate little things like routers.
But this is working fine for you?

A little clarification on the subject---

The rating on an electronic device (usually in mA, 1A(mp) = 1000 mA) is an indication of the amperage the device *will want to have*. The rating on a power brick or battery is an indication of the *maximum it can give*.

I'll use an example of the wireless router I jury-rigged recently: 

Device wants 12 volts, 500 mA. Power brick supplies 12 volts and up to 3000 mA. Result --- device works perfectly. :KS

The very important thing is that you _match or exceed_ the demand on the device with the supply from the power source (brick or battery) as well as the Voltage rating *exactly*. Too many volts will BBQ the device, too few will not work or work very erratically. 

-=Also=- be *absolutely sure* that, if you are using a wall wart, that it is an AC-to-DC adapter. Some of them simply step down the AC voltage...plug one of those into a DC device and you'll get one serious fireworks show.

---

### Post by HunterThomson on 2009-08-05
> **tgalati4 said:**
> You probably don't need the voltage regulator as the router probably has some power conditioning circuitry already.  Open up the router and look for a 5-pin LM-something chip and do a search to confirm that the router has a regulator in it.  If so, then you have saved yourself $3.

[QUOTE=Dark-Star]A little clarification on the subject---

The rating on an electronic device (usually in mA, 1A(mp) = 1000 mA) is an indication of the amperage the device will want to have. The rating on a power brick or battery is an indication of the maximum it can give.

I'll use an example of the wireless router I jury-rigged recently:

Device wants 12 volts, 500 mA. Power brick supplies 12 volts and up to 3000 mA. Result --- device works perfectly.

The very important thing is that you match or exceed the demand on the device with the supply from the power source (brick or battery) as well as the Voltage rating exactly. Too many volts will BBQ the device, too few will not work or work very erratically.

-=Also=- be absolutely sure that, if you are using a wall wart, that it is an AC-to-DC adapter. Some of them simply step down the AC voltage...plug one of those into a DC device and you'll get one serious fireworks show.[/QUOTE]


Yes, you are both right. I already pointed both points out in this thread before.

[QUOTE=hunterthomson]Just to complet this.

No, you do not use a resistor.... Realy you don't need anything. You can just sodder lead form the + & - prongs of the DC/in jack on the bottom of the board.


I did put in a 12V/1A voltage regulator on a breadboard just for redundancy but the WRT54GS and WRT54G alredy have a voltage regulator. As for the Amp's well the router will only pull what it needs so it dosn't madder if the battery can push more. I then stuck two screws through the vent on the router and sodered the wire's to them. That way it was simple to just use aligator clips on the screws sticking out the router to power it. I also used the extra wire from a $5 100' roll form radioshack to make a ~25' powercord with Big 30A aligator clips to connect to the batter on the ground. The battery last about a two weeks for 12hr's a day On.

I put my router with DD-WRT in a 5Gal bucket and then through a rock with a string tide to it up in a big tree. Then I undid the rock tied the string to the 5Gal buket and hosted it up there ~20 feet. Now my WiFi network spans and the whole lot ( 3 acer 1/4 acer wide spaghetti lot) and into the nabers lot. I am at the far end of the lot. The router gets 30% signial**<<Edit: really only got like 17-20%>>** and I get 20% form it. (3Mbis/s at gateway I get 1.5Mbis/s)[/QUOTE]

**Edit:** I now replaced the GW with an ASUS WL-520gC and DD-WRT Micro_Pluss w/SSH. Now the two routers get ~37% of eachother and the router is getting 35% of my laptop. Now I am like ~500feet form the GW and **I now get full 3Mbs download**.

---

### Post by tgalati4 on 2009-08-06
So now you can surf and surf.

---

### Post by gornokot on 2011-05-04
Ok, guys.

Two years after last post, can anyone drop a report, how much the whole thing worked on battery power without recharging accu (guessing that it had kind of standard capacity)? How fast the capacity dropped without service? I plan to run my h/w 24 hours with eventual recharging and leaving it out of service for 3 months..


I know the formulas for calculating kWh and may estimate that my hardware will run 20 hours on a single brandname "95Ah" accu (ok, really it will be an 35Ah with custom tuning and refurbishing, but it costs lower than a beer keg)...

But, what kind of losses may be expected? All my stuff is +12V, runs on 78xx IC's..

There's an article in Mikrotik wiki, see [http://wiki.mikrotik.com/wiki/Solar_Power_HOWTO](http://wiki.mikrotik.com/wiki/Solar_Power_HOWTO) for details..

---

