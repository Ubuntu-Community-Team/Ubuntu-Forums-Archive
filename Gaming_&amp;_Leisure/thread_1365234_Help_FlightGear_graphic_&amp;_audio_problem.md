---
title: "Help: FlightGear graphic &amp; audio problem"
date: 2009-12-27
forum: Gaming &amp; Leisure
---

### Post by escaflowne on 2009-12-27
I installed FlightGear and I guess it can runs properly but with graphic problem as in the attachment. I don't know how to describe the audio problem, but the engine sounds buzzing.

I already tried adjusting the rendering option, nothing can solve the problem.

My system specs as below:

Processor: Intel Core2Duo 2.4GHz
RAM: 4GB
Graphic Card: GeForce 8500 GT

Please any help?

Thanks

---

### Post by escaflowne on 2009-12-27
I have got the solution from the flightgear forum.

about the graphics 'problem': open the menu Environment --> Time Settings and choose a 'day'time like 'Noon'

about thr audio problem: The workaround is to create an empty file in the home directory with name .alsoftrc and writing this line 
drivers = oss

---

### Post by gazzatav on 2010-07-17
You might also need to install oss-compat from synaptic.

---

