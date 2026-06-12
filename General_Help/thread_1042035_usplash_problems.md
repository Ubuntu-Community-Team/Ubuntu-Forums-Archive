---
title: "usplash problems"
date: 2009-01-17
forum: General Help
---

### Post by FNHA on 2009-01-17
Hi, I'm having problems with using usplash other than the default ubuntu one. Whenever I try to change the usplash to something else with Startup-Manager, it just ends up showing the text version. Are there any packages I need to install before the usplashes will show up properly?

---

### Post by kangaroo738 on 2009-02-02
The start up manager is not reliable. Your better off manually setting the usplah. It took me too weeks of trying repetitively but i got it. I recommend using remastersys which can be added to your repository with deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/. This will allow you to make a disk back up of your system before you try to change the usplash. It was the only reason my I succeed. Also when doing it manually the instructions you may find on one site may not be the full deal. Browse other instructions for reference. I had to use a readme from another theme to figure out how to install mine, then another readme to change the resolution.

---

### Post by Andy06 on 2009-02-02
I wouldn't advice manual config if you're not adept with linux.

The start up manager must have the correct resolution set for the corresponding usplash theme.

So lets say the fingerprint theme is installed for example, it will spit out text during boot splash if the default 640x480 is left as the resolution. It needs to be set to 1024x768. Unfortunately this is different for every theme and you will have to experiment. Some I still cannot get to work. Perhaps badly written or configured theme.

You can also try replacing usplash with splashy which has some themes in the repositories and handles more theme formats. Any theme you get from the repository is much more likely to work without bugs then the ones off gnome-look which are really hit and miss.

Type in splashy and splashy themes in synaptic and it should throw up the relevant packages.

---

