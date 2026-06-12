---
title: "Updating wine from 0.9,33"
date: 2007-05-04
forum: Gaming &amp; Leisure
---

### Post by stevejbayer on 2007-05-04
Hi there 

I installed a clean kubuntu 7.10 a few days back and installed wine just last night.
on running winecfg i get the version number 0.9.33

I added new repos and then attempted to install wine and all i got was version number 0.9.35 from $ winecfg

Here are the steps i took

added repos and relevant GPG keys (beerorkid.com edgy, wine.sourceforge.net, wine.budgetdedicated.com feisty) well i think i need to remove beerorkid.com since thats just for edgy
sudo aptitude update
sudo aptitude install wine

I also downloaded libwine-dev_0.9.36~winehq0~ubuntu~7.04-2_all.deb and opened it with kubuntu package manager (asked for a lib which i installed and re-tried) and when i went to winecfg, I could see wine was at 0.9.33

How can I get wine 0.9.33 upto 0.9.36 I really miss the sound and mouse cursor in GW.

---

### Post by Praill on 2007-05-04
I never recommend installing wine from the repos. I know alot of people do, but wine needs alot of dependencies and will install WITHOUT important ones (opengl :S).

My recommendation: complete removal of the deb package and install the latest wine from source resolving all dependencies and **warnings**.

---

### Post by stevejbayer on 2007-05-04
Well am trying

sudo aptitude upgrade

It looks like its getting 0.9.36 from budgetdedicated.com

---

