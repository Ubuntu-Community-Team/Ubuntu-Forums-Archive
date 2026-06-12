---
title: "Stacking time over date?"
date: 2010-12-21
forum: Desktop Environments
---

### Post by Splat_NJ on 2010-12-21
I searched but I'm only finding about changing the format (12/18/10 vs 18/12/10, etc) so please help me out guys. What do I need to do to stack the time over the date in Ubuntu's tray? Thanks.

---

### Post by PhantmKllr on 2010-12-21
Are you saying that you want the time to come first? You can't do this with the Gnome panel applet. However, the Date/Time applet in 10.10 will be replaced by an Ayatana ([https://launchpad.net/ayatana]("https://launchpad.net/ayatana")) compatible applet in 11.04, which may solve the problem.

---

### Post by Splat_NJ on 2010-12-21
I know I've seen it done, but can't find it anywhere so I may be mistaken. I want the time to appear over the date like this:

 3:30pm
12/21/10

Thanks.

---

### Post by PhantmKllr on 2010-12-21
Right click on the panel, then click "Properties". Then increase the size of the panel until the the clock/date is stacked.

---

### Post by Splat_NJ on 2010-12-21
> **PhantmKllr said:**
> Right click on the panel, then click "Properties". Then increase the size of the panel until the the clock/date is stacked.

That's not stacking them for me because this gives the time and date actually more space.

---

### Post by Splat_NJ on 2010-12-21
Isn't it funny how things happen?  After searching all day for my answer I finally just now found it.  Note: depending what size font you use you may have to increase the size of your panel. I had to change mine to 35 to fit this new time/date format.

Here is now what I use for my clock:

<sup><span rise="3000" font_desc="Times New Roman 12"     color="green" weight="normal">%a     %D</span></sup>%n<sub><span font_desc="Times New Roman 13" color="green"     weight="bold">%I:%M%p</span></sub>

---

### Post by PhantmKllr on 2010-12-21
Alright then. Glad you found the answer to your problem.

---

