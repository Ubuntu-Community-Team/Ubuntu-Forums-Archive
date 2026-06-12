---
title: "CPU Frequency"
date: 2008-12-03
forum: General Help
---

### Post by Nathan Sweeney on 2008-12-03
Hello all,

Recently I installed kubuntu-desktop on my Ubuntu install.  I wasn't big on KDE, but I did like the fact that the battery monitor also showed the CPU frequency (I wasn't even aware that Linux was capable of scaling back the frequency at certain times).

Is there anything similar and "gnome-ish" that I can install to get the same information.  If so, what would be the package name to install it if it is available via apt.

Thanks,

Nathan

---

### Post by mdurham on 2008-12-03
The CPU Frequency Scaling Monitor is an applet that can be added to a panel. Right click on the panel and select "add to panel"
You will probably need to install the Gnome-applets from the repos to make them available.
Cheers, Mike

---

### Post by Nathan Sweeney on 2008-12-03
> **mdurham said:**
> The CPU Frequency Scaling Monitor is an applet that can be added to a panel. Right click on the panel and select "add to panel"
You will probably need to install the Gnome-applets from the repos to make them available.
Cheers, Mike

Yeah, I can't install gnome-applets...it's already installed.  I right clicked on the panel and found the CPU Freq items.  I added 2, one for each core.  I never knew that was there.  Don't I look a fool :oops:

Thanks for the hint...

---

### Post by jespdj on 2008-12-03
> **Nathan Sweeney said:**
> I added 2, one for each core.
What processor do you have? On Intel Core 2 Duo processors, both cores always run at the same speed. They don't switch speeds independently. So you'd only need to add one instance of the frequency applet.

---

### Post by Nathan Sweeney on 2008-12-03
> **jespdj said:**
> What processor do you have? On Intel Core 2 Duo processors, both cores always run at the same speed. They don't switch speeds independently. So you'd only need to add one instance of the frequency applet.

Hmm, I thought that I saw them changing independently maybe they just didn't update at the same time.  I didn't think they could throttle independently, but when I saw that I thought maybe they could.  I just run one then.  Thanks for the tip!

---

