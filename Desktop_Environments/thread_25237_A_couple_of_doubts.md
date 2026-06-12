---
title: "A couple of doubts"
date: 2005-04-09
forum: Desktop Environments
---

### Post by thesen on 2005-04-09
Hi!

This is my first time around here and I've got two questions, hope you can help me. 

The first one is about the default theme for Kubuntu. I've been touching the theme manager and now I can't go back to the defaults. In another post I read that you can go back by removing de .kde folder in home, but I've been looking in the folder and I saw that it contains config files for kde applications, is it important? I mean, I've been configuring some apps and I think the config files are there. If i delete/move the folder do I lose the config? In case I do, how can I go back to the default theme?

My second problems comes with firefox. I've tried to install it from the apt repositories but it doesn't work for me. I apt-get it and when I try to execute it, it just do nothing.

Thanks in advance.

TheSen

---

### Post by denzilla on 2005-04-09
Amazingly, installing FF hasn't been an issue for me. I tried apt-get, but it started moaning about missing packages after installation. On the second wipe/reload of Kubuntu, I used Kynaptic to install FF and it did so without issue. Used that method ever since.....

---

### Post by Sleepy_Sentry on 2005-04-09
There are a few things you have to install to be able to install apps. I'm new to Linux and am still looking for answers on how to install the stuff to be able to install apps. I would go to [http://ubuntuforums.org/showthread.php?t=25163](http://ubuntuforums.org/showthread.php?t=25163) and look at my other thread in the same forum for some information. Also, you need to be logged into root.

---

### Post by thesen on 2005-04-09
Update:

I've tried moving .kde folder to see what happens and it just forget my preferences about apps, but the color schemes, translucency, fonts, etc. is still the same.

**Sleepy_Sentry:** I don't have problems installing apps, just installing firefox. Try this link: [Ubuntu Guide](http://ubuntuguide.org/) It's very helpful.

**denzilla:** I've tried both, apt-get and kynaptic. I can install firefox with both, but I cannot run the app. 

Thanks both for your answer.

TheSen

---

### Post by digby on 2005-04-09
Did you try just downloading firefox from their website and using their installer?

---

### Post by thesen on 2005-04-10
Yep, I've tried with the same result. I think the problem was trying to install the web version instead of the repositories one, I couldn't find the uninstaller and searching in the firefox faq it says to just delete the folder so I did that.

When I installed for the first time from the web I could run mozilla but just as root with sudo (the permissions were ok) so I tried to uninstall it. Now it doesn't work even for root. 

I've solved the problem by reinstalling Kubuntu. It was a fresh install so it was no problem. Just had to apt-get and setup again the apps. I finished in about an hour.

Thanks all for your answers.

TheSen

---

