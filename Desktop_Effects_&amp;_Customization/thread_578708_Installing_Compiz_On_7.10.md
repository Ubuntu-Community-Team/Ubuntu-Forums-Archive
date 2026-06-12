---
title: "Installing Compiz On 7.10"
date: 2007-10-17
forum: Desktop Effects &amp; Customization
---

### Post by Mithrandir06 on 2007-10-17
Info: Running laptop with Radeon Xpress 200m

I installed Compiz via
[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)
and am having major problems getting compiz to work.  I ran 
compiz --replace
and got it to run but i can't open the settings manger from system preferences.  also after compiz is running my wobbly windows no longer works.
my normal desktop effects wobbly windows works fine.
Please help.

---

### Post by freetonik on 2007-10-17
On 7.10? But Gutsy already has Compiz!

So, if you want to install Compiz manually, you have to completely uninstall old compiz. 

sudo apt-get remove compiz-core desktop-effects
and then - delete /home/USERNAME/.gconf/apps/

---

