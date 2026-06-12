---
title: "Wireless Triangulation Thoughts"
date: 2009-01-28
forum: Education &amp; Science
---

### Post by affl1cted on 2009-01-28
Hi all,

After spending a few nights hunting down Unsecured Wireless locations, I began to think that there must be a better approach to finding the house in which the modem lies. So I started thinking, and using Pythagoras theorem:
SqRt(a[2] + b[2]) = C
Along with the Law of Cosines:
a = SqRt(b[2] + c[2] - 2bc cos A)

And Applying this to the signal strength on 3 corners of a Block, you obviously have a Right Angle triangle, and 3 Scalene triangles, all of which can be used to give lengths of sides etc. etc.

Its also probably likely that the Unit used in these lengths is Signal strength, ie ##% Signal strength taken from each of the points, or multiple taken across a 30 second time length, then trimmed of inaccurate readings (spikes) and averaged out.

What I'm asking is, Is this a viable method of Triangulating the location of a Wireless Modem, and how would I approach this? Also, can what Ive said above, about taking signal strengths indicate where you might find the modem location? or would it be took inaccurate to use.

Thanks :)

[ATTACH]101342[/ATTACH]

---

### Post by hubie on 2009-01-29
What kind of antenna are you using?  Just the one from a laptop, or do you have one that is directional, such as a [cantenna]("http://www.turnpoint.net/wireless/cantennahowto.html")?

If you have a directional one, then the problem is pretty easy and is just your basic [Radio Direction Finding]("http://www.hvdfa.webhop.net/") problem.

If you are using a more generic omnidirectional antenna, then you need to be careful.  In principle I think what you are suggesting (assuming I understand what you are suggesting) would work, that is, using the signal strength, but this would only be true if you had a transmitting antenna out in the middle of nowhere and you had direct line-of-sight to the antenna.  Your picture suggests many houses with no line-of-sight, so you run the danger of signal reflection and multipath messing up your signal strengths.

The best way to do it is with a directional antenna.

Just out of curiosity, why are you mapping out wireless access points in your neighborhood anyway?

---

### Post by affl1cted on 2009-01-31
At the moment, just the Laptops one. Also, what could/would cause signal reflection? Noting that where I live is rural/urban, and there arent an abundance of people with Wireless, let alone Internet.

To be honest, we wanted the ability to get a strong, unsecured internet signal anywhere in our Country, as sooner of later we will be traveling around a bit, so we feel that using someones unsecured network for online phonebook, google etc. isnt a biggie.

Also, NZ's internet is sketchy at best of times, and weak wireless just makes it worse XD, i think at about 60% signal, we only get 50kb/s at about 1-4am, which is sad lol.

Thanks

---

### Post by hubie on 2009-02-01
Different materials have different reflection and attenuation effects on radio waves.  If you have a wall between you and the access point, the received signal will be different depending on whether it is a concrete or wooden wall.  Similarly, if a house off to the side has nice aluminum siding, it could act as a reflector and bounce a signal around an obstruction.  The effect of all of this depends on the geometry of your layout.  Now the accuracies you are after appear more like determining which house something is in instead of which room, so these effects might not matter all that much.  If nothing else, it sounds like it would be fun to try it out.

I did stumble upon [this paper]("http://guigui.teleco.ulpgc.es:8028/TSI2005-07764-C02-01/Members/david/papers/iwwn06.pdf") that spells out the problem pretty nicely, though it is a bit different than your situation.  That paper starts with known access point locations and is trying to find the mobile user.  In what you propose, you become the access points by moving to known locations, such as the corners of your neighborhood.

A more pessimistic evaluation of wifi triangulation is found in [this thread]("https://forums.hackervoice.co.uk/index.php?showtopic=680"), which not only mentions the problems associated with having a variety of "stuff" around that can confuse your signal, but it also takes into consideration more as to how these wireless access cards work (i.e., the signal you see reported on your laptop might not be indicative of the true signal because it might be considering only the valid data it receives).

In any event, what you are proposing and what you are expecting all sound reasonable.  Certainly it is easy enough to try.  I would start just by considering a known access point, such as one in your house, to see if it would work.  A rough start would be to consider that pdf I linked above and set n=1, S=0, and Lw=0 in their Equation 3.  Calculate a d (distance) for each corner of your block, draw circles around each location with radii equal to d, and see where they all intersect (you could also figure it out analytically by finding where the circles intersect by coming up with the equation of each circle (make one of them at the origin to simplify it a bit) and finding their intersections).

If you were going to try it out, I would do as you suggest by taking a number of values at each point and averaging them to knock down the variability in the received signal.  I would also move the laptop around withing a couple meter box as the data were being taken to help and try to smooth out subtle multipath issues you might get.  If you take some data, post it; it would be fun to play with the data.

---

### Post by affl1cted on 2009-02-02
Well, I also thought for another approach, instead of using triangulations, using circles to find the intersections and use that as a rough guide to a location.

It would be based principally on the same system as the triangulation, except instead of calculating the scalene triangles, you would instead apply the maxstr minus curstr result to the radius, and then build the circle from there.

---

