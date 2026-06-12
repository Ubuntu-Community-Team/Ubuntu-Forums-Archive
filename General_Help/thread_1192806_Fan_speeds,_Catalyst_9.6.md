---
title: "Fan speeds, Catalyst 9.6"
date: 2009-06-20
forum: General Help
---

### Post by shade11 on 2009-06-20
I just bought a Radeon HD 4890 a few weeks ago and decided to get it working in Linux. After hearing about the new Catalyst 9.6 drivers being released I decided that now would be the right time to go back to Ubuntu and get my video drivers running properly.

I installed the drivers from AMD's website with no problem at all. But after opening up the Catalyst Control Center I find that there is no manual fan controller.

I hear that people have the ability to set their fan speeds on ATi cards manually in Ubuntu. How would I go about doing that?

---

### Post by khelben1979 on 2009-06-20
Look in this thread: [HOWTO Control Fan Speed tutorial]("http://ubuntuforums.org/showthread.php?t=846480") might be what you're looking for.

Bad of ATi not to include this in their catalyst software for Linux. From my time using the ATi Catalyst for Windows, software for increasing the speed of the GPU core and it's memory has been available for years.

---

### Post by shade11 on 2009-06-20
eeeegggghhhhh, at least it's better than nothing. Damn ATi. Thanks though.

EDIT: For future reference, I found a better method at doing so.

In the terminal, type aticonfig --pplib-cmd "set fanspeed 0 <desired fan speed % 1-100>"

---

### Post by khelben1979 on 2009-06-21
> **shade11 said:**
> aticonfig --pplib-cmd "set fanspeed 0 <desired fan speed % 1-100>"

That's cool! However, if the card isn't getting good cooling it will probably shorten it's life cycle. So if the cooler isn't doing a very good job, you might consider getting a better one. At least that would be the thing I would do, I think.

---

### Post by Legace on 2009-06-21
> **khelben1979 said:**
> That's cool! However, if the card isn't getting good cooling it will probably shorten it's life cycle. So if the cooler isn't doing a very good job, you might consider getting a better one. At least that would be the thing I would do, I think.

The thing is, if you replace the stock cooler, you will void your warranty..

---

### Post by khelben1979 on 2009-06-21
> **Legace said:**
> The thing is, if you replace the stock cooler, you will void your warranty..

Yes, that's right. Therefore it wouldn't be a good recommendation to anyone except those who knows how to do it.

---

### Post by jlreich on 2009-06-29
> **shade11 said:**
> For future reference, I found a better method at doing so.

In the terminal, type aticonfig --pplib-cmd "set fanspeed 0 <desired fan speed % 1-100>"
Perhaps others knew how to use this but it took me awhile to figure it out. So I thought I would share for those like me that kept getting syntax errors. :confused:

  [COLOR=Red]aticonfig --pplib-cmd "set fanspeed 0 xx"[/COLOR]

Where **xx** is the desired speed.

In my search here is one I found to see your core temp so you know it is where you want it to be.

[COLOR=Red] aticonfig --adapter=0 --od-gettemperature

[COLOR=Black]Hope that helps someone. :) My temp was 67.5C before I was finally able to get fan control. Very happy now that I am not going to roast my card (4870 for those that want to know it works with these cards). ;)[/COLOR]
[/COLOR]

---

### Post by nmsmith on 2009-08-14
Thanks for this. What is the default behaviour of this fan? Is it a preset speed, or temperature-sensitive?

I have the catalyst control centre version 2.6 installed, and xorg-driver-fglrx version 2:8.600-0ubuntu2.

---

### Post by jlreich on 2009-08-23
For my card (HIS 4870) the default seems to be 4%, way too low. I set the fan speed to 45% and it keeps it nice and cool without being too loud.

Edit - While I am here...

If you use "Watermark" screenlet you can add the line below as a custom sensor and get your ATI card temps in the screenlet.

[COLOR=Red]aticonfig --adapter=0 --od-gettemperature[/COLOR]

I had to play around with the font position to get it to look decent because the output is so long and it doesn't wrap well, but it works fine once you play to get it where you like it.

---

