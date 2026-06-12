---
title: "Battery is charged notice malfunctioning"
date: 2010-10-06
forum: Desktop Environments
---

### Post by Crazedpsyc on 2010-10-06
I am running Ubuntu Lucid with just about all the default settings except for one thing that might effect this: I am using AWN for my bottom panel. I am getting the battery is charged notice constantly. It will not go away. just to clarify which notice I am getting exactly there is a screenshot of it attached. any ideas?

---

### Post by whiskeylover on 2010-10-06
Do you have the battery icon on the gnome panel? If so, do they both (gnome battery and AWN battery) show the same remaining battery level percentage?

---

### Post by Crazedpsyc on 2010-10-06
the one in AWN says 100% but I have the gnome one set to only show when the battery is charging or discharging

---

### Post by whiskeylover on 2010-10-06
Okay, you can set it so it shows all the time. Also, I bet the percentage shown on the gnome panel is less than 100. That happens because as the battery ages, its health decreases. As that happens, both applets (on gnome panel and on AWN) interpret the values returned by the battery API differently. AWN might be thinking that the battery is fully charged when in fact its not. Try moving the notification applet to gnome panel.

Worth a try.

---

### Post by Crazedpsyc on 2010-10-06
I looked at it and It too says 100%. and my battery shouldn't be that run-down because I got it just over a month ago

---

### Post by whiskeylover on 2010-10-06
Oh, then I'm out of ideas. Sorry : (

---

### Post by Crazedpsyc on 2010-10-06
that's all right. I hope someone else can figure it out though!

---

### Post by Crazedpsyc on 2010-10-06
Still nothing? Bump bumpadee bump bump... Bump Bump!

---

### Post by Crazedpsyc on 2010-10-06
> **Crazedpsyc said:**
> Still nothing? Bump bumpadee bump bump... Bump Bump!
I can't believe there is still nothing!! BUMP!
It did finally go away but I am pretty sure it will be back next time I log in

---

### Post by Crazedpsyc on 2010-10-12
Ok, I fixed it. I set the preferences in the awn battery monitor to not notify when battery level reaches 100 percent. I though it would just announce when it first became fully charged, but I guess not.

---

