---
title: "A Tiny Problem with Xgl and Compiz for Dapper"
date: 2006-09-13
forum: Desktop Environments
---

### Post by EmyrB on 2006-09-13
Hi, I wonder if someone could shed some light on to some problems I am having with this excellent add on for Linux. I followed the instructions to the letter as given by this [http://www.tectonic.co.za/view.php?src=rss&id=1153](http://www.tectonic.co.za/view.php?src=rss&id=1153) and everything went according to plan.

Now I have 2 questions, the first is concerning how do I get to have Xgl and compiz to load automatically after logging in without the need to run compiz-manager form a terminal?

The second question is to do with an error I get in the terminal window which reads as follows: -compiz: water: GL_ARB_fragment_program is missing. I have tried apt-get install for it but no joy. I want to get this working as I sure would like to have the water effect on my desktop as I move my mouse (just to show off to my Windoze friends what Linux can do on existing hardware, that's all, honest ;))

Any help is greatfully recieved,

Cheers

EmyrB

---

### Post by ayoli on 2006-09-13
> **EmyrB said:**
> 
Now I have 2 questions, the first is concerning how do I get to have Xgl and compiz to load automatically after logging in without the need to run compiz-manager form a terminal?

in gnome main menu go to System > Preferences > Sessions, then pick "Startup programs" tab and add compiz-manager here.

dunno for your second question, actually water effect won't work for me (with aiglx)

---

### Post by EmyrB on 2006-09-26
Thanks Ayoli followed your instructions and it works. Still no joy with the water effects though :(

---

### Post by dentaku65 on 2006-09-26
If you have an Itel i810 or derivates water plugin cannot be work due to the limit of this device.

---

