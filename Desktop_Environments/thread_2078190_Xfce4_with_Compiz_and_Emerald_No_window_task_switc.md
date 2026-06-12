---
title: "Xfce4 with Compiz and Emerald: No window task switcher function"
date: 2012-10-30
forum: Desktop Environments
---

### Post by Tobba on 2012-10-30
I have Ubuntu Studio 12.10 with Xfce4, and I installed Compiz and Emerald on it. All is working just fine except i'm lacking any 'window task switching'-function. I already checked the 'Compiz Settings Manager', but there's no any of such opinion to choose.

So basically my problem is, to my knowledge: My (newest) compiz is lacking alt-tab opinion. Why's that?'


BTW: Hello to everybody!

---

### Post by LewisTM on 2012-10-30
There are a number of switcher plugins in the Window Management section of CCSM. You should verify that you have all compiz plugins installed in Synaptic.

Cheers!

---

### Post by Tobba on 2012-10-30
Ya, I missed the compiz-plugins package. Cheers to you!

---

### Post by kutalion on 2012-10-30
How did you make compiz run with XFCE? I recieve no Windows Decoration even if I mark the appropriate plugin for this I also receive no WM functionality no matter if I load all plugins. It just won't budge.
As far as I remember I've had no problems with previous versions of Ubuntu (I am using Ubuntu Studio as well)

So please a hint or two would really be helpful. I'd appreciate.

EDIT: Lamest mistake EVER. The folder ~/.config/compiz-1 which holds user configurations of compiz was owned by root without even permission to read. I've ran sudo chown -R <user>:<group> <homedir> to fix this and any other issue that I could eventually face if I accidentally messed with the ownership of other dirs as well.

---

