---
title: "Temperature sensor formula"
date: 2008-06-28
forum: Education &amp; Science
---

### Post by DemonDomen on 2008-06-28
I'm making an electronic thermometer and need some help with two constants:

&#945; = 7.88 10^&#8722;3 K^&#8722;1; &#946; = 1.937 10^&#8722;5 K^&#8722;2

I don't know how much K is or how I should use it.
I tried ignoring it and after that using K=1000 but it doesn't seem to work.

---

### Post by lisati on 2008-06-28
My first thought was maybe that "K" might have something to do with "Degrees Kelvin", but then again, probably not.......

I have a sneaking suspicion that "K" will depend on the particular temperature sensor you are using.

---

### Post by Kevbert on 2008-06-28
Could K be relative air pressure (typically 1000mbar at see level) ?  If so you need to know your altitude and the absolute air pressure in order to work out K.

---

### Post by DemonDomen on 2008-06-28
If it helps, the sensor is KTY 13-5.

> **lisati said:**
> My first thought was maybe that "K" might have something to do with "Degrees Kelvin", but then again, probably not.......

I have a sneaking suspicion that "K" will depend on the particular temperature sensor you are using.

I didn't find anything in the datasheet that would tell me K, so I guess it doesn't depend on the sensor.


> **Kevbert said:**
> Could K be relative air pressure (typically 1000mbar at see level) ?  If so you need to know your altitude and the absolute air pressure in order to work out K.

I really don't know, but I don't think it's about air pressure. The only thing that changes is the resistance of the sensor. I don't think the pressure would be important.

---

### Post by kleeman on 2008-06-28
Point us to the technical doc. It is hard to figure this out without some context. In physics k is either Kelvin or Boltzmans constant neither of which make sense here....

---

### Post by DemonDomen on 2008-06-28
The datasheet is here: [LINK]("www.infineon.convergy.de/upload/documents/techdoc/GF_42/kt_10_.pdf")

---

### Post by kleeman on 2008-06-28
ok that is very clear. The K does indeed mean degrees Kelvin. So you multiply alpha by a temperature (the excess or deficit from 25C) and get a dimensionless factor similarly you multiply beta by the same temperature difference squared and get another dimensionless term add the both to unity and this gives the factor to multiply the sensor resistance at 25C to get the resistance at any other temperature.....

---

### Post by bite on 2008-06-29
From the datasheet:

R T = R 25 × ( 1 + &#945; × &#8710; T A + &#946; × &#8710; T A2 ) = f ( T A )
with: &#945; = 7.88 10&#8722; 3 K^&#8722; 1; &#946; = 1.937 10&#8722; 5 K^&#8722; 2

K is Kelvin. Perform a dimensional analysis of the expression, noting that the part inside round parentheses must be adimensional.

---

### Post by RebounD11 on 2008-06-29
Just out of curiosity do you need this sensor for something related to automotive?... I had a project involving this kind of sensor... and it was appointed to me by an automotive company.

---

### Post by DemonDomen on 2008-06-30
No, I want to put it in my PC and have a display that's showing the temperature.

---

### Post by RebounD11 on 2008-06-30
> **DemonDomen said:**
> No, I want to put it in my PC and have a display that's showing the temperature.

Then you don't need anything extremely fast or accurate... (0.5 degrees Celsius shoud be precise enough and you don't need it to refresh a million times per second). You can use a LM35 (which outputs voltage proportional to the temperature in degrees Celsius) and a fairly cheap ADC (ADC0804... I guess that's absolete ... so maybe ADC0808 or equivalents). If I'm not mistaking there's an application of such sort in LM35's Datasheet. 

You can set the ADC in continous conversion and show the temperature on a 2 digit 7-segments LED display (which is also pretty cheap) for which you need only too decode the ADC output (8 bit ADC is pretty accurate for what you need). It's pretty easy to manufacture and I can give you a hand if you want (Schematic, Simulation or PCB - gerber files). 

PS: The final PCB will be fairly small even if you use THD components only, and you can use the 5V power supply from you computer power cables.

Link to datasheet:
[http://www.datasheetcatalog.com/datasheets_pdf/L/M/3/5/LM35.shtml](http://www.datasheetcatalog.com/datasheets_pdf/L/M/3/5/LM35.shtml)

---

