---
title: "Can't set system time"
date: 2009-01-27
forum: Desktop Environments
---

### Post by IainPurdie on 2009-01-27
Hi, I just updated to Intrepid Ibex and for some reason I now cannot set the system time. I'm running the bog standard Gnome interface so I wouldn't expect a problem and had no issues pre-upgrade.

I right-click on the clock and select "Adjust Date/Time". From the popup that appears, I choose "Set System Time" and enter the admin password (or I did, until I told it to remember this for later use).

Then... nothing.

It doesn't crash, I don't get an error. I simply don't get the popup letting me change the time zone. This is a bit of an issue as I travel a lot (left London 7 hours ago, not in Abu Dhabi, will be in Bangkok in the morning with a bus to Cambodia afterwards!) and as a result I do adjust the time zone a lot.

Is there a package I could uninstall / reinstall or something?

---

### Post by utnubuuser on 2009-01-27
Might it be as simple as uninstalling and reinstalling the applet?

---

### Post by mcduck on 2009-01-27
You shouldn't need to change the system time because of traveling. (After all, the traditional Unix/Linux way would be to run the system clock always in UTC, regardless of your local time zone..)

Just add more locations to the clock applet, and you can easily change between them.. Lot easier than messing with the system time and as a bonus the weather information stays correct as well. ;)

---

### Post by IainPurdie on 2009-01-27
Ah, now see:

1) I'm not sure what the name of the applet is... so I can't uninstall/reinstall

2) I do keep the time in UTC, but I need to change the time zone. Which I'd do in the applet that I can't get into!

---

### Post by IainPurdie on 2009-01-27
OK, I just spotted this works a lot differently to Hardy Heron where I used to get a map and I could click on the time zone I was in.

I just added Thailand and the UK to my "Locations" page, but can't find any way to tell the system that I've moved from one to the other. Am I missing something stupidly obvious?

---

### Post by IainPurdie on 2009-01-27
Got it! It's just that the interface has changed A LOT between Hardy and Intrepid. And I mean, A LOT.

The "set system time" button on the "Adjust" panel doesn't open another panel. It sets the time to what you put in the little boxes *on that page*.

Adding the time zones is in the Preferences section, but you then have to LEFT click on the clock and spot the "Locations" triangle at the top to set them. Utterly, completely different from Hardy. I don't know if it's better or worse - it does seem more work. But at least I have the right time on my desktop now.

---

### Post by mcduck on 2009-01-28
> **IainPurdie said:**
> Got it! It's just that the interface has changed A LOT between Hardy and Intrepid. And I mean, A LOT.

The "set system time" button on the "Adjust" panel doesn't open another panel. It sets the time to what you put in the little boxes *on that page*.

Adding the time zones is in the Preferences section, but you then have to LEFT click on the clock and spot the "Locations" triangle at the top to set them. Utterly, completely different from Hardy. I don't know if it's better or worse - it does seem more work. But at least I have the right time on my desktop now.

Actually you can access the locations with two ways, either click the clock applet and under locations-section click "Edit". Or right-click the clock applet and select "preferences". Both ways take you to the same dialog. ;)

What really is different is the ability to set multiple locations, to display times and weather information for many places at the same time, and then changing your own location between them simply by clicking the clock applet and then clicking the "set"-button next to any location you have configured.

I'd say that's definitely better than what previous Gnome versions had.

---

### Post by IainPurdie on 2009-01-29
I've not found how to get multiple clocks at the same time as yet (or do you mean when you open up "locations"?), but I quite liked the graphical interface. It was a lot easier to use than the HUGE drop-down you now get.

As an aside, when I change between the two zones I've got set at the moment, I notice a small graphical change on the map above. It doesn't actually *tell* me anything, but it changes! I'd have thought it was meant to tell me where the location I've picked is on the map, but it doesn't - the little dots sit square in the centre.

*shrug*

I have the right time. That's all that matters!

---

### Post by mcduck on 2009-01-29
Yes, I mean seeing the multiple locations when you click the clock applet and open the locations (I have it open all the time). Having multiple clocks in the panel would eat quite a lot of panel space.. ;)
You need to have coordinates for your locations to show them on the map. The applet knows locations of most international airports so if you choose one of them as your location you'll get all required data automatically. if you simply create a location of your own and set the time zone you need to set the coordinates yourself.

I usually just select the closest airport, as that way I also get weather information.

---

### Post by IainPurdie on 2009-01-31
AH, got you - yes, I saw it asking for coordinates. Top notch. I'll have a fiddle with that when I have a few minutes

---

