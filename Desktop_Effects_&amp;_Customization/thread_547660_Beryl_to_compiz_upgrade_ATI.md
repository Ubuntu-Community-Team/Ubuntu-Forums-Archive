---
title: "Beryl to compiz upgrade ATI"
date: 2007-09-10
forum: Desktop Effects &amp; Customization
---

### Post by absolut24 on 2007-09-10
If you have installed beryl and emerald themes you may run into a few problem when upgrading to compiz fusion.
The first thing is that you will need to COMPLETELY remove beryl, including all the plugins:

beryl-plugins
beryl-settings
libberyldecoration0

If you do not remover all the beryl plugin, when come times to install emerald themes you will only be able to download emerald-themes version 0.2. However this version does not work properly with compiz fusion, you want emerald version 0.3. 

Furthermore remove all beryl repositories from
/etc/apt/source.listquamarine [0.2.0~0beryl1 (feisty, noquamarine [0.2.0~0beryl1 (feisty, now) -> 0.2.1.dfsg+git20070318-0ubuntu2
(feisty)]w) -> 0.2.1.dfsg+git20070318-0ubuntu2
(feisty)]

Next step is to reload the synaptic package manager to save all the changes.
Now you can install compiz fusion and use it with emerald without a problem. When installing emerald and emerald-themes make sure the version is:

emerald [-> 0.3.0+git20070621~3v1ubuntu0 (feisty)

I hope this will help someone

---

