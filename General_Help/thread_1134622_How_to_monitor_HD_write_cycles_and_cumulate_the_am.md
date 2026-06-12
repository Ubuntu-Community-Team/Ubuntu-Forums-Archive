---
title: "How to monitor HD write cycles and cumulate the amount ?"
date: 2009-04-23
forum: General Help
---

### Post by Browser_ice on 2009-04-23
Back in January, I had succeeded in creating a persistent USB key Kubuntu to use at the office, that I can boot off of it just like it was a normal HD.

I have received today an answer from the maker of my USB key (OCZ technology) for my specific model (Rally 2 8Gb). I was told that the life expectancy of it is 5000 write cycle.

This is good news but I want to know how it would be possible to have a monitoring script running on my Kubuntu that would somehow monitor and cumulate the write cycles done so I would know when I am getting close to that 5000 cycles.  I do not want to wind up with a non working USB key and/or have a lost of data because I past that point and did not know.

P.S.: the only reason why I have Kubuntu on my USB key is that the office does not want me to change any PCs and the tools I need for my office projects are free in Linux but in Windows, the office does not want to pay for the licenses.

---

### Post by sgosnell on 2009-04-23
Don't worry about it.  That means 5000 write cycles for every single cell, but the drive should use wear leveling, which means it writes to a different cell each time, so the wear is even across the drive.  To write 5,000 times to every cell on the drive, you need to start now, writing constantly, and come back in a few years.  I've never heard of a flash drive worn out by writing.  Plus, you would have to write the count to the drive on every write, meaning it would wear out much more quickly than if you weren't doing the monitoring.  

In short, you have many more important things to worry about, such as an alien spacecraft abducting you, or the sun dying.

---

