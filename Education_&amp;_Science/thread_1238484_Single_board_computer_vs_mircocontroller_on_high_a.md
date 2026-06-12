---
title: "Single board computer vs mircocontroller on high altitude balloon"
date: 2009-08-12
forum: Education &amp; Science
---

### Post by hammeraxe on 2009-08-12
Hello, everyone!

I was wondering where to post this and somehow these forums seemed the right place, even though the question is not entirely Ubuntu-related.

We are doing project here, which involves constructing a high altitude weather/sounding balloon. The payload consists of various sensors along with GPS for recovery and communications equipment. So there must be something that coordinates the action of all this. That's right, a computer.

I am not sure, though, what is a better choice. There are these single board computers that are used in routers and other embedded applications. One of these ([http://soekris.eu/shop/index.php?language=en]("http://soekris.eu/shop/index.php?language=en")) should do the trick, when properly loaded with some lightweight linux distro. This is a bonus as programming becomes just as easy as on a desktop machine (well, almost).

Yet SMCs are rather pricey when compared to microcontrollers such as one of these [http://www.atmel.com/products/AVR/default_picopower.asp?source=home]("http://www.atmel.com/products/AVR/default_picopower.asp?source=home")
Budgeting is important, but I have no experience with microcontroller programming and viewing the manual was quite frustrating as I didn't get much of it. Moreover, i have no idea how to make it to process data from the GPS, say. Then again, I'm a fast learner :D

Does anyone here has any experience with something like this? Could you please advise me on the best choice or at least give some pointers to put this all together?

---

### Post by hubie on 2009-08-13
What are your instrument requirements?  How does each instrument talk?  RS232, ethernet, etc.  Do they operate autonomously, or do they need to be controlled by the computer?  What about the data, is it recorded by each instrument, or will it need to be stored on the computer?  The answer will probably be determined based on how many serial ports, usb ports, storage media, etc. you need to get it all working.

---

### Post by ahmatti on 2009-08-14
Have a look at FOX Board [http://foxlx.acmesystems.it/?id=4](http://foxlx.acmesystems.it/?id=4), its an embedded linux board with fairly good communication options. They have a GPS/GPRS Application kit for the board as well and even a TUX case :)

I have never tried this myself, but the website has some cool projects listed such as "FOX board in the air", that I think you'll find interesting [http://foxlx.acmesystems.it/foxlx_acmesystems_it/00033/foxintheair.pdf](http://foxlx.acmesystems.it/foxlx_acmesystems_it/00033/foxintheair.pdf).

---

### Post by hammeraxe on 2009-08-14
The cameras are USB with no internal storage and the GPS is USB as well, none of these have dedicated power supply. As to temperature and pressure probes, we have not bought anything yet. :/ I just want to make sure that everything works smoothly.

I have a Greisinger temperature sensor in mind, but it has a 3.5mm plug like the ones they use for audio. I couldn't find any info on their site on how to interface with it or whether they provide any software for doing that.

The FOX board actually looks really nice, yet I would  need additional USB ports. I wonder if the system would support a USB hub. :confused:
And the fact that it supports Python is great, so the webcam part should be clear for me. Just capturing frames from time to time and saving them somewhere (probably to another USB device).

It seems that the most challenging part could be the radio telemetry, though...

---

