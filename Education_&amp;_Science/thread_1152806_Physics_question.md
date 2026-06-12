---
title: "Physics question"
date: 2009-05-08
forum: Education &amp; Science
---

### Post by blazemore on 2009-05-08
Hi, please only answer if you know, not an ill-informed guess, thanks:

> You are required to design a laboratory experiment to investigate how the acceleration of a wheel and axle rolling down a slope varies with the diameter of the wheel

The wheel is rolling down rails, so only the axle is touching the rails. The axle stays the same for every diameter of the wheel.


Question: What effect would the diameter of the wheel have on the acceleration? Acceleration due to gravity remains constant, so my first guess would be that it is less, due to more air resistance. What does UF think?

---

### Post by InfernalNeutrino on 2009-05-08
For some reason I'm feeling a bit socratic, so maybe I'll just give some hints instead of the straight up answer.

Think about what forces you have on the wheel and their direction. Obviously gravity will be the force responsible for the motion down the track, but you aren't in free fall anymore if you're on a track.

Then think about the equations of motion and what kinds of energy the rolling wheel is picking up. It's moving, but also rotating... and rotational energy depends on the rotation rate and the "moment of inertia"...

So really the question might be rephrased: what happens to the moment of inertia of a wheel as its diameter changes? Answer that, and you've got it. Cheers!

---

### Post by blazemore on 2009-05-08
Okay, my gut instinct was that the larger wheel would accelerate more slowly.
Am I right in saying that any changes in friction and air resistance are negligible, when compared to the changes in the moment of inertia?
Basically, the larger wheel will accelerate more slowly than the smaller wheel, because the amount of torque on the axle has to turn a larger mass?

---

### Post by InfernalNeutrino on 2009-05-08
Close. The mass probably won't actually affect it so much since it will appear on both sides of T = Ia and therefore cancel. The real trick is the moment of inertia's dependence on the radius of the wheel. See some examples [here]("http://hyperphysics.phy-astr.gsu.edu/HBASE/mi.html"). Basic idea is that when you rearrange for the angular acceleration you will find an inverse relationship with the radius of the wheel, which explains why it accelerates slower with the larger wheel. Cheers!

---

### Post by PandaGoat on 2009-05-09
_*[I MISREAD THE QUESTION.  THIS IS WRONG.  SEE MY OTHER POST FOR MY FIXED SOLUTION.]*_

The errors from neglecting friction, rolling with slipping, and the thickness of the wheel are the least of your worries when you are being misinformed.  So let's assume friction is negligible, the wheel rolls without slipping, and the thickness of wheel is negligible.

I will stay with being Socratic, but I can go through the derivations if you ask.  

You will find that the linear acceleration of each wheel is independent of the radius.  That is *they have the same linear acceleration*. However, if you mean to compare their angular acceleration, then they would be different.  There are various ways to come to this conclusion; I did it using the conservation of energy and the aforementioned assumptions.

---

### Post by InfernalNeutrino on 2009-05-09
It would seem we have a dispute, which I believe to be caused by different interpretations of the question. In the interest of clarity, I attached the method by which I came to my conclusions. You'll note that if we eliminated the whole axle/wheel combo and simply rolled the wheel down the ramp then Panda would in fact be correct. So, it's just a matter of which interpretation you were going for. Cheers!

---

### Post by PandaGoat on 2009-05-09
Oh, hmm, I think I misinterpreted/misread the question.  I did not notice that it is not really the wheel rolling down a slope but the axle rolling down a slope.  I must not have read the sentence following the quote.  This changes the conditions for slipping.  

I was nearly finished with typing up a response with my solution when I discovered my misconception, so I will post it anyway with the fix; it is a different method than what you did so hopefully it will contribute something.  

Anyway, the linear acceleration does turn out to be depend on the radius of the wheel.  Sorry for any confusion I may have caused.

[Wheel.pdf]("http://snoopy.tuxfamily.org/files/wheel.pdf")

---

### Post by blazemore on 2009-05-10
The level at which this is aimed is AS level, which is a British qualification sat as the first year of an A level course (In the school year you turn 17).

---

### Post by issih on 2009-05-10
Been a while since I did many mechanics problems but I'm pretty sure InfernalNeutrino's solution is wrong.

The analysis presented analyses the instant rotational forces at the point of contact of the axle with the track, then converts the acceleration about that point to a linear acceleration using the no slip assumption that alpha = a/r where alpha is rotational and a is linear acceleration.

This last bit is the issue, you translate the point of rotation being considered from the point of contact (for the force analysis) to the actual axis of rotation (for the no slip assumption). This is not valid. The angular acceleration about the axis does not necessarily equal the instantaneous angular acceleration about the point of contact.

A correct analysis presents the linear acceleration including an unknown force F from friction.

F is then quantified by assuming (under no slip) that the torque associated with it is enough to cause the angular acceleration to match the linear one.

This results in an overall equation for the linear acceleration something like:

acceleration = g*sin(theta)* {Mt/(Mt + [It/R^2])}

where Mt is the total mass, It the total moment of inertia and R the radius of curvature (i.e. the radius relating angular and linear motion)

could be wrong, but thats what I think

Oh and the question doesn't want any of this...it wants you to design an experiment to investigate what happens. i.e. a set of protocols to measure the acceleration. So you need a slope and one of those silly ticker tape things. or a slope and the time it takes to pass several points down the slope. its not about solving the equations, its about how would you get the experimental data?

---

### Post by blazemore on 2009-05-10
I've worked out a method for getting the experimental data, don't worry.

I just need a simple hypothesis, and a straightforward explanation.

---

### Post by issih on 2009-05-10
Well if you just want a way of thinking about it, you can say that the potential energy the object has at the top of the ramp is converted into kinetic energy + rotational energy at the bottom.

so 1/2 mv^2 + 1/2 Iw^2

where I is moment of inertia and w is angular velocity.

with no slip v and w are tied as v=wr with r the radius of the axle.

so total energy at the bottom is 1/2 v^2 (m + I/[r^2])

the energy gained falling from the same height is just the potential energy, so as I increases with the wheel size, the final velocity, must drop.

Same sort of logic applies to the acceleration. The frictional force needed to maintain the rotation at the no slip condition increases as I increases and therefore in the linear force equation the total force acting down the slope is reduced, and the acceleration drops in proportion.

Hope that helps

---

### Post by blazemore on 2009-05-10
Right so because the starting velocity is 0, and each wheel is travelling the same distance, the fact that the velocity is LESS at the end must mean the acceleration has decreased.

Brilliant, thank you all!

---

### Post by PandaGoat on 2009-05-10
Blazemore has the right conclusion, but I want to clear up something.

There is no frictional force involved for the rolling without slipping condition.  There could be, but we neglect it in our theoretical calculations or we actually find the coefficients of friction and then use them. Doing the latter is unlikely.  When we measure it through experiment, we include the propagated error (from friction) in the measured value.

Did you see, in my last post, the attached pdf with my solution?  You seemed to only comment that InfernalNeutrino's solution was wrong.  I'm just curious since the link is not noticeable, and I'm wondering what you thought about my solution if you think InfernalNeutrino's solution is wrong.

---

### Post by ugm6hr on 2009-05-10
This appears to fit into the "homework help" category.

Closed.

---

