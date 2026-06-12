---
title: "Can't get gDesklets to start at startup"
date: 2007-04-27
forum: Desktop Effects &amp; Customization
---

### Post by Catsworth on 2007-04-27
Hey Guys,

I've tried adding gDesklets to my startup session but the change doesn't seem to stick.

I've tried adding "gdesklets", "gdesklets start", and tried using the option to browse, but all to no effect.

Any ideas?

Thanks.

---

### Post by orb9220 on 2007-04-27
> I've tried adding gDesklets to my startup session

Did you install them from synaptic and the gdesklets-data?
So it would also install the dependecies for python and other libs.

---

### Post by Catsworth on 2007-04-27
gDesklets is installed and working fine, I can run it from a terminal but it just won't run when Ubuntu starts.

---

### Post by Happy_Man on 2007-04-27
You need to run "gdesklets-daemon" at startup.

---

### Post by orb9220 on 2007-04-27
Wierd because I just use the word  gdesklets in startup on edgy and feisty.

---

### Post by Catsworth on 2007-04-30
Ok, this is symptomatic of a larger problem.

I can't get *anything* to load at startup.

The problem is that nothing saves within the Sessions > Startup tab.

I add something new in there, close the dialog window, and then open it again, and the new items I added have gone.  Anybody any ideas what's causing this?

---

### Post by mlhudson on 2007-04-30
I have this same issue. After trying: "gdesklets", "gdesklets startup", and "gdesklet-daemon" as a New Item in the session manager, none of them stay there. They all disappear when I close out the session manager. Consequently, no gdesklets @ startup. A solution would be very handy!

---

### Post by Catsworth on 2007-05-01
The solution to this is in the second post of this thread:

[http://ubuntuforums.org/showthread.php?t=359686&highlight=startup+chown+permissions](http://ubuntuforums.org/showthread.php?t=359686&highlight=startup+chown+permissions)

---

### Post by mlhudson on 2007-05-01
Catsworth - Thanks a million! This seems to have fixed the issue for me.

---

