---
title: "Dell Inspiron 1525 laptop running hot at times"
date: 2012-07-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by cybrsaylr on 2012-07-04
Got this ~4 yr old Dell Inspiron 1525 model # pp29L core2 duo laptop that had a bad HDD. Replaced it with a 250GB Seagate 5400 rpm drive and installed 64 bit 12.04 and all seems to be running fine. 

Then I decide to use it to turn my LED HDTV into a super smart TV. It has an HDMI port. Plug it into the HDTV and it runs that LED TV great, better than my Toshiba laptop that I had to use the VGA port to run the LED HDTV did. Anyways while running YouTube clips and I notice when running it at 720 quality the picture is very good but after awhile the laptop fan starts to kick into high speed and the the bottom of the Dell is getting pretty warm.

Decide to check the 'System Monitor' to see what's going on and note that when running Youtube in HQ 720 mode the CPU usage for both cores is running ~75%! When I drop the YouTube clip, from 720 quality down to 240, CPU usage for both cores is drops down to ~33%. 

Question is is this normal?
Does running at HQ modes cause things to heat up that noticeably?
Will this cause problems down the road and shorten the life of this Dell core2 duo laptop if I continually run it like that in HQ mode?

---

### Post by mikewhatever on 2012-07-04
> **cybrsaylr said:**
> ...

Question is is this normal?
Does running at HQ modes cause things to heat up that noticeably?
Will this cause problems down the road and shorten the life of this Dell core2 duo laptop if I continually run it like that in HQ mode?

1. Yes.
2. Yes. Flash for Linux lacks hardware acceleration, which means higher CPU usage and more heat.
3. It might.

---

### Post by cybrsaylr on 2012-07-05
Thanks for confirming what I suspected mike.

Was playing around with it more and the CPU usage definitely spikes when moving to the HQ settings on YouTube. When staying away from HQ settings laptop didn't get as hot. 

Other than that this Dell laptop seems to be running 12.04 fine.

This didn't happen when using my Toshiba laptop below in my sig, because the Toshiba didn't have any HDMI port, only a VGA port. I noticed with the Dell laptop more HQ settings are available than with the Toshiba laptop. However the Dell looks better when plugged into and running the HDTV.

---

