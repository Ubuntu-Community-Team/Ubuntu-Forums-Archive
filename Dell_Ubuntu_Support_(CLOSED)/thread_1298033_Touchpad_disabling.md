---
title: "Touchpad disabling"
date: 2009-10-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sbooder on 2009-10-22
Hi All,
        I now have Ubuntu 9.10 beta on my Dell Inspiron laptop.  Is there a way of permanently disabling the touchpad when a usb mouse is attached.

Thanks for any help.

---

### Post by moe_syzlak on 2009-10-23
If your laptop supports it, there is a keyboard combination that you can press that disables touchpad mouse. Or you can disable it in Xorg, but that would be unnecessary as it's not able to be changed rapidly that way (on the fly aka when you want it to switch).

How about you just leave it the way it is?

---

### Post by jaugen on 2009-10-24
sudo apt-get install gsynaptics

---

### Post by sbooder on 2009-10-24
> **jaugen said:**
> sudo apt-get install gsynaptics

Thank you, that worked a treat.

---

### Post by aasmith on 2009-11-04
Is there some reason that Karmic doesn't let us totally disable the touchpad anymore?  It seems a poor design decision, to actually *take away* functionality. It seems like it could still be a button, right next to "disable while typing."

---

### Post by sbooder on 2009-11-05
I agree, it is annoying.  I installed gsynaptics and although I thought that it worked, it keeps resetting its self at any given moment to enabled.

 I never use my touchpad, and I am fed up with accidentally moving the curser out of where I am typing into another open program and typing in there.

---

### Post by RayArdia on 2009-11-12
Exactly the same problem, touchpad disabled via System-Administration-Touchpad but as soon as I use the keypad the touchpad is re-enabled!
Like lots of others I can't seem to avoid touching it whilst typing which results in all kinds of unwanted actions.

---

### Post by bobcollard on 2009-11-12
> **sbooder said:**
> I agree, it is annoying.  I installed gsynaptics and although I thought that it worked, it keeps resetting its self at any given moment to enabled.

 I never use my touchpad, and I am fed up with accidentally moving the curser out of where I am typing into another open program and typing in there.

Put gsynaptics in your Sytem Settings/Advanced/Autostart as a program.  You will have the choice to use it or not when you startup and mine stays put all day.  You never know, you just might want to take that laptop on the road without a mouse or your mouse could break down.  If you are using Kubuntu don't forget to check the advanced "startup with KDE" in the same place.

---

### Post by tbullock on 2009-11-13
> **RayArdia said:**
> Exactly the same problem, touchpad disabled via System-Administration-Touchpad but as soon as I use the keypad the touchpad is re-enabled!
Like lots of others I can't seem to avoid touching it whilst typing which results in all kinds of unwanted actions.

I have the same issue. When I type the touchpad is re-enabled. My touchpad is broken and if I touch it then I can no longer left click. So I have to restart. There must be a way to turn this thing off for good...

---

### Post by bobcollard on 2009-11-13
> **tbullock said:**
> I have the same issue. When I type the touchpad is re-enabled. My touchpad is broken and if I touch it then I can no longer left click. So I have to restart. There must be a way to turn this thing off for good...

gsynaptics is not what the system setting uses in Ubuntu, it is a little different.  True, it changes when you restart, but it lasts.  There is another touchpad app called touchfreeze, it only works while you are typing.

---

### Post by tbullock on 2009-11-13
> **bobcollard said:**
> gsynaptics is not what the system setting uses in Ubuntu, it is a little different.  True, it changes when you restart, but it lasts.  There is another touchpad app called touchfreeze, it only works while you are typing.

Is my best option taking the thing apart and unpluging the touchpad? There has to be another way that just requires a code in the terminal...

---

### Post by bobcollard on 2009-11-13
> **tbullock said:**
> Is my best option taking the thing apart and unpluging the touchpad? There has to be another way that just requires a code in the terminal...
Have you checked with Dell?  They have a Forum too : [http://en.community.dell.com/forums/](http://en.community.dell.com/forums/)  I'd be careful pulling wires and I am trained in Micro Computer Repairs.

---

### Post by tbullock on 2009-11-14
Ok, I figured out why it was re-enabling.

Once you install gsynaptics and disable the touchpad you have to then go to the system/preferences/mouse and then uncheck the option that says to disable touchpad while typing. With that setting the other way or checked it turns the touchpad back on after typing. Not sure if it will stay through a restart but give me a minute and I will know.

---

### Post by tbullock on 2009-11-14
Ok, it stays off through a restart on my machine. I think I should be good to go. :D

---

### Post by tetris11 on 2009-11-14
Cant you just go the BIOS menu (F2?) and disable the auto-internal touchpad feature?

Usually works like a charm in Windows...

---

### Post by HeadInTheClouds on 2009-11-14
Got any idea how to make this work in Wine? / perhaps is does work in Wine once done? In Jaunty it was fine, but now when I play Wine - CS against my son I last less than two seconds, usually die looking at the roof, my thumbs on the touchpad making my viewpoint hop all over the place, I used to last at least 4 seconds ;-)

---

