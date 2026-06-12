---
title: "Math Question"
date: 2009-10-02
forum: Education &amp; Science
---

### Post by fallenshadow on 2009-10-02
I am posting in this section since I will most likely get an answer here. (well I hope so :)  )

I am developing a little program to calculate the force for a pellet gun but I am a little stuck with the maths of it all.

_Here is what I know:_

328FPS (feet per second) is equal to 100M/S (metres per second).

A 0.2 gram pellet shot at 328FPS (or 100M/S) results in an output of 1 Joule of energy.

I am stuck on how weight affects the formula... I know that a heavier pellet will be slower... obviously... but I don't know how to mathematically calculate how much slower the pellet would be. Any ideas?

---

### Post by PandaGoat on 2009-10-02
Before I answer, I have a question.  Do you mean that the more massive the pellet, the slower it will be shot out of the gun if the same amount of energy is used?

If you increase the mass of a pellet but keep the speed at which the pellet is fired, then the energy increases, but the pellet does not move any slower; so I suspect you mean for the amount of energy used to fire the pellet to be the same, but I want to be sure.

---

### Post by bostonaholic on 2009-10-02
Considering
```
F = ma
(F)orce
(m)***
(a)cceleration
```

As you increase the mass of the object (and maintain it's a acceleration) the Force increases proportionally.

Theory:
```
1 Joule is the amount of energy to move a 1 Newton object, 1 meter through space.
1J = 1N * 1m

1N = 1 kg*m/s^2

1000g = 1kg
```

EDIT:  I'll let you do the rest. ;)

---

### Post by unutbu on 2009-10-02
```
sudo apt-get install units
% units
2445 units, 71 prefixes, 33 nonlinear units

You have: 1 kg * m*m/s/s
You want: joule
	* 1
	/ 1
You have: 0.2 g * (100*m/s)^2
You want: joule
	* 2
	/ 0.5

```

---

### Post by nema.arpit on 2009-10-02
A simple 
```
 E=0.5*m*v^2 
E=Energy (kinetic in this case)
m=mass
v=velocity


```
should suffice.

And shouldn't it be Physics question?

---

### Post by bostonaholic on 2009-10-02
> **bostonaholic said:**
> Considering
```
F = ma
(F)orce
**(m)*****
(a)cceleration
```

As you increase the mass of the object (and maintain it's a acceleration) the Force increases proportionally.

Theory:
```
1 Joule is the amount of energy to move a 1 Newton object, 1 meter through space.
1J = 1N * 1m

1N = 1 kg*m/s^2

1000g = 1kg
```

EDIT:  I'll let you do the rest. ;)

Haha, I just noticed that it starred out *******. in my (m)***.

---

### Post by Chronon on 2009-10-02
> **bostonaholic said:**
> Haha, I just noticed that it starred out *******. in my (m)***.

Did you also notice that you're claiming that 1 g=1000 kg?

---

### Post by ad_267 on 2009-10-02
> **nema.arpit said:**
> 
```
 E=0.5*m*v^2 
E=Energy (kinetic in this case)
m=mass
v=velocity


```


+1, I think that's what you're after. Assuming the gun will transfer the same amount of energy to any weight pellet, you can calculate the velocity with different weights.

---

### Post by bostonaholic on 2009-10-02
> **Chronon said:**
> Did you also notice that you're claiming that 1 g=1000 kg?

oops, thanks.  Fixed.

---

### Post by fallenshadow on 2009-10-03
> A simple
Code:

E=0.5*m*v^2 
E=Energy (kinetic in this case)
m=mass
v=velocity

should suffice.

And shouldn't it be Physics question? 

Yes it is a physics question I suppose. 
So I understand that:

Energy = Joules
Mass = Weight of pellet
Velocity = FPS (feet per second) or M/S (metres per second)

So where does the 0.5 come from? or are you just saying that the Mass needs to be halved?

---

### Post by nema.arpit on 2009-10-03
It's the kinetic energy **E** of a body moving with velocity **v** and having mass **m**.**E** is in joules only if **m** is in kg and **v** in m/s.
The 0.5 factor comes in from the integral which lets you arrive at the expression.Check the derivation here: [http://en.wikipedia.org/wiki/Kinetic_energy]("http://en.wikipedia.org/wiki/Kinetic_energy")

---

### Post by issih on 2009-10-03
Note that basically all science (regardless of your location) is done in SI units these days..metres, kg, seconds etc. imperial units like foot, inches, pounds and ounces are never used.

It is important to use these units as the units we use contain implicit constants reflecting the ratio of one thing to another e.g. F=ma is only that because with mass measured in kg and accel in m/s^2 the constant of proportionality is 1. If you use other units then F will still be proporional to ma, but there will be a different constant involved other than 1.

---

### Post by fallenshadow on 2009-10-03
> **nema.arpit said:**
> It's the kinetic energy **E** of a body moving with velocity **v** and having mass **m**.**E** is in joules only if **m** is in kg and **v** in m/s.
The 0.5 factor comes in from the integral which lets you arrive at the expression.Check the derivation here: [http://en.wikipedia.org/wiki/Kinetic_energy]("http://en.wikipedia.org/wiki/Kinetic_energy")

Understood.... if I have any issues I will return to this thread and post a new reply. Thanks all! :)

---

