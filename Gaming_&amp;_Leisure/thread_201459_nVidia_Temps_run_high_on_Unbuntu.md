---
title: "nVidia Temps run high on Unbuntu"
date: 2006-06-21
forum: Gaming &amp; Leisure
---

### Post by lleonard on 2006-06-21
I have an eVGA 6800GT card, and it seems to run **much** hotter running OpenGL programs on Ubuntu that it does running directx games on Windows. I am running 6.06 with the 686 kernel (2.6.16-25) and nVidia 8762 drivers (P4 2.66 1.5 gig RAM, blah blah blah).  

Running World of Warcraft the thermal monitor easily goes in the upper 80's C on Unbuntu but never goes above 75 or so on Windows.  And glxgears just climbed to 95 deg C before I closed it.

Does anyone else experience this?  

I know there was an issue with the nVidia driver a few versions back where it was misreporting the core temperature, but supposedly that bug was fixed.

I know the default setting for the driver is that it doesn't throttle back the GPU until the core hits 120 but I don't like the idea that running graphics apps on Ubuntu is going cause these high temps.

---

### Post by mkw87 on 2006-06-23
Sounds like your card has some pretty bad cooling, are you sure the fan is still spinning?  The only time I've seen a card hit the 90's is when a temp sensor probe got stuck in my fan and made it stop spinning while I was running 3DMark, I watched the temp climb to like 94 then the comp shutdown.

---

### Post by tseliot on 2006-06-23
You can try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14]("http://www.nvnews.net/vbulletin/forumdisplay.php?f=14")

---

### Post by handy on 2006-06-23
I have a 6800gt too, driver is 1.0-7667, this one is on Breezy 5.10.

So, I checked it out with 10 min's of glxgears -printfps:

Core Temp peaked at 80 C

Ambient at 52 C

Then I removed the card & blew the dust out with compressed air (being careful to keep the fan stationary, so as not to damage it by over reving it)

Same test, new scores:

Core Temp now peaked at 72 C

Ambient at 47 C

I have a heatpipe cooler to install on the card.  I do it later to day & update for those that are interested.

I'll also check it in Dapper with the latest nVidia driver.

---

### Post by Bokonon on 2006-06-23
I have to agree with you on the temps, but unfortunately, I can't get sensors to work to verify.

One advantage windows has is that I can undervolt my CPU and the GPU has a shared cooling pipe with the CPU, so less heat from the CPU results in more cooling for the GPU.

The reason I am pretty certain my CPU and GPU run hotter in Ubuntu is that the sticky pads for my laptop feet have "melted" after a long day of use in linux.  One is by the GPU and the other by the CPU.

Maybe it is time to check around for sensors and Dell laptops again.  Maybe there is an updated guide.

---

### Post by lleonard on 2006-06-23
The fans on the video card and case are all working fine, as far as I can tell based on outflow of air and the sound of the eVGA card's fan.  The case has been open in the last couple months, but I'll open it up again and check things out.

What is interesting to me is that similar temperature increases for WoW don't happen when I run it on Windows (I dual boot).

---

### Post by handy on 2006-06-24
[QUOTE=lleonard]
What is interesting to me is that similar temperature increases for WoW don't happen when I run it on Windows (I dual boot).[/QUOTE]

Could there be a discrepancy between the 2 **nVidia Settings** software, running under the 2 OS's?  Just a thought...

---

### Post by handy on 2006-06-24
[QUOTE=handy]I have a 6800gt too, driver is 1.0-7667, this one is on Breezy 5.10.

So, I checked it out with 10 min's of glxgears -printfps:

Core Temp peaked at 80 C

Ambient at 52 C

Then I removed the card & blew the dust out with compressed air (being careful to keep the fan stationary, so as not to damage it by over reving it)

Same test, new scores:

Core Temp now peaked at 72 C

Ambient at 47 C

I have a heatpipe cooler to install on the card.  I do it later to day & update for those that are interested.

I'll also check it in Dapper with the latest nVidia driver.[/QUOTE]

I have fitted the **Thermaltake Schooner Fanless VGA Cooler with heatpipe technology. P/N:CL-G0009**

I  ran glxgears -printfps, for hours with the following results:

It took 13 minutes to hit the Core Temp 92 C Red Line!

Core Temp, maxed out at 98 C

With Ambient reaching 82 C

It ran at these high temperatures for hours, before I cancelled glxgears.

I am dissapointed in the cooling capacity of the fanless solution.  I will run it on Dapper with the latest driver & see if there is any difference.

---

### Post by handy on 2006-06-25
[QUOTE=handy]I have fitted the **Thermaltake Schooner Fanless VGA Cooler with heatpipe technology. P/N:CL-G0009**

I  ran glxgears -printfps, for hours with the following results:

It took 13 minutes to hit the Core Temp 92 C Red Line!

Core Temp, maxed out at 98 C

With Ambient reaching 82 C

It ran at these high temperatures for hours, before I cancelled glxgears.

I am dissapointed in the cooling capacity of the fanless solution.  I will run it on Dapper with the latest driver & see if there is any difference.[/QUOTE]

I've run the fanless cooler on the 6800gt for hours now, with glxgears -printfps running, in Dapper, on the current nVidia driver 1.0-8762:

Core Temp Peaked @ 102 C

Ambient Temp Peaked @ 85 C

An interesting thing was that my glxgears speed were about 700 fps faster on average than the older driver under Breezy.  

700 fps faster & 4 degrees hotter - I guess as the drivers improve the cards will run hotter...

This driver says it slows down the GPU at 120 C!  I'll give it a workout in UT2k4 & GW & see what happens.

---

### Post by handy on 2006-06-29
Guild Wars, on the Breezy fanless setup, runs at around 80 C.  Which is acceptable to me.

---

