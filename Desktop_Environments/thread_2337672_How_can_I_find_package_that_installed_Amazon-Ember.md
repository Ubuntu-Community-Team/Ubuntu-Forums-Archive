---
title: "How can I find package that installed Amazon-Ember font?"
date: 2016-09-20
forum: Desktop Environments
---

### Post by greg2lapa on 2016-09-20
Hey guys.

I installed the new Ubuntu 16.04 and one day while using LO Writer, I noticed that I have the Amazon-Ember font available for use. This is weird because I have a pretty vanilla setup. I have run dpkg -l | grep looking for amazon, ember, amazon-ember etc but never get any hits. I found the file Amazon-Ember-Regular.ttf in my /usr/share/fonts folder. But when I run ```
dpkg -S /usr/share/fonts/Amazon-Ember-Regular.ttf
``` it says "dpkg-query: no path found matching pattern /usr/share/fonts/Amazon-Ember-Regular.ttf"

How can I find out how Amazon-Ember-Regular.ttf was installed? What package installed it?

---

