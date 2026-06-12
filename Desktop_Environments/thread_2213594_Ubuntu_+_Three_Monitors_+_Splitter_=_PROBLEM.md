---
title: "Ubuntu + Three Monitors + Splitter = PROBLEM"
date: 2014-03-27
forum: Desktop Environments
---

### Post by centras on 2014-03-27
Hi there i am stuck with an issue maybe anyone know how to set this up. 

I bought this splitter [http://datagate.ee/adapters-eng/audiovideo/4world-adapter-dvid-m-241-2-x-dvid-f-241-black/](http://datagate.ee/adapters-eng/audiovideo/4world-adapter-dvid-m-241-2-x-dvid-f-241-black/)

I have AMD HD 6990 card, I want to connect three monitors in to a single card that only has two ports hence the purchase of splitter. this is the issue that i have [http://i62.tinypic.com/5cn506.jpg](http://i62.tinypic.com/5cn506.jpg)
The screens connected to splitter are at 640 x 320 resolution and will not change. i Assume i need to configure xorg.conf but unable to sort this out. 

ANy advicer will be appreciated.

Regards

---

### Post by Thee on 2014-03-27
If you have the proprietary drivers installed, you should be able to easily configure the 2nd monitor output from the Catalyst Control Center.

---

### Post by centras on 2014-03-28
[COLOR=#000000]Catalyst Control Center will not allow any resolution changes it is just stuck at the resolution mentioned above. there is three screens and it only shows two [/COLOR]

---

### Post by Thee on 2014-03-29
The reason why it shows only 2 screens is because you are only using 2 outputs on your graphic card. The splitter doesn't act as a 3rd output, it only splits 1 signal into 2 and shows the same image on 2 displays.
The graphics card can not detect the 3rd display like that. So you won't be able to achieve a true 3 monitor setup with a splitter, if that was your goal. For that you need to use 3 outputs on your graphic card.

Did you open the Catalyst Control Center in Administrative mode?

---

