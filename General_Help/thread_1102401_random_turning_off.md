---
title: "random turning off"
date: 2009-03-21
forum: General Help
---

### Post by djbenny on 2009-03-21
laptop just randomly turns off i have copied the last system log entries before the turn off.

> Mar 21 17:24:31 blaptop kernel: [ 2220.646816] CE: hpet increasing min_delta_ns to 22500 nsec
Mar 21 17:47:59 ben-laptop -- MARK --
Mar 21 18:07:59 ben-laptop -- MARK --


has been doing it randomly for the past 2 weeks...

---

### Post by detroit/zero on 2009-03-21
> **djbenny said:**
> laptop just randomly turns off i have copied the last system log entries before the turn off.




has been doing it randomly for the past 2 weeks...

Does it go through a shutdown procedure (i.e., with the splash screen and a progress bar and/or text saying that services are being shut down) or does it just poweroff **right now**? 

When's the last time you cleaned it? Many times, seemingly random shut-downs can be attributed to high temps. Either way,  taking it apart and cleaning dust and filth from the fan(s), heat sink(s), and other areas will greatly improve your computers cooling and help avoid these (and many other much worse) problems.

If it's a laptop, what condition is the battery in? Does it charge fully and properly? Does it hold a charge? What kind of run time do you get off a full charge? Does the AC adaptor work properly? Are the plugs (on the adaptor) and sockets (in the wall and in the computer) clean and in good repair? Do they sometimes jiggle loose, causing you to run on battery power when you think you're on AC?

Sorry to ask so many questions, but you didn't really provide *any* relevant information in your post. These are the kinds of things we will all need to know if we're going to help you solve this problem.

---

### Post by djbenny on 2009-03-21
no, just turns off.

was cleaed about 4 months ago its a laptop and i get a technician too look it occasionally through support but they wont look at with ubuntu as they want windows on.

the battery and power adapter are fine.

looking at the system monitor temps the temp is around 70 celcius through the nvidia software

---

### Post by detroit/zero on 2009-03-21
> **djbenny said:**
> no, just turns off.

was cleaed about 4 months ago its a laptop and i get a technician too look it occasionally through support but they wont look at with ubuntu as they want windows on.

the battery and power adapter are fine.

looking at the system monitor temps the temp is around 70 celcius through the nvidia software
I take my Toshiba apart once about every six weeks or two months at the most, and I'm usually quite shocked at the amount of filth that collects in that time.

You say 'nvidia software'.. Is that a graphics card temp sensor? Do you have other sensors on your motherboard? Have you installed lm-sensors to monitor cpu temp? 70°C is kind of warm, but not really critical. At the same time, though, 58°C to 65°C is average running CPU temp for my Toshiba laptop. If I remember right, shutdown occurs at 100°C.

If you don't have lm-sensors installed to monitor cpu temps, you might want to grab that. You can either pipe the output through conky, or there's applets for gnome-panel and AWN, whichever you use. Having a constant watch on your CPU temps will be a good indicator of how dirty the inside of your laptop is.

Or, I could be barking up the wrong tree and it's something software related, and you might want to wait and see what other kinds of replies you get. The fact you say it does a hard shutdown leads me to believe that it's a thermal problem, though...

---

### Post by djbenny on 2009-03-21
i have a acpi termal temp sensor currently reporting 52-57 celcius

---

### Post by djbenny on 2009-03-23
last time i saw it was at 56 and turned itself off.

---

### Post by djbenny on 2009-03-29
the screen does a lot of flickering too...

i dont know what this could be. but its frustrating...

---

### Post by djbenny on 2009-03-31
bump, need a solution urgently

---

### Post by paradigm2 on 2009-03-31
> **djbenny said:**
> bump, need a solution urgently

Almost certainly temp related if that 70 degrees refers to the hard drive temp.  70 degrees Celsius is sky high and dangerous IF you are referring to the hard drive temp sensor.  If it is the cpu sensor then that is just a little bit high but okay.

I highly suspect a temperature issue as well due to the other symptoms of the screen flickering and general quirkiness.  I have the same issue with an Acer Laptop of mine.  Whenever the cpu temp gets above 75 degrees C or the HDD temp goes above 55 degrees C weird things happen on the laptop such as screen issues or sudden shutdowns.

---

### Post by djbenny on 2009-04-03
> **paradigm2 said:**
> Almost certainly temp related if that 70 degrees refers to the hard drive temp.  70 degrees Celsius is sky high and dangerous IF you are referring to the hard drive temp sensor.  If it is the cpu sensor then that is just a little bit high but okay.

I highly suspect a temperature issue as well due to the other symptoms of the screen flickering and general quirkiness.  I have the same issue with an Acer Laptop of mine.  Whenever the cpu temp gets above 75 degrees C or the HDD temp goes above 55 degrees C weird things happen on the laptop such as screen issues or sudden shutdowns.

the 70C was for the graphics card temp sensor... i thinking i should contact toshiba to come and have a look but im noy sure if because i have got ubuntu on it will void the warranty?

its usually around about 60celcius on the ACPI temp sensor as a screenlet reports. screen flickers sometimes too
but it does long peroids with no fan action. which i find odd.

---

### Post by David H T@E on 2009-05-09
Hi
I am not able tell you what causes the problem but thought you may like to know, this may not be temperature related as I have the same problem but if I boot in Windows, I experience no problems at all.

---

