---
title: "What happens when your CPU overheats?"
date: 2009-12-22
forum: Desktop Environments
---

### Post by Caps18 on 2009-12-22
I am working on building a fanless system, and was wondering what risk there is to the CPU is it does get too hot?  Will it shutdown or stop working and allow itself to cool, or will it meltdown and permanently damage the chip?


The CPU is an AMD Athlon 64 X2 (3.6 Ghz), and it will just be running Mythbuntu (HD video will be the hardest thing it will run).


Thanks

---

### Post by Kraust on 2009-12-22
Well in my experience, I tried to use an Old CPU without an HSF and it endded badly.

On boot Grub acted strange which led to a bad burning smell and resulted in a fried CPU.

The CPU at touch alo burned me.

---

### Post by sailthesea on 2009-12-22
Nasty smelling blue smoke and tears!:)

---

### Post by iponeverything on 2009-12-22
I think it would take that cpu about 1 minute to start cooking without a fan, load or not.

If you want to make a fan less system, look at doing it with a low power mobile cpu like intel c2d SU9400 or SL9400. I don't think that an atom would have the power you would need.

---

### Post by Kraust on 2009-12-22
Could go with the Sempron 140. It's an AM3 Processor, only 45W and got some good HTPC reviews.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103698](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103698)

---

### Post by schmolch on 2009-12-22
45nm AMD Processors can easily run fanless.
I did it with 2 AMD64-X2 at 2.3 and 2.7GHz.
Idle they are below 35C and under load at full clockspeed they go to a max of 65C, which is way below what my Laptops will run at when taxed.
You need a big Heatsink and a little bit of airflow from the Power-Supply, thats all.

---

### Post by schmolch on 2009-12-22
If a CPU overheats it reduces its clock and in the worst case a temperatur sensors inside the CPU shuts it off immediately. So unless you run it without any heatsink at all you are pretty safe.

---

### Post by Cuco3 on 2009-12-22
> **Caps18 said:**
>  Will it shutdown or stop working and allow itself to cool, or will it meltdown and permanently damage the chip?


The CPU is an AMD Athlon 64 X2 (3.6 Ghz), and it will just be running Mythbuntu (HD video will be the hardest thing it will run).


ThanksIIRC it'll freeze the computer about 15-30 seconds in but will continue to be powered on. It's at this time that you'll need to turn off the computer and let it cool off completely in order to avoid killing the cpu.

---

### Post by judge jankum on 2009-12-23
Blue smoke, tears, and loud cussin'

---

### Post by realzippy on 2009-12-23
> **schmolch said:**
> If a CPU overheats it reduces its clock and in the worst case a temperatur sensors inside the CPU shuts it off immediately. So unless you run it without any heatsink at all you are pretty safe.

Yes,newer Intel CPU would do so.but this old AMD 64 would die.

---

### Post by schmolch on 2009-12-23
> **realzippy said:**
> Yes,newer Intel CPU would do so.but this old AMD 64 would die.

That's bull, CPUs have builtin Diodes since a long time and a X2 is not that old.
Btw. a 3.6GHz X2 does not exist so maybe he meant to say 2.6GHz.

---

### Post by apswartz on 2009-12-23
My Dell Inspiron 1420 overheated once and the computer automatically popped up a message and began a shutdown sequence. I am running Kubuntu 9.10

---

### Post by realzippy on 2009-12-27
> **schmolch said:**
> That's bull, CPUs have builtin Diodes since a long time and a X2 is not that old.
Btw. a 3.6GHz X2 does not exist so maybe he meant to say 2.6GHz.

AMD Athlon 64 X2 CPUs use the Tcase to determine their temperatures, and not TJunction.G1 and G2 steppings are buggy,wrong temps.
If you disabled thermal throttling in the BIOS,the CPU can easily die.Intel
cannot.


@ schmolch:
Think before posting and mind your pleasantness...

---

### Post by aircos on 2009-12-27
youtube your friend

to show u its posabel [http://www.youtube.com/watch?v=C4YPcDeyYd0]("http://www.youtube.com/watch?v=C4YPcDeyYd0")

to show u whats probertly is gone happen [http://www.youtube.com/watch?v=ReaAZVd9i3I]("http://www.youtube.com/watch?v=ReaAZVd9i3I")

hope this is helpfull

---

### Post by cascade9 on 2009-12-27
> **iponeverything said:**
> I think it would take that cpu about 1 minute to start cooking without a fan, load or not.

If you want to make a fan less system, look at doing it with a low power mobile cpu like intel c2d SU9400 or SL9400. I don't think that an atom would have the power you would need.

Actually, theres quite a few people running mythTV boxxen for HD playback. It works fine. But I wouldnt get one, if the OP was really going to spend any money at all get a Phenom xxxxe (or a 'black edition' for major underclocking) for AM2/AM2+, or for AM3 one of the Phenom II xxxxe (the 'e' being 'energy efficient', 45watt CPUs) or this- 

> **Kraust said:**
> Could go with the Sempron 140. It's an AM3 Processor, only 45W and got some good HTPC reviews.

> **schmolch said:**
> That's bull, CPUs have builtin Diodes since a long time and a X2 is not that old.
 Btw. a 3.6GHz X2 does not exist so maybe he meant to say 2.6GHz.
 
 Yep. 

> **aircos said:**
> youtube your friend
 
 to show u its posabel [http://www.youtube.com/watch?v=C4YPcDeyYd0](http://www.youtube.com/watch?v=C4YPcDeyYd0)
 
 to show u whats probertly is gone happen [http://www.youtube.com/watch?v=ReaAZVd9i3I](http://www.youtube.com/watch?v=ReaAZVd9i3I)
 
 hope this is helpfull

Ummm....that is really, really, really old. Since the Atlon 64 (socket 939) there is-

> [FONT=Times][SIZE=3][FONT=Times]The processor provides a hardware-enforced thermal protection mechanism.[/FONT][/SIZE][/FONT][http://www.amd.com/us-en/assets/content_type/white_papers_and_tech_docs/31411.pdf](http://www.amd.com/us-en/assets/content_type/white_papers_and_tech_docs/31411.pdf)

> **realzippy said:**
> AMD Athlon 64 X2 CPUs use the Tcase to determine their temperatures, and not TJunction.G1 and G2 steppings are buggy,wrong temps.
 If you disabled thermal throttling in the BIOS,the CPU can easily die.Intel
 cannot.
 
 @ schmolch:
 Think before posting and mind your pleasantness...
 
Even though AMD does use Tcase, AFAIK they have given it enough leeway that it doesnt really matter. 

But there was some bugginess in HTC/STC hardware thermal control/software thermal control. As far as I know, that is pretty rare. Anyway, who is going to try to run fanless and disable thermal protection in BIOS? 

[http://www.amd.com/us-en/assets/content_type/white_papers_and_tech_docs/33610.pdf](http://www.amd.com/us-en/assets/content_type/white_papers_and_tech_docs/33610.pdf)

But here is an idea.- 

> **Caps18 said:**
> The CPU is an AMD Athlon 64 X2 (3.6 Ghz), and it will just be running Mythbuntu (HD video will be the hardest thing it will run).

Since your only using it for mythbuntu, and HD is as hard a task as it has to do...underclock/undervoltage the hell out of it. If you have a nVidia card, it does the decoding, so you should be able to go down to 1Ghz (or possibly even less) and get totally stutter free HD playback. Lowering the voltage and clock speed will really reduce the max heat output.

---

