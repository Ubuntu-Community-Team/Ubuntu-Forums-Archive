---
title: "what's up with the resolution?"
date: 2007-04-09
forum: Desktop Effects &amp; Customization
---

### Post by north zulch computer geek on 2007-04-09
alright, im not too new to linux, but im having this irritating little problem.

i need a higher resolution for some work i am doing!

the drop-down menu has 3 options:

1024x768
800x600
640x480

i need 1600x1200

i know my video card supports extremely high resolution, because i also run MAC OSX 10.3.9 on this computer, and i run it at 1600x1200.

is it even possible to get it up higher? and if so, what do i do?

yes, i know this is probably a noob question.

PS, i have a ton of experience using OSX and windows XP

thanks

---

### Post by Compyx on 2007-04-09
Run ```
sudo dpkg-reconfigure xserver-xorg
```
paying special attention to the questions about you monitor. Sometimes the auto-detection of your monitor's capabilities doesn't work quite as well as it should. When asked about the horizontal/vertical refresh rates, enter them yourself (select 'Advanced' or something) from the monitor's manual/specsheet.

This should provide you with a lot more resolution options. Be careful though, selecting ranges larger than your monitor can handle might damage it. (Although my monitor simple says' frequency out of range' when I had entered some wrong values)

---

### Post by north zulch computer geek on 2007-04-09
OK, but what do i put for bus identifier?

---

### Post by rocknrolf77 on 2007-04-09
Default :)

---

### Post by rocknrolf77 on 2007-04-09
Default :) Remember to restart x with ctrl - alt - bkspace.

Edit : Pushed stop in the browser to add some more. But it was posted anyhow.

---

### Post by north zulch computer geek on 2007-04-09
thanks, but, this is just confusing me. i have never worked with xorg.

is there any detailed instruction guide for this?

or can someone who has some time on their hands email me and tell me step-step?

it would be very apprieciated.

[email]thelinuxguy@yahoo.com[/email]

---

### Post by reclusivemonkey on 2007-04-10
Please post

What monitor you have
What graphics card you have
What version of Ubuntu you are using

and attach your xorg.conf

Detailed instructions on xorg.conf, like so many other things, can simply be found by searching google.

---

