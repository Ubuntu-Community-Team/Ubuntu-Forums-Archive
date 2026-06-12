---
title: "help in learning matlab"
date: 2012-11-13
forum: Education &amp; Science
---

### Post by nice man on 2012-11-13
hi i have a project to do about to control in light 

It is well known or it is a tradition that when the instructors enter a classroom, the first thing that they do is to turn on the classroom lights. Unfortunately, when they finish their lecture, most of the lectures do not turn-off the lights. Therefore, the light keeps shining all the day from 8:00 am to 4:00 pm. Thus, a considerate amount of energy is wasted during the daily breaks that separate lectures in the same room from each other. To save such energy, it might a wise idea to turn off the classroom lights during the previous breaks. Turning-off of such lights when not needed should be automated and not left to the mercy of the instructors.
To get an idea of how much energy from the lights can be saved. Let&#8217;s consider the following illustration:
Assume that the day of lecture in a one classroom is Monday or Wednesday. We know that the timings of lectures during Monday or Wednesday are as follows:
8:00 am to 9:15am, 9:30am to 11:00am, 1:00 pm to 1:15 pm, and 1:30 pm to 4:00 pm.
If there is no concern about energy consumption by the lights, the light will be used continuously for 8:00 hours (from 8:00 am to 4:00 pm).
However, if there is a concern about energy savings, the lights should be off during the breaks: 9:15 to 9:30 Am, then 10:45 am to 1:00 pm, then 2:15 pm to 2:30 pm, then 3:45 pm to 4:00 pm. Adding all previous breaks results in 3 hours saving of energy used by the lighting system in the classroom. This means, we can save on Monday and Wednesday 3/8=0.375 (i.e 37.5%) of energy used by the lighting system.
The present project will propose an automatic controller using Matlab as a control platform to:
- will turn on the light at 8:00 am and turn it off at 9:15 am, then
- will turn on the light at 9:30 am and turn it off at 10:45 am, then
- will turn on the light at 1:00 pm and turn it off at 2:15 pm, then
- will turn on the light at 2:30 am and turn it off at 3:45 pm, then
- then keep the light off from 3:45 pm to 8:00 am of the next day

anyone can help me to do this programming ..

---

### Post by ssam on 2012-11-14
does this have to be done with MATLAB? seems like an odd choice, unless you have some sort of MATLAB interface to the lighting system.

you might want to see if you can do it with an [arduino]("http://www.arduino.cc/"). it has more than enough computer power to count time, and switch lights on and off (though you may need an external clock module for more accurate time [https://www.sparkfun.com/products/99](https://www.sparkfun.com/products/99) ). It also has the benefit of being very low power, compared to leaving a computer on all the time control the lights.

---

### Post by nice man on 2012-11-14
> **ssam said:**
> does this have to be done with MATLAB? seems like an odd choice, unless you have some sort of MATLAB interface to the lighting system.

you might want to see if you can do it with an [arduino]("http://www.arduino.cc/"). it has more than enough computer power to count time, and switch lights on and off (though you may need an external clock module for more accurate time [https://www.sparkfun.com/products/99](https://www.sparkfun.com/products/99) ). It also has the benefit of being very low power, compared to leaving a computer on all the time control the lights.

yes it's must be done by MATLAB because this programming working 
in my circuit ..

---

