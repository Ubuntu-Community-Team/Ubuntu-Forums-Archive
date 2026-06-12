---
title: "Java trouble"
date: 2006-09-13
forum: Desktop Environments
---

### Post by greyash99 on 2006-09-13
I'm really having trouble installing Java in Ubuntu.  I installed it but it didn't work and I don't know why.  How can I install it without using easyubuntu or automatix?

---

### Post by andypaxo on 2006-09-13
If you could give a little detail on how it didn't work, that would help.

The easiest way would be to use apt:
- First, enable the extra repositories (tick the universe and multiverse boxes in Synaptic (Settings menu, then repositories), I can't rememeber which one of the two Java is in, but it won't hurt to have both)
- 'Reload' in Synaptic
- Then install Java either by using Synaptic, or by running the following on the command line:
sudo apt-get install sun-java5-jre sun-java5-plugin

Hope that helps

---

