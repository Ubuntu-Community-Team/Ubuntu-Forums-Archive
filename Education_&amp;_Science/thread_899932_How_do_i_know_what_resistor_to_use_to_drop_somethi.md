---
title: "How do i know what resistor to use to drop something fomr 9v to 5v"
date: 2008-08-24
forum: Education &amp; Science
---

### Post by Tanjer1588 on 2008-08-24
i am trying to find out how to calculate the ammount of voltage a resistor will drop something, if i know the volts and Ohms of something i can find out its current, i think XD, but i dont know how to use the resistors to drop the voltage of something. Any help will work

thank you.

---

### Post by gunksta on 2008-08-25
This is a little tricky, since I don't have a clue what you are doing!

But what the hell. I'm going to assume that you are dropping a resistor into a simple circuit. If it's a complicated circuit, go do some research before doing anything but this will get you started.

```
Amperage = Volts/Resistance
```

Amperage is measure in amps, voltage is measured in volts and resistance is measured in ohms.

The rest is math (and making sure you've got the right color-coding on the resistor....that part is darned important too!).

Enjoy

---

### Post by hubie on 2008-08-25
I agree that you do need to provide a bit more input.  Start with exactly what it is that you do know.  I presume you have something that runs on 5 volts and you want to power it with 9 volts (like a battery), *i.e.*, you want to come up with a 5 volt supply?

If your current requirements are not too great, you can just use a simple 7805 regulator chip as described [here]("http://www.tkk.fi/Misc/Electronics/circuits/psu_5v.html").

If it is more complicated then that (or more complicated than using a simple wall wort) and you want/need to go with resistors, then you need to provide some more information such as load resistance, current, or power.

The basic idea of what you want to do, which is to set up a voltage divider, is shown in [this link]("http://hyperphysics.phy-astr.gsu.edu/hbase/electric/voldiv.html").

---

### Post by Proton Soup on 2008-08-26
yeah, what hubie said.   it really depends on what you're trying to do.  if it's a reference voltage to something that requires little input current, a voltage divider may be best.  if that reference needs to be exacting, then you want to buy a voltage reference IC.  

if the load(current draw) is static, you only need to know how much current it will draw at 5V and design the input resistor accordingly.

if the load is variable, then you'll need a voltage regulator like the 7805s.

even a simple question like this becomes a design problem and the answer is "it depends".

---

