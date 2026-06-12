---
title: "Installing R - Can't find sample datasets"
date: 2010-03-09
forum: Education &amp; Science
---

### Post by theaks on 2010-03-09
I am using R and RCmdr for a University course. Naturally they have instructions for getting set up in Windows and nothing else.

This isn't a big deal as I managed to find both in synaptic and I've run sudo apt-get install r-base r-base-dev r-cran-rcmdr

However now I'm following the lessons and I'm required to use two datasets that should be supplied with R. They're called faithful and InsectSprays. Following the instructions I'm provided I can't get the datasets loaded into R (through Rcmdr). I've searched my system and some files do exist

/usr/lib/R/library/datasets/R-ex/faithful.R
/usr/lib/R/library/datasets/R-ex/InsectSprays.R

However these files do not like they contain datasets at all.

I'm wondering if there is some other package I need to install to get these datasets? I've tried searching through the package archive for file names, but with no luck so far. Hopefully someone can point me in the right direction

---

### Post by bryncoles on 2010-03-09
What guide are you following? I've just tried loading the data in my own installation (by typing data(InsectSprays)) and this works in both R and Rcmdr. 

Have you tried this? - in Rcmdr you can just type it in the script window then click submit. 

Also, please post any error messages you get, they'll help us help you!

---

### Post by theaks on 2010-03-09
I've just managed it myself, but using data(InsectSprays, package="datasets")

The guide was supplied by my University. The instructions were for Rcmdr.

"On the Data menu, click Data in packages, then Read data set from an attached package...", select InsectSprays from the dialog.

When the dialog appears for me, the only option in the Package menu is "car" if i click this, then the dataset menu populates with all the datasets from the car package. It seems to me like this is an issue with Rcmdr interface rather than R.

---

### Post by bryncoles on 2010-03-09
Ha! I'm, always doing that too - most of my help threads are solved my me a few hours after I post them!

Well done sorting the problem

---

